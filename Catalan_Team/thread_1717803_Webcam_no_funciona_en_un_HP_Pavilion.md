---
title: "Webcam no funciona en un HP Pavilion"
date: 2011-03-30
forum: Catalan Team
---

### Post by Lomarc on 2011-03-30
Hola, a veure si em podeu ajudar!
Tinc un HP Pavilion Entertainment dv6265ea amb kubuntu 10.10 instal·lat.
La webcam no funiona, he provat amb Skype i Cheese i res
He provat d'instal·lar controladors que he trobat per aquí als foros i no hi ha manera

Crec que aquesta informació us pot ser útil per saber que em passa
```
lomarc@lomarcportatil:~$ dmesg | grep -i video
[    0.272538] pci 0000:00:02.0: Boot video device
[    1.217220] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input5
[    1.217274] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   19.121220] Linux video capture interface: v2.00
[   19.149430] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:1810)
[   19.153062] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   19.153996] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[   19.154001] uvcvideo: Failed to initialize the device (-5).
[   19.154114] usbcore: registered new interface driver uvcvideo
[   19.154117] USB Video Class driver (v0.1.0)


```

Espero que em pugueu ajudar!
Gràcies per avançat!

---

### Post by wgarcia on 2011-03-30
Has provat el controlador que hi ha a:

[https://bitbucket.org/ahixon/r5u87x/src](https://bitbucket.org/ahixon/r5u87x/src)

A baix de tot posa les instruccions per instal·lar. No tinc un Pavillion i no sé si aquest controlador val per a tots els models de webcam integrada, em sembla que és per a les webcam Ricoh integrades, però hi ha gent que diu que li serveix per a models 6000 (tot i que no he trobat referències específiques per al teu model).

---

### Post by Lomarc on 2011-03-30
> **wgarcia said:**
> Has provat el controlador que hi ha a:

[https://bitbucket.org/ahixon/r5u87x/src](https://bitbucket.org/ahixon/r5u87x/src)

A baix de tot posa les instruccions per instal·lar. No tinc un Pavillion i no sé si aquest controlador val per a tots els models de webcam integrada, em sembla que és per a les webcam Ricoh integrades, però hi ha gent que diu que li serveix per a models 6000 (tot i que no he trobat referències específiques per al teu model).

Gràcies, aquest controlador si que funciona!!
Moltes gràcies de veritat, com diuen a la meva terra, ets lo puto amo! :)

---

