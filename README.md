# Simon Oyunu - Docker & Nginx

ESP32-C3 Simon oyununun web versiyonu, Docker ile containerize edilmiş ve Nginx ile serve edilmektedir.

## 🚀 Hızlı Başlangıç

### Docker Compose ile Çalıştırma (Önerilen)

```bash
# Projeyi klonlayın veya dosyaları indirin
cd gamegam

# Container'ı build edin ve çalıştırın
docker-compose up --build

# Arka planda çalıştırmak için
docker-compose up -d --build
```

Oyun şu adreste erişilebilir olacak: **http://localhost:8080**

### Manuel Docker ile Çalıştırma

```bash
# Docker image'ını build edin
docker build -t simon-game .

# Container'ı çalıştırın
docker run -d -p 8080:80 --name simon-game-container simon-game
```

## 🎮 Oyun Nasıl Oynanır?

1. **"Oyunu Başlat"** butonuna tıklayın
2. Bilgisayarın gösterdiği renk sekansını izleyin
3. Aynı sırayla butonlara tıklayarak sekansı tekrarlayın
4. Her doğru cevaptan sonra sekans uzar
5. Yanlış tıklarsan oyun biter!

## 📁 Proje Yapısı

```
gamegam/
├── simon-game.html     # Ana oyun dosyası
├── Dockerfile          # Docker container tanımı
├── docker-compose.yml  # Docker Compose konfigürasyonu
├── nginx.conf          # Nginx konfigürasyonu
└── README.md          # Bu dosya
```

## 🔧 Konfigürasyon

### Port Değiştirme

`docker-compose.yml` dosyasında port'u değiştirebilirsiniz:

```yaml
ports:
  - "3000:80"  # localhost:3000 için
```

### Nginx Konfigürasyonu

`nginx.conf` dosyası şu özellikleri içerir:
- ✅ Gzip sıkıştırma
- ✅ Security headers
- ✅ Static asset caching
- ✅ Health check endpoint (`/health`)
- ✅ Performance optimizasyonları

## 🛠️ Geliştirme

### Oyunu Güncelleme

Oyun dosyasını güncelledikten sonra:

```bash
# Container'ı yeniden build edin
docker-compose up --build

# Veya sadece restart edin (volume mount sayesinde)
docker-compose restart
```

### Logları İzleme

```bash
# Container loglarını görüntüleyin
docker-compose logs -f simon-game

# Nginx access logları
docker exec simon-game-container tail -f /var/log/nginx/access.log
```

## 🔍 Sağlık Kontrolü

Container'ın sağlıklı çalışıp çalışmadığını kontrol etmek için:

```bash
# Health check endpoint
curl http://localhost:8080/health

# Container durumunu kontrol etme
docker-compose ps
```

## 🛑 Durdurma ve Temizleme

```bash
# Container'ları durdur
docker-compose down

# Container'ları ve volume'ları temizle
docker-compose down -v

# Image'ları da temizlemek için
docker-compose down --rmi all
```

## 🌟 Özellikler

- **Responsive Design**: Mobil ve masaüstü uyumlu
- **Modern UI**: Tailwind CSS ile şık arayüz
- **Ses Efektleri**: Web Audio API ile gerçekçi sesler
- **Performance**: Nginx ile optimize edilmiş servis
- **Security**: Güvenlik başlıkları ve best practices
- **Monitoring**: Health check ve logging

## 🔊 Tarayıcı Uyumluluğu

- ✅ Chrome/Chromium
- ✅ Firefox
- ✅ Safari
- ✅ Edge

**Not**: Ses efektleri için modern tarayıcı gereklidir (Web Audio API desteği).

## 📝 ESP32 Orijinal Kod

Bu web versiyonu, ESP32-C3 için yazılmış orijinal Simon oyunu kodunun tam bir portudur:
- Aynı oyun mantığı
- Aynı ses frekansları
- Aynı seviye sistemi
- Aynı skorlama

Enjoy the game! 🎉 