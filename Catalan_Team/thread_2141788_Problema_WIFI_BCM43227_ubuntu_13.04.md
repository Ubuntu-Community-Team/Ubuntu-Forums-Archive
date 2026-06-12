---
title: "Problema WIFI BCM43227 ubuntu 13.04"
date: 2013-05-03
forum: Catalan Team
---

### Post by Aleix1379 on 2013-05-03
Hola, estic utilitzant ubuntu 13.04 amb un acer 5750G amb l'adaptador sense fils, he provat de tot però no me'l detecta.
```
aleix@aleixgnu:~$ iwconfig 
vmnet8    no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

vmnet1    no wireless extensions.
```

```
aleix@aleixgnu:~$ lspci  | grep Network
03:00.0 Network controller: Broadcom Corporation BCM43227 802.11b/g/n

```

[IMG]http://i.imgur.com/fCSWISW.png[/IMG]

[IMG]http://i.imgur.com/IwviasS.png[/IMG]

---

### Post by wgarcia on 2013-05-04
Primer l'obvi, per si un cas tot i que segur que és el primer que has mirat, si l'ordinador té un botonet  per habilitar/deshabilitar l'antena wifi, està engegat, oi?

Segon, es pot mirar si el wifi està bloquejat per alguna raó. Per això es pot obrir una terminal (ALT-F2, entrar "terminal" i intro) i a la terminal entrar:

```
rfkill list all
```

i enganxa el que surti.

---

