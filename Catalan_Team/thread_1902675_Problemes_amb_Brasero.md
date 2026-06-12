---
title: "Problemes amb Brasero"
date: 2011-12-31
forum: Catalan Team
---

### Post by skywalk on 2011-12-31
Bon dia i bon final d'any i millor 2012:
Vulguen gravar una recopil-alció de cançons de durada total de uns 81 minuts a uns CD-R de 90 minuts (800MB) m'ha sigut impossible amb el Brasero a Ubuntu 10.10. Al afegir cançons al passar de 60 minuts aproximadament, a la següent que afegia am deia ja mes de 100 minuts i al intentar gravar es penjava el ordinador. Passava el mateix amb el Xfburn a una altre partició amb Arch. A un altre ordinador amb Fedora 15 i amb el Brasero em deia el mateix, però ja no vaig provar de gravar. Vaig tenir de gravar-los al  Windows Xp d'aquest ultim ordinador. Sabeu perquè em passa això? Que faig malament?

---

### Post by wgarcia on 2012-01-03
Tens suficient espai al directori "/tmp"? Per veure com estàs d'espai pots fer:

```
df
```

des d'una terminal i enganxar aquí els resultats.

---

### Post by skywalk on 2012-01-05
wgarcia:

No tinc problemes de espai al disc. Les cançons que vull gravar estan amb mp3. Cercant informació per la xarxa  l'únic que he trobat es que el gstreamer0.10-fluendo.mp3 pot interferir amb el ffmpeg i que tinguen aquest últim era llogic eliminar el fluendo.mp3. Així ho he fet però no ha fonccionat. Continua igual. Al anar afegint cançons, quan  superes el 60 minuts  abaix  a on et diu la mida estimada del projecte, passa de  p.e. 58 minuts a 1 hora i 4 minuts i llavors si continua's, al gravar es penja. Al anar cercant informació veig que hi ha molta historia arran de cdrecord  etc. amb Brasero.
De moment no men surto.

---

### Post by wgarcia on 2012-01-06
Per aclarir, estàs convertint fitxers de mp3 a wav i gravant-los a un CD blanc, oi?

---

### Post by skywalk on 2012-01-06
No, no. Tinc totes les cançons amb mp3 i vull gravar-las a un CD en blanc.

---

### Post by wgarcia on 2012-01-07
Però les vols gravar en format "àudio", oi?: aquest és el format wav, el que poden reproduir aparells d'àudio.

---

