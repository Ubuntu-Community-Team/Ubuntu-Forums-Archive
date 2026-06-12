---
title: "Connectar a monitor extern o tv"
date: 2011-08-04
forum: Catalan Team
---

### Post by simfomet on 2011-08-04
Hola a tots,

tinc un netbook amb xubuntu instal·lat i m'agradaria poder connectar-lo a una tv a través d'una sortida VGA que té i quan ho faig em detecta que té connectat un monitor quan ho miro al gestor d'actualitzacions--pantalla mostrant les opcions de resolució i demés però a la tv no surt res, només un soroll irritant però pantalla negra.

Se us acut que puc fer? Com puc mirar quins controladors o gràfica tinc ja que no sé com fer-ho a xubuntu?

---

### Post by simfomet on 2011-08-05
Llegint una mica per la xarxa he trobat que no es pot fer a menys que facis una inversió en una mena de conversor de senyal ja que el sincronisme i altres històries de la senyal elèctrica no "s'entenen" per dir-ho així entre la sortida vga d'un portàtil i les entrades RCA analògiques d'una tv de tub.

---

### Post by snoopo71 on 2011-08-19
> **simfomet said:**
> Llegint una mica per la xarxa he trobat que no es pot fer a menys que facis una inversió en una mena de conversor de senyal ja que el sincronisme i altres històries de la senyal elèctrica no "s'entenen" per dir-ho així entre la sortida vga d'un portàtil i les entrades RCA analògiques d'una tv de tub.

Aviam, aclareix-ho un mica, com connectes el portàtil a la TV(quin cable)? Quina Gràfica tens? Tens els drivers a dia?

---

### Post by simfomet on 2011-08-22
> **snoopo71 said:**
> Aviam, aclareix-ho un mica, com connectes el portàtil a la TV(quin cable)? Quina Gràfica tens? Tens els drivers a dia?

Doncs l'única opció que tinc per connectar-ho és a través d'un cable [com aquest]("http://www.aficam.es/images/CABLE%20VGA%20A%20RGB.3%20x%20RCA.%20AV%20VIDEO%20COMPONENTES.%20HD%20TV.jpg") comprat en una tenda de "xinos", la veritat no tinc idea de com mirar la gràfica que tinc amb xubuntu però ho miraré i sobre els drivers sempre intento tenir-ho al dia actualitzant el sistema.

---

### Post by vila-seca on 2011-08-24
> **simfomet said:**
> , la veritat no tinc idea de com mirar la gràfica que tinc amb xubuntu però ho miraré i sobre els drivers sempre intento tenir-ho al dia actualitzant el sistema.

Per a mirar la gràfica obres una consola i poses:

```
lspci | grep VGA
```

---

### Post by quitus on 2011-08-24
El cable aquest que mostres es un cable de components i pel que he llegit la frecuencia del senyal ha de ser el que la tv pugui interpretar, es ha dir de 50Hz ja que suposo que si fos de 100Hz ja tindria una entrada de PC.

salut

---

### Post by snoopo71 on 2011-08-25
> **quitus said:**
> El cable aquest que mostres es un cable de components i pel que he llegit la frecuencia del senyal ha de ser el que la tv pugui interpretar, es ha dir de 50Hz ja que suposo que si fos de 100Hz ja tindria una entrada de PC.

salut

Totalment cert, canvia la freqüència a 50Hz i ja estar, per molt que haig de dir que no havia vist mai un cable d'aquests! A mes només hauria de tenir un cable rca, ja que la sortida vga només envia imatge i no sò, em sembla que potser el cable no és l'adequat. Mira si tens una sortida S-video, crec que anira millor!

---

### Post by simfomet on 2011-08-26
Per parts, en primer terme la gràfica que té el netbook és una integrada i la info que surt amb l'ordre és:

Compaq-Mini-CQ10-500:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller

Si el cable que he comprat és de component segurament l'he pifiat perquè la meva tv només té entrades d'euroconector, RCA i S-Video. El netbook només té VGA de sortida. He provat de tornar a connectar i en qualsevol de les resolucions que em deixa provar la gràfica no em permet baixar de 60Hz, només en una ho fa i no obtinc imatge.

---

### Post by snoopo71 on 2011-08-26
> **simfomet said:**
> Per parts, en primer terme la gràfica que té el netbook és una integrada i la info que surt amb l'ordre és:

Compaq-Mini-CQ10-500:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller

Si el cable que he comprat és de component segurament l'he pifiat perquè la meva tv només té entrades d'euroconector, RCA i S-Video. El netbook només té VGA de sortida. He provat de tornar a connectar i en qualsevol de les resolucions que em deixa provar la gràfica no em permet baixar de 60Hz, només en una ho fa i no obtinc imatge.

Ja m'estranyava tants fils, es veritat, no es RCA, es de components. Dons així deixau o canvies la tv o ho proves amb un monitor amb vga o dvi, o potser pots trobar un adaptador (no un cable ja que les senyals no son "compatibles") vga a rca, però et valdrà bastant.

Maco sort!!

---

### Post by snoopo71 on 2011-08-31
Passa't per [aquí]("http://www.dealextreme.com/p/15-pin-vga-to-s-video-av-rca-tv-cable-19cm-length-81243") aviam si et serveix!!

---

### Post by simfomet on 2011-09-26
Gràcies snoopo71, crec que em pot servir i pel que costa val la pena provar.

---

### Post by simfomet on 2011-10-31
> **snoopo71 said:**
> Passa't per [aquí]("http://www.dealextreme.com/p/15-pin-vga-to-s-video-av-rca-tv-cable-19cm-length-81243") aviam si et serveix!!

Vaig demanar l'andròmina aquesta que és barata i mira... però no ha servit de res. Ni amb Xubuntu, ni Kubuntu ni fins i tot Windows 7 que el tinc més dominat no he aconseguit veure res en la meva vella tv de tub. En fi...

---

