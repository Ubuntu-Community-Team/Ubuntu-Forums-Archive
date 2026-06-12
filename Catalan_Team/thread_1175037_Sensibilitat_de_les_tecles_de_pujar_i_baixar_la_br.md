---
title: "Sensibilitat de les tecles de pujar i baixar la brillantor de la pantalla"
date: 2009-05-31
forum: Catalan Team
---

### Post by PatrickVogeli on 2009-05-31
Hola gent,

L'unic problema que tinc en Jaunty és que la sensibilitat de les tecles de pujar i baixar la pantalla sembla que no funciona correctament.

La meva pantalla té 8 estats (de 0 a 7) de brillantor, i el problema es que quan el baixo, tipicament fa 7-5-3-1-0; quan puja, 0-2-4-6-7.

Un altre problema relacionat es que, a vegades, quan apreto al tecla de pujar la brillantor, la puja i la baixa, per tant no canvia. Mirant la comanda acpi_listen, es registren 2 codis, el de pujar i el de baixar. Això no ho fa sempre.

Si descarrego el modul video la cosa funciona perfectament, però llavors perdo el control per software de la pantalla: la brillantor no baixa quan funciona en bateria, ni quan l'equip no fa res, etc.

Això funcionava perfectament amb ubuntu Hardy i Intrepid, però fa el mateix a debian 5.0.1. Jo diria que és alguna cosa "upstream", potser del hal? El kernel el descarto, ja que debian no fa servir el mateix i jo n'he provat de diferents (compilats de kernel.org) i fa el mateix.

Hi un bug report aqui: [https://bugs.launchpad.net/ubuntu/+bug/352699](https://bugs.launchpad.net/ubuntu/+bug/352699)
Tema en angles: [http://ubuntuforums.org/showthread.php?p=7378504#post7378504](http://ubuntuforums.org/showthread.php?p=7378504#post7378504)

salut!

---

### Post by PatrickVogeli on 2009-06-04
pujo aquest tema per dir que ja ho he solucionat!

La solucio ha estat senzilla, i l'he trovat per casualitat als grandisims forums de gentoo.

S'ha de carregar el modul video amb l'opcio seguent: brightness_switch_enabled=0

Aixi que podem crear l'arxiu /etc/modprobe.d/video.conf i afegir-hi el següent: options video brightness_switch_enabled=0

despres de recarregar el modul ja funciona com sempre havia fet!

[SOLVED]

---

