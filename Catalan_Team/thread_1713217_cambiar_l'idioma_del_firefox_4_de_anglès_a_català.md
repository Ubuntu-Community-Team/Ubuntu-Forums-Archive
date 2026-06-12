---
title: "cambiar l'idioma del firefox 4 de anglès a català"
date: 2011-03-23
forum: Catalan Team
---

### Post by dariusill on 2011-03-23
Hola Ubuntaires,

M'acabo de descarregar el firefox 4 i ha arribat en anglès...algú sap com posar-lo en català?!?!

( per cert...pinta mooooooooooooooolt bé)


Gràcies

Ill

---

### Post by wgarcia on 2011-03-24
Suposo que l'hauràs instal·lat directament des de la pàgina de Mozilla. Hi ha un dipòsit que permet instal·lar-lo de forma que es vagi actualitzant, tot i que ja ve per defecte a la nova versió d'Ubuntu que apareix a l'abril. Si vols instal·lar-lo del dipòsit, hauries de desinstal·lar el que has instal·lat i seguir les següents instruccions des d'una terminal:

sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get install firefox ubufox

Com veus aquesta instal·lació també inclou algunes coses específiques d'ubuntu ("ubufox").

De totes maneres si ho prefereixes pots mantenir la versió que tens, i els paquets de llengua els pots baixar de:

32 bits: [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/4.0/linux-i686/xpi/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/4.0/linux-i686/xpi/)

64 bits: [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/4.0/linux-x86_64/xpi/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/4.0/linux-x86_64/xpi/)

(Com veus primer has d'assegurar-te si tens Ubuntu de 32 o 64 bits).

Per últim, si vols moure el menú a l'esquerra, com ve per defecte a Firefox 4 però que no ho fa si tenies un perfil de Firefox 3 instal·lat, pots fer servir la següent extensió:

[https://addons.mozilla.org/en-US/firefox/addon/movable-firefox-button/](https://addons.mozilla.org/en-US/firefox/addon/movable-firefox-button/)

---

### Post by oriolsbd on 2011-03-24
El millor és insta&#320;lar el Firefox 4 des de repositoris (el que indica el wgarcia) però, com comentes, si ho fas així tindràs el Firefox en anglès. Mira aquesta anotació, on expliquem com posar el paquet d'idioma en català i com configurar algunes de les noves característiques:
[http://www.gnulinux.cat/2011/03/installa-i-configura-el-nou-firefox-4/](http://www.gnulinux.cat/2011/03/installa-i-configura-el-nou-firefox-4/)

Salut!

---

### Post by dariusill on 2011-03-24
Hola wgarcia i companyia,

He baixat els paquets d'idioma en comptes de desinsita·llar i instal·lar de nou i m'ha funcionat. Gràcies de 9. Per cert, m''he instal·lat una aplicació amb la qual tinc la interficie del meu pc com un MAC, jejej mola!


Salut!

---

