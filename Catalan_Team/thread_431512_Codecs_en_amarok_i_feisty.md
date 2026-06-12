---
title: "Codecs en amarok i feisty"
date: 2007-05-03
forum: Catalan Team
---

### Post by PellRoja on 2007-05-03
bones, m' havien explicat que hi havia una nova forma de poder instal·lar els codecs propietaris en la nova versió.

El fet és que acabo de instal·lar, i he instal·lat l' amarok, pero al escanejar les cançons em diu que no les puc escoltar per falta de codecs.

Algu sap com es fa la nova instal·lació de codecs?

:guitar:  :P

---

### Post by patrickfromspain on 2007-05-03
sudo apt-get install libxine1-ffmpeg libxine-extracodecs

salut!

---

### Post by PellRoja on 2007-05-03
he provat això pero segueix sense funcionar. l' error que em surt a l' amarok es aquest


S'ha produït un error en carregar el mitjà
No hi ha cap connector demux adequat. Això sovint significa que el format del fitxer no està suportat.
file:///media/hdb1/musica/Varis Hala Bediren Konzertua Gazteiz/hala bediren konzertua gazteiz/b - 01 - la polla records - la justicia.mp3


he canviat els permisos del disc dur a 777 per si era problema de això, però res. he provat amb un .ogg i tampoc mel reprodueix

---

### Post by patrickfromspain on 2007-05-03
proba instalant libxine1

Suposo que despres de reinstalar has reiniciat l'amarok?

---

### Post by PellRoja on 2007-05-03
he trobat com instal·lar-los per el reproductors de ubuntu. Pero amb amarok no va.

el nou sistema per instal·lar codecs per entorn grafic. Sols tenim que clickar sobre qualsevol mp3, i si el mateix reproductor no el troba, ens llistara els codecs per poder-los instal·lar. Així de senzill, pero amarok segueix sense funcionar

editat: tenia un problema molt raro, l' he solucionat borrant la carpeta .xine, i ella sola es restaurava al iniciar amarok, ara si amb mp3.

---

### Post by papapep on 2007-05-03
(amb Universe descomentat al /etc/apt/sources.list):

sudo aptitude install gstreamer0.8-mad

---

### Post by patrickfromspain on 2007-05-03
amarok no fa servir gstreamer, el seu motor es xine.

---

### Post by orestesmas on 2007-05-04
Una opció és afegir els repositoris de MEDIBUNTU, que contenen versions dels reproductors (amarok, kaffeine...) amb el suport per escoltar mp3, veure dvd, etc., compilat a dins. En aquest país (encara) no és il·legal tenir-los.

[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

---

### Post by ernestux on 2007-05-05
Hola a tots,

Jo tinc ubuntu, i escriptori gnome , però tinc també instal·lat el kde-core bàsic. Acabo d'instal·lar AMAROK i no em corria elsmp3 ; ni seguint els passos que heu comentat abans.  Mirant altres forums he vist que instal·lant libxine-extracodecs  ho solucionava;  dit i fet i  ja puc sentir els mp3 .  Ah ! i borrant la carpeta .xine de la home 


Com més serem més avançarem !:)

---

