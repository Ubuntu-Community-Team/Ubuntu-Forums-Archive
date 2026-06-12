---
title: "sistema-administració-xarxa"
date: 2009-03-19
forum: Catalan Team
---

### Post by Molsa on 2009-03-19
M'he instal.lat el Xubuntu, però no puc accedir a la xarxa, em diu que entri la contrasenya,... la poso,... busca,... i salta.
L'inalàmbric funciona perquè m'ofereix vàries xarxes.

Sembla que he d'anar a sistema-administració-xarxa i allà podré mirar d'arreglar-ho. Però no ho trobo. A sistema no hi ha ni administració, i d'usuari només hi sóc jo.

---

### Post by papapep on 2009-03-20
Hola Molsa,

Caldria tenir més informació de tot plegat. No ens expliques ni quina placa de xarxa inalàmbrica tens, ni si la xarxa està xifrada i, si ho està, amb quin xifrat (WEP, WPA, WPA2..).

Per saber la placa que tens, fes a un terminal:

```
lspci
```

Per veure quin dispositiu és l'inalàmbric, fes:

```
sudo ifconfig
```

i veuràs tots els dispositius de xarxa configurats. Probablement, l'inalàmbric sigui wlan0 o eth1.

Si fas:

```
sudo iwlist "el_dispositiu_inalàmbric" scan
``` veuràs totes les xarxes inalàmbriques que detecta i la seva configuració.

A partir d'aquí, i veient tot això, es podrà analitzar si el que passa és a nivell de xifrat, o per culpa de la placa de xarxa o pel que sigui.

Et recomano una bona llegida al [fil pels nouvinguts]("http://ubuntuforums.org/showthread.php?t=599965") i si vols passar i presentar-te al [fil de presentació]("http://ubuntuforums.org/showthread.php?t=562776"), doncs, ja saps :)

---

### Post by Molsa on 2009-04-10
Gràcies. Miraré de fer tot això.

---

