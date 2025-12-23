# Customer Cohort Analysis

Analisis kohort pelanggan untuk mengidentifikasi pola retensi, tingkat churn, dan karakteristik loyalitas pelanggan berdasarkan waktu pendaftaran dan perilaku transaksi awal.

## 📊 Deskripsi Proyek

Proyek ini melakukan analisis mendalam terhadap data pelanggan menggunakan teknik cohort analysis untuk memahami:
- **Retention Rate**: Persentase pelanggan yang tetap aktif dari bulan ke bulan
- **Churn Pattern**: Kapan pelanggan cenderung berhenti bertransaksi
- **Customer Loyalty**: Perbedaan perilaku antara pelanggan antusias vs pelanggan coba-coba

### Dataset yang Digunakan

1. **invoice.csv** - Data transaksi (ribuan record)
   - `Invoice`: Nomor invoice
   - `Customer ID`: ID pelanggan
   - `InvoiceDate`: Tanggal transaksi

2. **users.csv** - Data pendaftaran user
   - `user_id`: ID user
   - `signup_date`: Tanggal pendaftaran

## 🔍 Metodologi Analisis

### 1. Time-Based Cohort Analysis
Mengelompokkan pelanggan berdasarkan **bulan pendaftaran** dan melacak retensi mereka dari bulan ke bulan.

**Metrik Utama:**
- `signup_month`: Bulan pendaftaran (cohort group)
- `cohort_index`: Bulan ke-n setelah pendaftaran (0, 1, 2, ...)
- `retention_rate`: Persentase pelanggan yang masih aktif

<img width="749" height="523" alt="image" src="https://github.com/user-attachments/assets/901b96e2-f7cf-4a2a-8b7f-fef4d023fc74" />


### 2. Loyalty-Based Cohort Analysis
Mengkategorikan pelanggan berdasarkan **frekuensi transaksi di bulan pertama**:
- **Antusias**: Belanja >10 kali di bulan pertama
- **Coba-coba**: Belanja 10 kali saja di bulan pertama

<img width="955" height="493" alt="image" src="https://github.com/user-attachments/assets/9750d5e6-8303-416c-92db-efe9e3b03073" />


## 📈 Key Findings

**Golden Rule:**
> "Efek 'Power User' pada Retensi Pelanggan yang memiliki frekuensi transaksi tinggi (>10 kali) di bulan pertama menunjukkan tingkat loyalitas yang jauh lebih kuat dibandingkan pelanggan yang hanya bertransaksi satu kali."

### Temuan 1: Massive First-Month Drop
- **Penurunan drastis** terjadi di bulan pertama setelah pendaftaran
- Retensi turun dari **100%** menjadi **12%-45%**
- Rata-rata kehilangan **55%-88%** pelanggan dalam 30 hari pertama

**Implikasi Bisnis:**
- Butuh strategi onboarding yang kuat
- Promo khusus atau reminder di minggu ke-2 dan ke-4
- Email nurturing campaign untuk bulan pertama

### Temuan 2: Declining Quality of New Customers
Kualitas pelanggan baru menurun seiring waktu:
- **Februari 2010**: Retensi bulan-1 = 45%
- **November 2010**: Retensi bulan-1 = 12%

**Kemungkinan Penyebab:**
- Kampanye akhir tahun menarik bargain hunters
- Quality vs quantity dalam akuisisi pelanggan
- Seasonal effect (holiday shoppers)

### Temuan 3: The 5-Month Loyalty Threshold
Pelanggan yang bertahan hingga **bulan ke-5** cenderung menjadi pelanggan loyal:
- Retensi stabil atau bahkan naik setelah bulan ke-5
- Contoh: Cohort Feb-2010 stabil di 40% dari bulan 7-9

**Strategic Focus:**
- Prioritas tinggi: Pertahankan pelanggan sampai bulan ke-5
- Loyalty program mulai aktif di bulan ke-3
- Check-in rutin untuk pelanggan bulan ke-4

### Temuan 4: 2x Retention from Repeat Purchases
Pelanggan yang belanja >1 kali di bulan pertama memiliki:
- **Retensi 2x lebih tinggi** (40.6% vs 23.7% di bulan-1)
- **Lifetime value lebih besar** (bertahan hingga bulan ke-10)
- **Lower churn risk** sepanjang customer journey

**Golden Rule:**
> "First repeat purchase dalam 30 hari = predictor terkuat loyalitas jangka panjang"

### Temuan 5: February 2010 Anomaly
Cohort Februari 2010 adalah yang **paling healthy**:
- Retensi konsisten >30% hingga bulan ke-10
- Warna paling gelap di heatmap (retensi tertinggi)

**Action Items:**
- Review: Apa yang dilakukan berbeda di Feb 2010?
- Apakah ada product launch, promo khusus, atau service improvement?
- Replicate strategy tersebut untuk bulan-bulan lain

## 💡 Rekomendasi Strategis

### Immediate Actions (0-30 Days)
1. **Welcome Series yang Kuat**
   - Email sequence 5-7 hari pertama
   - Tutorial penggunaan produk/layanan
   - Personal onboarding call untuk high-value customers

2. **Incentive untuk Transaksi Kedua**
   - Voucher khusus untuk pembelian kedua dalam 30 hari
   - "Complete your first month" challenge dengan reward
   - Free shipping untuk transaksi kedua

### Medium-Term Actions (1-5 Months)
3. **Milestone Engagement**
   - Check-in otomatis di hari ke-30, 60, 90
   - Personalized recommendation berdasarkan transaksi pertama
   - Exclusive access untuk pelanggan yang mencapai bulan ke-3

4. **Early Warning System**
   - Identifikasi pelanggan yang tidak transaksi 45 hari
   - Win-back campaign sebelum mereka completely churn
   - Survey: "Why haven't you shopped with us lately?"

### Long-Term Strategy
5. **Improve Acquisition Quality**
   - Review kampanye marketing Q4 (Oktober-November)
   - Fokus pada sustainable growth vs viral but low-quality growth
   - A/B testing: discount heavy vs value-driven messaging

6. **Loyalty Program Redesign**
   - Tier system yang reward repeat purchases di bulan pertama
   - Exclusive perks unlock di bulan ke-5 (loyalty threshold)
   - Referral bonus untuk pelanggan cohort yang sehat

## 🛠️ Setup & Installation

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn
```

### Running the Analysis
```python
# Mount Google Drive (untuk Google Colab)
from google.colab import drive
drive.mount('/content/drive')

# Jalankan script utama
python cohort_analysis.py
```

## 📊 Output Visualizations

1. **Cohort Retention Heatmap**
   - Menampilkan retention rate per cohort dari bulan ke bulan
   - Warna biru gelap = retensi tinggi, kuning = retensi rendah

2. **Loyalty Comparison Heatmap**
   - Membandingkan retensi pelanggan Antusias vs Coba-coba
   - Membuktikan pentingnya repeat purchase di bulan pertama

## 📝 Notes

- Data coverage: Februari - Desember 2010
- Sample size: ~4,000 transaksi dari 200+ unique customers
- Analysis framework: Time-based + Behavior-based cohort

## 🚀 Next Steps

1. **Predictive Modeling**: Build ML model untuk prediksi churn di hari ke-30
2. **RFM Analysis**: Kombinasikan dengan Recency-Frequency-Monetary segmentation
3. **Lifetime Value Calculation**: Hitung CLV untuk setiap cohort
4. **A/B Testing Framework**: Test strategi retensi secara sistematis

---

**Author**: Data Analytics Team  
**Last Updated**: December 2024  
**Tools Used**: Python, Pandas, Seaborn, Matplotlib
