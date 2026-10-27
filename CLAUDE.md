# Özcan Yapı sitesi

ozcanyapikarasu.com — GitHub Pages, `main` dalından otomatik yayınlanır (build yok, düz HTML).
Kullanıcı Türkçe ve samimi konuşur; cevaplar kısa ve Türkçe olsun.

## Yapı

- Kök (`index.html`, `hakkimizda.html`, `iletisim.html` …): firma sitesi, projelere link verir.
- Her proje kendi klasöründe: `yakamoz4/`, ileride `yakamoz5/` vb.
  Her proje klasöründe aynı sayfalar var: `index`, `daireler`, `detay`, `konum`, `galeri`, `santiye`, `iletisim`.
- `detay.html`: projenin 3D modeli (Three.js). Müşteriye gönderilen link budur.
- `durum.json`: o projenin daire satış durumları. `detay.html` bunu açılışta okur.
- `rota-animasyonu-ozcan-yapi.html` (kökte): Yakamoz 4 → sahil rota animasyonu (MapLibre + Esri, token gerekmez).

## Aktif proje

Şu an satıştaki proje: **Yakamoz 4** (`yakamoz4/`).
Yakamoz 5 başlayınca: `yakamoz5/` klasörü açılır, kendi `durum.json`'ı olur, bu bölüm güncellenir.
Biten projelerin klasörleri silinmez, referans olarak kalır.

## "X daire satıldı" gibi istekler

Kullanıcı "A5 satıldı", "B3 opsiyonlu", "A1 fiyatı 3.450.000 TL" derse:

1. Proje belirtilmediyse **aktif projenin** `durum.json`'ını düzenle. Belirsizse sor.
2. Sadece ilgili dairenin `durum` / `fiyat` alanını değiştir:
   - `durum`: `satista` | `opsiyon` | `satildi` (başka değer yazma, sayfa yok sayar)
   - `fiyat`: metin, ör. `"3.450.000 TL"`; boş `""` ise sitede "Bilgi için arayın" görünür.
3. Dosyanın geçerli JSON olduğunu kontrol et (`python3 -m json.tool <dosya>`).
4. Commit at ve **doğrudan `main`'e push et**. Ayrı dal/PR açma, site ancak `main`'den yayınlanır.
5. Kullanıcıya hangi daireyi neye çevirdiğini tek satırda söyle; 1-2 dk içinde sitede olacağını belirt.

`detay.html` içindeki `<script id="state">` sadece yedektir (durum.json okunamazsa kullanılır); onu elle güncellemek gerekmez.
