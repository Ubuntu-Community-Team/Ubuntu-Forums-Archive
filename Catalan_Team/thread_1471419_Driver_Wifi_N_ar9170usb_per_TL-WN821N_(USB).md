---
title: "Driver Wifi N ar9170usb per TL-WN821N (USB)"
date: 2010-05-03
forum: Catalan Team
---

### Post by dnit on 2010-05-03
Hola gent , bona nit veureu tinc el següent problema vaig comprar un llapis amb un router TP-Link amb wifi N, i el llapis no hi ha manera de que em connecti amb el wifi. El tinc des de fa 3 mesos es el Model TL-WN821N.
Amb la versió 9.04 ni el detectava  no vaig poder fer-lo anar pro amb Lucid la cosa a millorat i si el reconeix a mitges m'explico, si poso al router que funcioni amb Mixed b,g,n es connecta a la primera i puc navegar però si poso nomes Wifi N que es com el vull, no hi ha manera de connectar.
 Tota l'estona em demana la clau però no connecta. La clau que tinc posada es una WPA/PSK. També e de dir que estat buscant i e llegit que hi havia un bug o un fallo amb aixo però no se si esta resolt i per culpa d'això no em puc connectar el llapis. Si em podeu dir alguna solució o necessiteu mes dades os las faig arribar sense cap problema un salut.

lsusb.
```
sergi@sergi-laptop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 006 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 04f2:b064 Chicony Electronics Co., Ltd
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 001 Device 007: ID 0cf3:1002 Atheros Communications, Inc.**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
sergi@sergi-laptop:~$
```

Gracies.

---

### Post by sjappie on 2010-05-27
Translated from Catalan:

People hello, good night you will see I have the following problem I  bought a pencil with a router TP-Link with wifi N, and the  pencil there is not way that I connect with the wifi.  I have it|him since 3 months ago him  the Model TL-WN821N.
With version 9.04 not even it|he|she detected it|him  I could not make it|him to go pro with  Lucid the thing to improved and if he|she|it recognizes it|him halfway I explain, if I put in the router that works with Mixed b,g,n it|he|she connects to the first and can sail  but if I put nomes Wifi N that him how I want it|him,  there is not way to connect.
All the while he|she|it  asks me for the key but it|he|she does  not connect. The key that I have put him a WPA/PSK.  Also e of suggesting|saying  that been searching and read e that there  was a bug or one I fail with aixo but not him if esta  solved and due to this I can not connect the pencil. If you can say me  any solution or need month datum weary bone I make to arrive without any  problem a greeting.               

I have the same problem: my WN821N worked OK at 802.11n in 9.10, but in 10.04 works only in 802.11b/g mode.  Does anyone have a clue?

Thanks in advance.

Alco Warners

---

### Post by papapep on 2010-05-27
Hi, Sjappie.

Seems you didn't see this is the [catalan]("http://en.wikipedia.org/wiki/Catalan_language") speakers subforum; so, if you can't read and write in that language it would be a better choice for you to make your question in the general forum, where english it's the common language. ;)

Cheers.

---

### Post by kimet on 2010-05-27
El driver ath9k no funciona per a claus usb, mira amb ```
dmesg
``` si es el que fas servir.

Mira a aquesta pàgina per aconseguir el driver ar9170:
[http://wiki.debian.org/ar9170usb](http://wiki.debian.org/ar9170usb)

Salut.

---

### Post by GrandTheft on 2010-07-23
sjappie:


in  10.04 works only in 802.11b/g mode.  Does anyone have a clue?

EXACTLY the same here.
Have you found any solution? Someone else, maybe? 

Sry for wrong subforum, but the thread was the best match to my problem..

Regards,
GT

---

### Post by GrandTheft on 2010-07-24
UPDATE: The stick works at N speed outofthebox with kernel 2.6.35 (atm mainline). 

thx go out to elektronenblitz63 from german ubuntuusers.de forum.

Best regards,
GT

---

### Post by papapep on 2010-07-24
> Sry for wrong subforum, but the thread was the best match to my problem..

Then you can use translate.google.com or any other translation engine to translate it to catalan before posting. But no more non-catalan-written posts, please.

Thanks in advance.

---

### Post by GrandTheft on 2010-07-24
[COLOR=#000000]Tot clar! [/COLOR]Gràcies per el suggeriment.

GT

---

### Post by papapep on 2010-07-24
Das war großartig. Vielen Dank! ;)

---

