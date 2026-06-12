---
title: "Repositoris Maverick"
date: 2010-10-13
forum: Catalan Team
---

### Post by akyra on 2010-10-13
Hola a tothom,

Tinc un petit problema amb uns repositoris. Algú sap que pot ser?
El missatge que em dóna és el següent:
> W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY D7260B8F5A0FA8F1
W: Imposible obtener [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry  non-free/source/Sources in Meta-index file (malformed Release file?)
W: Imposible obtener [http://download.virtualbox.org/virtualbox/debian/dists/maverick/Release](http://download.virtualbox.org/virtualbox/debian/dists/maverick/Release)  Unable to find expected entry  non-free/source/Sources in Meta-index file (malformed Release file?)

E: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.



Gracies

---

### Post by tanreb20 on 2010-10-13
```
gpg --keyserver keyserver.ubuntu.com --recv NUM

gpg --export --armor NUM | sudo apt-key add -
```

I apa!

---

### Post by akyra on 2010-10-14
Collonut Tanreb,
Ara només em falten aquestes dos:
> W: Imposible obtener [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry  non-free/source/Sources in Meta-index file (malformed Release file?)

W: Imposible obtener [http://download.virtualbox.org/virtualbox/debian/dists/maverick/Release](http://download.virtualbox.org/virtualbox/debian/dists/maverick/Release)  Unable to find expected entry  non-free/source/Sources in Meta-index file (malformed Release file?)

E: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.

---

