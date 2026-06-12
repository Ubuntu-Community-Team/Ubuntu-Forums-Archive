---
title: "actualització a Ubuntu 10.04 truncada"
date: 2010-05-14
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2010-05-14
Bones.
Tenia un Kubuntu 9.10 i avui li he afegit l'escriptor gnome.
A anat bé i he pogut entrar amb gnome.

Després he volgut actualitzar a 10.04, a mig fer, un missatge m'ha dit que no es podien baixar tots els paquets. A més, l'ordinador s'ha quedat penjat. Cap tecla feia res.

En reiniciar, amb el primer kernel,hem surt aquest missatge:
mount: mounting none on /dev failed: No such device"

Després diu:
"No es pot obrir el fitxer tema /usr/share/kde4/apps/themes/oxygen-air"

En acceptar aquest missatge, queda la opció:
"Kubuntu login:"

Aleshores, hem logo amb el habitual usuari i executo "startx" per iniciar entorn gràfic.

Tot seguit surt aquest missatge:
"Install problem! The configuration defaults Gnome power manager have not been installed correctly."

A partir d'aquí no se com recuperar la insta&#320;lació.
He provat el recovery mode del grub i no hem soluciona res.

Algú hem dona un cop de ma? sisplau.

---

### Post by Miquel Ubuntero on 2010-05-15
Hola de nou.
Avui, amb una mica més de calma, he pogut solventar el meu problema.
Ho explico per si algú l'interessa.

Al PC en qüestió hi tenia 2 kernels. Tot allò que vaig escriure en aquest post, era referent al kernel més nou.

dons bé. amb el kernel més antic, avui he pogut fer des de Terminal, un apt-get upgrade i apt-get update. En reiniciar el PC he tingut l'alegria de veure que tot funciona. Això si, amb el kernel més antic.

De moment, he tret el kernel nou que em donava problemes. Ja rumiaré més endavant si actualitzo el kernel.

de moment funciona tot bé, ja no toco res més.

Salut!

---

