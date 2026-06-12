---
title: "Firefox piratejat"
date: 2013-06-22
forum: Catalan Team
---

### Post by akyra on 2013-06-22
Hola tots,

M'he adonat que quan estic navegant amb firefox la navegació és molt lenta, tan amb wifi com en cable, i inclús sa màrribat a desconnectar el wifi (potser això és un altre problema).
Bé, ahir vaig trucar a Ono, dient que la velocitat era penosa, de 45MB contractats en tenia 1,4MB de baixada però 2MB de pujada o sigui que la baixada fatal i la pujada perfecte. Vaig fer les proves amb windows i anava a 45MB o sigui que no era problema de Ono.

Vaig observar que quan em connectava amb el meu usuari a fer el test em dirigia a una pàgina que no era la que hem dirigia quan vaig fer el test amb windows, i després ho he provat amb altres usuaris i funciona bé.

Amb Chromium dóna correcte la velocitat.

La pregunta és que haig de fer per deixar el Firefox com si fos nou, sense perdre els preferits?
La versió de Firefox és la 21.

Moltes gracies.

---

### Post by papapep on 2013-09-03
Hola, Akyra.

Abans de res, exporta els preferits i així els podràs reimportar quan acabis tot el procés.

Per a eliminar completament el Firefox, assumint que l'has instal·lat des dels paquets del repositori, fes:

```
sudo apt-get purge firefox
```

Fet això, esborra els directoris de configuració que tens dins el teu directori personal. Ves amb compte amb aquesta ordre, si t'equivoques de directori esborrarà tot el que hi hagi sota:

1. Assegura't de ser al teu directori personal. El caràcter ~ el fas amb AltGr i 4:
```

cd ~
```

2. Ara verifiques que hi ets. Amb aquesta ordre hauries de veure "/home/akyra", suposant que el teu nom d'usuari sigui "akyra":
```
pwd 
```

3. I ara elimines el directori ".mozilla", i tot el que hi hagi per sota, que hauries de tenir dins el teu directori personal:
```
rm -rf .mozilla
```
(atenció que hi ha un punt "." davant "mozilla", que és com s'anomenen els directoris ocults en Gnu/Linux!)

Tingues present que és possible que el que t'hagi "piratejat", si realment ha passat això, el Firefox sigui algun complement que hagis instal·lat, no el navegador en si. T'ho comento per a que ho tinguis en consideració a l'hora d'instal·lar-ne. Sempre és (MOLT) recomanable instal·lar el Noscript [https://addons.mozilla.org/ca/firefox/addon/noscript/](https://addons.mozilla.org/ca/firefox/addon/noscript/) que limita el mal que et puguin fer alguns atacs amb Javascript, els més comuns als navegadors web.

Espero que això et serveixi.

Salut.

---

### Post by akyra on 2013-09-05
Ho probaré, gracies.

---

