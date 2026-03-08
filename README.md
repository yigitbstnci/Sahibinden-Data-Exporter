# Sahibinden Data Exporter 🚗📊

Bu proje, **sahibinden.com** üzerindeki ilan listelerini tek bir tıklama ile **JSON** formatında dışa aktarmanızı sağlayan hafif ve güvenli bir **Bookmarklet** aracıdır. Veri analizi ve yapay zeka  testleri için hızlı veri toplama amacıyla tasarlanmıştır.

## ✨ Özellikler

* **Hızlı Kurulum:** Herhangi bir eklenti veya kütüphane gerektirmez, sadece bir yer imi (bookmark) olarak çalışır.
* **Modern Arayüz:** Sayfanın sağ üst köşesine sabitlenen, kullanıcı dostu bir kontrol butonu enjekte eder.
* **Kapsamlı Veri Çekme:** İlan tablosundaki; **Model, Başlık, Yıl, KM, Renk, Fiyat, Tarih ve Konum** bilgilerini otomatik olarak yakalar.
* **Gizlilik Odaklı:** Verileriniz hiçbir harici sunucuya gönderilmez; tüm işlemler tarayıcı tarafında (client-side) gerçekleşir.

## 🚀 Kurulum ve Kullanım

### 1. Adım: Yer İmi Oluşturma
Tarayıcınızın yer imleri çubuğuna sağ tıklayarak yeni bir yer imi ekleyin.
* **İsim:** `Sahibinden Export`
* **URL/Adres:** Aşağıdaki JavaScript kodunun tamamını buraya yapıştırın.

### 2. Adım: Kod (Bookmarklet)
```javascript
javascript:(function(){if(document.getElementById('s-export-btn'))return;var b=document.createElement('button');b.id='s-export-btn';b.innerHTML='📊 Export JSON';Object.assign(b.style,{position:'fixed',top:'20px',right:'20px',zIndex:'2147483647',padding:'12px',backgroundColor:'#4f46e5',color:'#fff',border:'none',borderRadius:'8px',cursor:'pointer',fontWeight:'bold',boxShadow:'0 4px 12px rgba(0,0,0,0.5)'});b.onclick=function(){var d=[];var r=document.querySelectorAll('tr.searchResultsItem');r.forEach(function(s){if(s.cells.length>5){d.push({model:s.cells[1]?.innerText.trim(),baslik:s.cells[2]?.innerText.trim(),yil:s.cells[3]?.innerText.trim(),km:s.cells[4]?.innerText.trim(),fiyat:s.cells[6]?.innerText.trim()});}});if(d.length>0){var blob=new Blob([JSON.stringify(d,null,2)],{type:'application/json'});var u=URL.createObjectURL(blob);var a=document.createElement('a');a.href=u;a.download='sahibinden_data.json';a.click();b.innerHTML='✅ Done!';setTimeout(function(){b.innerHTML='📊 Export JSON'},2000);}else{alert('No data!')}};document.body.appendChild(b);alert('Buton eklendi!');})();

```
**Not:** Eğer yer imine tıkladığınızda buton görünmüyorsa, tarayıcınızın JavaScript çalıştırma izinlerini (özellikle Safari'de) kontrol edin veya sayfayı yenileyip tekrar deneyin.
