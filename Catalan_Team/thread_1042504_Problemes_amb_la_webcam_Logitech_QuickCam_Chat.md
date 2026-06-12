---
title: "Problemes amb la webcam Logitech QuickCam Chat"
date: 2009-01-17
forum: Catalan Team
---

### Post by jmaspons on 2009-01-17
Hola,

Sóc lluny de casa i m'he decidit a comprar una webcam que ara em dona problemes. Sembla que linux la detecta:
```
joan@joan-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 046d:08da Logitech, Inc. QuickCam Messanger
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

El nom és diferent del de la caixa (QuickCam Chat / QuickCam Messanger) però suposo que no és important. Amb l'Skype és veuen imatges psicodèliques de color verd (i sense prendre res estrany!) i amb el Kopete tot negre.

He provat d'instal·lar drivers amb l'easycam2 i he donat força voltes. Em sembla que és una regressió introduida a ubuntu 8.10 intrepid degut a un [bug]("https://bugs.launchpad.net/ubuntu/+bug/267522").

Alguna idea de què puc fer per arreglar-ho o he d'esperar que el temps ho arregli (ubuntu jaunty)?

Gràcies

---

### Post by RainCT on 2009-01-17
Has provat amb el següent?

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so kopete
```

---

### Post by jmaspons on 2009-01-18
Moltes gràcies!!
Fantàstic, ja puc parlar amb la xicota i que em vegi!

Hi ha alguna manera de fer el canvi de variables (o el què sigui això que m'has dit) per defecte? De moment he canviat les entrades del menú i funciona.

Estic molt content! Poder veure la persona que estimes quan estas lluny de casa no té preu, i si és des del linux encara val més :P

Et faria una abraçada!

---

