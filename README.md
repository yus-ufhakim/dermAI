# 🩺 dermAI - Cilt Hastalıkları Sınıflandırma Modeli

**dermAI**, dermatolojik görüntüler üzerinden **Egzama (Eczema)**, **Sedef Hastalığı (Psoriasis)** ve **Sağlıklı (Normal)** deri dokularını yüksek doğrulukla ayırt etmek üzere geliştirilmiş derin öğrenme tabanlı bir görüntü sınıflandırma projesidir.

---

## 📊 Veri Seti (Dataset)
Model eğitiminde toplam **6.113** adet görüntü kullanılmıştır. Sınıflar arasındaki veri dengesizliğini gidermek amacıyla eğitim sürecinde sınıf ağırlıklandırma (`class_weight`) ve veri çoğaltma (Data Augmentation) teknikleri uygulanmıştır.

* **Psoriasis (Sedef Hastalığı):** [Kaggle - Psoriasis Dataset](https://www.kaggle.com/datasets/aditipathak17/psoriasis) (1.586 görsel)
* **Eczema (Egzama) & Normal:** [Kaggle - Eczema Dataset](https://www.kaggle.com/datasets/adityush/eczema2?resource=download) (1.544 Egzama, 2.983 Sağlıklı görsel)

---

## 🧠 Model Mimarisi ve Eğitim Süreci
* **Temel Mimari:** ImageNet ağırlıklarıyla önceden eğitilmiş **EfficientNetB0**
* **Eğitim Stratejisi:**
  1. **Feature Extraction:** Temel katmanlar dondurularak sınıflandırma katmanı eğitildi (%93.04 doğrulama başarısı).
  2. **Fine-Tuning (İnce Ayar):** Modelin son 30 katmanının kilidi açılarak `1e-5` öğrenme oranı ile ince ayar yapıldı (**%95.50** doğrulama başarısı).

---

## 📈 Performans Sonuçları (Validation Set)

| Sınıf | Precision (Kesinlik) | Recall (Duyarlılık) | F1-Score | Görsel Sayısı |
| :--- | :---: | :---: | :---: | :---: |
| **Eczema** | 0.85 | 0.99 | 0.92 | 275 |
| **Normal** | 1.00 | 0.96 | 0.98 | 612 |
| **PSORIASIS** | 0.98 | 0.91 | 0.95 | 335 |
| **Genel Doğruluk (Accuracy)** | | | **0.95** | **1222** |

---

## 🚀 Kurulum ve Kullanım

1. Repoyu klonlayın:
   ```bash
   git clone [https://github.com/yus-ufhakim/dermAI.git](https://github.com/yus-ufhakim/dermAI.git)
   cd dermAI
