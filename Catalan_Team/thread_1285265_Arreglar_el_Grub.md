---
title: "Arreglar el Grub"
date: 2009-10-07
forum: Catalan Team
---

### Post by mesmerize on 2009-10-07
Hola,

Us comento el que m'ha passat. Tinc dos discs durs, un amb Ubuntu 8.04 i l'altre amb Ubuntu 9.04. En el primer tenia molts kernels instal·lats i vaig decidir fer neteja i deixar-ne dos. El problema és que vaig fer alguna cosa malament i en el Grub només apareix una entrada i és d'un kernel que ja està desinstal·lat, i per tant no arrenca. Com puc modificar aquesta entrada per que correspongui a un kernel instal·lat?

Salutacions

---

### Post by quitus on 2009-10-07
Pots editar el menu.lst que es troba en /boot/grub des de un live cd o pots fer servir el supergrub que es una aplicació/programet que pots gravar en un disquet i al engegar l'ordinador et recuperarà el grub. Cerca supergrub a internet i hi trobaràs molta informació, sempre va bé tenir un disquet d'aquests a la butxaca.

salut

---

### Post by mesmerize on 2009-10-07
Hola i gràcies per contestar,

El Super Grub Disk ja l'he provat però té masses opcions i no m'aclareixo. Per editar el menu.lst no em fa falta un LiveCD ja que el Grub està instal·lat en el disc dur d'Ubuntu 9.04, i aquest arrenca bé. El problema es afegir una entrada que correspongui al kernel instal·lat al 8.04. No sé si m'he explicat bé, de totes maneres tornaré a provar el SGD.

Salutacions

---

### Post by quitus on 2009-10-07
Hi ha una opció "auto  linux" o alguna cosa així, que a mi sempre m'ha anat bé.

salut

---

### Post by guillemsola on 2009-10-08
Potser et refereixes a grub-install?

De totes formes a males fas l'arxiu /boot/grub/menu.lst i poses

title           Ubuntu 9.04, kernel 2.6.28-15-generi
uuid            1547dded-afc7-4500-b0b3-c36e61cab78e
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=1547dded-afc7-4500-b0b3-c36e61cab78e ro quiet splash
initrd          /boot/initrd.img-2.6.28-15-generic
quiet

és a dir (ja que aquest és un exemple del menu)

title: el que et vingui de gust

uuid: fas un "tree /dev/disk/by-uuid/" i copy-paste del uuid que identifica la partició que vols arrencar

kernel i initrd: al directori /boot de la partició que vols arrencar agafes la versió superior del kernel que tens instalat (fes cas a la numeració)fixa't que a kernel a més fa falta altre cop el UUID

e voilá, crec que amb això pots arrencar la teva partició linux i després fes el grub-install per recuperar totes les altres entrades.

---

### Post by mesmerize on 2009-10-08
Hola

He editat el menu.lst i he canviat la versió del kernel i de initrd per una que crec que està instal·lada, i ara arrenca la partició, però un cop la barra de progrés s'ha completat la pantalla es queda negra i l'ordinador penjat.

---

