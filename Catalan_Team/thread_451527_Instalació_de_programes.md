---
title: "Instalació de programes"
date: 2007-05-22
forum: Catalan Team
---

### Post by ventma on 2007-05-22
De quina manera puc fer l instal·lació de qualsevol programa extern, que no estigui incorporat a l'instal·lador d'ubuntu, per tal d'integrar-lo dins del sistema. Per exemple, el "Real Player", l'he instal·lat, el programa s'obre bé però el Firefox no el reconeix, no el té com a plugin.

---

### Post by Ferri on 2007-05-22
Pel que dius, probablement t'ha instal·lat els connectors a una carpeta diferent d'on te'ls busca el firefox.
```
locate nphelix.so
locate nphelix.xpt
```
En el meu cas són a /usr/lib/firefox/plugins/
Si és així, fes:
```
ln -s /usr/lib/firefox/plugins/nphelix.xpt /home/ventma/.mozilla/plugins
ln -s /usr/lib/firefox/plugins/nphelix.so /home/ventma/.mozilla/plugins

```
A "ventma" posa el nom de la teva carpeta /home, i a la primera part, corregeix el camí d'accés si s'escau.
Segurament el firefox no et troba els connectors perquè deus fer servir una versió que no és la que et vé amb Ubuntu. El paquet que et descarregues de Mozilla et busca els connectors a /home/elteunom/.mozilla/pluguins, el d'Ubuntu, entre d'altres, busca també a /usr/lib/firefox/plugins/

---

### Post by ventma on 2007-05-24
Els fitxers estan a:
/home/ventura/.mozilla/plugins/nphelix.so
/home/ventura/.mozilla/nphelix.xpt
La versió del RealPlayer no és la que diu el Firefox instal·lat per l'ubuntu, però és la darrera, que puc fer?

---

### Post by orestesmas on 2007-05-25
Jo mouria els fitxers al directori /usr/lib/firefox/plugins. Fes-ho com a root (amb sudo)

Probablement això t'ha passat perquè has instal·lat el RealPlayer com a usuari normal, i no pas amb sudo, o bé li has dit que t'ho instal·li al directori d'usuari.

En acabat, obre el navegador i ves a la URL "about:plugins" per comprovar que tot és ok.

---

### Post by ventma on 2007-05-27
Els fitxers s'han copiat bé a /usr/lib/firefox/plugins però no funciona i a "about:plugins" no apareixen.

---

### Post by orestesmas on 2007-05-27
No estaras utilitzant per casualitat una versió d'ubuntu de 64 bits? Els plugins de programes privatius generalment només existeixen per 32 bits i no funcionen (o cal molta feina perquè ho facin) en arquitectures de 64 bits.

Si no és això, de moment no se m'acut res més, excepte el dir-te que tornis a executar l'instal·lador del RealPlayer però aquesta vegada com a Root. Normalment si ho fas així el plugin s'instal·la a nivell global de sistema (i ell s'encarrega de cercar on l'ha de posar), mentre que si ho instal·les com a usuari només et queda disponible per tu i prou.

---

