---
title: "Nomes tinc xubuntu i apareix error unknown filesystem grub rescue"
date: 2013-08-09
forum: Catalan Team
---

### Post by simfomet on 2013-08-09
Hola a tots, 

  tinc un portàtil amb xubuntu 13.04 instal·lat (**només xubuntu, ni windows ni res més**) i de repent fa un parell de dies al posar-lo en marxa apareix:

error unknown filesystem grub rescue

Vaig creure que restaurant el grup amb el supergrubdisk o rescatux ho solucionaria però res de res, ho he provat i no hem funciona. No sé què fer. Algún consell?

---

### Post by wgarcia on 2013-08-11
Aparentment el grub, el programa que inicia el sistema operatiu, no pot trobar el sistema de fitxers on està configurat per arrencar el Xubuntu. Això pot ser degut a què el grub s'hagi desconfigurat, o menys probablement, a què hi hagi algun problema real al disc on s'ha de arrencar el sistema, o bé perquè ha estat reformatejat o perquè tinc algun problema de maquinari. Esperem que sigui el primer, simplement un problema de desconfiguració del grub. 

Per intentar reparar aquest problema el millor és usar un sistema que es diu "Boot-repair". Mira si te'n pots sortir usant les instruccions (en anglès) d'aquest enllaç:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Si no t'aclareixes ho podem continuar comentant aquí.

---

