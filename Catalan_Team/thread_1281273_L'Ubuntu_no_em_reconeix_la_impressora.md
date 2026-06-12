---
title: "L'Ubuntu no em reconeix la impressora"
date: 2009-10-03
forum: Catalan Team
---

### Post by jinglada on 2009-10-03
La impressora-scanner Hewlett-Packard PSC 1400 no la detecta en Ubuntu ja que en Windows si que la veu; ho he hagut de provar perquè necessitava imprimir imprescindiblement un document.

Faig lsusb i veig que si que la veu.

joan@joan-laptop:~$ lsusb
Bus 002 Device 003: ID 04f2:b029 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 03f0:4d11 Hewlett-Packard PSC 1400
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c058 Logitech, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0b05:1751 ASUSTek Computer, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

La resta de perifèrics per USB funcionen tots. Em podeu ajudar, si us palu?

---

### Post by anna_marti_gomez on 2009-10-03
Hola,

a mi em va passar el mateix amb una HP LaserJet 1018. Sé que vaig haver de baixar-me un driver, però ara no sé d'on. Aquí he trobat una adreça que sembla interessant: [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

Quan tinga una mica més de temps, t'ho miro.

anna

---

### Post by jinglada on 2009-10-04
> **anna_marti_gomez said:**
> Hola,

a mi em va passar el mateix amb una HP LaserJet 1018. Sé que vaig haver de baixar-me un driver, però ara no sé d'on. Aquí he trobat una adreça que sembla interessant: [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

Quan tinga una mica més de temps, t'ho miro.

anna

Gràcies Anna. Ja et diré el què!

---

### Post by jinglada on 2009-10-04
> **anna_marti_gomez said:**
> Hola,

a mi em va passar el mateix amb una HP LaserJet 1018. Sé que vaig haver de baixar-me un driver, però ara no sé d'on. Aquí he trobat una adreça que sembla interessant: [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

Quan tinga una mica més de temps, t'ho miro.

anna

Ja ho he fet però al final em dóna un error:

-----------------------------

RE-CHECKING DEPENDENCIES
------------------------
error: A required dependency 'cups (CUPS - Common Unix Printing System)' is still missing.
error: Installation cannot continue without this dependency.
error: Please manually install this dependency and re-run this installer.
---------------------------

Com es fa per instal·lar manualment la dependència cups?

---

### Post by papapep on 2009-10-04
jinglada:

A un terminal:

```
sudo aptitude install cups
```

---

### Post by jinglada on 2009-10-04
> **papapep said:**
> jinglada:

A un terminal:

```
sudo aptitude install cups
```

Gràcies papapep. Ja torno a tenir impressora-escànner.

---

