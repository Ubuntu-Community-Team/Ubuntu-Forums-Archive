---
title: "ubuntu 12.04 no llegeix arxius odt"
date: 2012-04-29
forum: Catalan Team
---

### Post by josep-maria on 2012-04-29
Ha posat l'ubuntu 12.04, i ara ja no puc obrir cap arxiu odt. Sí que obre els pdf i els jpg. Diu que hi ha un error de lectura, però no sé si el writer no funciona o és que ha fet malbé tots els arxius quan ha canviat la versió de l'ubuntu.

---

### Post by wgarcia on 2012-05-01
El primer a verificar, suposo que ja ho hauràs fet, és verificar si tens instal·lat el "libreoffice", o reinstal·lar-lo per si un cas s'hagués fet malbé la instal·lació d'aquest paquet. 

Obre una terminal (ALT-F2 "terminal") i un cop oberta la terminal entra: 

```
sudo apt-get install --reinstall libreoffice
```

a veure si això ho arregla. 

Si continua sense obrir-se es poden investigar altres coses, però el que es pot descartar és que els "odt" estiguin danyats, les actualitzacions de versió no toquen els fitxers existents, sols actualitzen les aplicacions i paquets, però no les dades de l'ordinador.

---

### Post by josep-maria on 2012-05-03
He fet això de reinstall i em diu: E: No s'ha trobat el paquet reinstall.

---

### Post by Joan A. on 2012-05-03
Has provat de fer un 'reinstall' complet?

```
sudo apt-get reinstall libreoffice
```

Esperam notícies!

---

### Post by josep-maria on 2012-05-03
Si faig: sudo apt-get reinstall libreoffice, em diu:
E: operació no vàlida reinstall.

---

### Post by wgarcia on 2012-05-03
Has de posar-lo exactament com s'indica en la meva intervenció prèvia, amb dos guionets davant de "reinstall", és a dir:

```
sudo apt-get install --reinstall libreoffice
```

---

### Post by Joan A. on 2012-05-04
Uish, perdona! És vera, has de posar els dos guionets. Error meu! De totes formes a mi ahir em varen arribar unes actualitzacions del Libreoffice, tal vegada t'hagin solucionat el problema.

---

### Post by josep-maria on 2012-05-05
Ja va bé!

Avui seguia igual de malament, suposo que l'actualització d'ahir no ho ha arreglat.

Havia fet: sudo apt-get install --reinstall libreoffice i m'havia donat error. 

Ara he fet: sudo apt-get install --reinstall libreoffice i sí que ha funcionat.

Moltes gràcies.

---

