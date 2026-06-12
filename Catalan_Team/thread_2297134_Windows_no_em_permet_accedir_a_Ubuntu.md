---
title: "Windows no em permet accedir a Ubuntu?"
date: 2015-10-01
forum: Catalan Team
---

### Post by slink on 2015-10-01
Hola a tothom!

He instal·lat Ubuntu 15.05 en un HP Pavillon amb Windows 8.1 seguint aquest tutorial:

[http://www.pcsteps.com/961-install-ubuntu-linux-windows/](http://www.pcsteps.com/961-install-ubuntu-linux-windows/)

Tot el procés ha anat be, Ubuntu s'ha instal·lat correctament, he iniciat una sessió Ubuntu amb normalitat. 

Després he reiniciat, li he indicat al GRUB que volia inicar sessió en Windows i també hi he accedit correctament. 

Llavors he reiniciat l'ordinador (desde Windows) i ja no ha aparegut la pantalla de GRUB (!), només la pantalla de la BIOS.

Quan intento accedir a Ubuntu em surt una pantalla blava:

"No se ha encontrado ningún dispositivo de arranque.
Instale un sistema operativo en su disco duro"

Desde Windows ja vaig desactivar el "Fast Boot", i desde la BIOS veig que "Secureboot" també està descativat.

Que més puc fer?

Windows ha modificat el sistema d'inici i no em deixa accedir a Ubuntu?

---

### Post by wgarcia on 2015-10-02
Sí, és possible que Windows hagi tornat a escriure els sectors d'arrencada del disc. Has fet alguna cosa quan estaves a Windows que pogués afectar el disc d'arrencada? 

Hi ha procediments per recuperar l'arrencada, però si vols conservar la partició que tens Windows, o tens dades que puguis perdre, s'ha d'anar amb cura. Per tant si tens dades abans de començar a remenar jo faria còpia de seguretat de tot. També és important saber si tens disc de recuperació de Windows per si t'interessa conservar-lo de totes, totes. Potser pots crear un abans de començar a provar coses. 

Per tenir millor idea de com estan organitzades les particions, podries iniciar el sistema amb una memòria USB o un DVD d'instal·lació de l'Ubuntu, posar "Provar"  (no instal·lar), i un cop iniciat l'Ubuntu obrir el programa "gparted". Una foto o una captura de pantalla del que mostra aquest programa pot mostrar com tens organitzades les particions del disc.

---

### Post by slink on 2015-10-05
> Has fet alguna cosa quan estaves a Windows que pogués afectar el disc d'arrencada? 

La única cosa, diguem-ne "anormal" va ser que vaig 'reiniciar' desde Windows, en lloc d''aturar' i 'encendre' l'ordinador. Windows va fer un reinici molt ràpid, sense carregar la BIOS. Va ser com tancar i reobrir la sessió.

Tornaré a instal·lar Ubuntu d'aquí unes setmanes, quan surti la versió 15.10, i procuraré no 'reiniciar' mai desde Windows, sinó 'aturar' i 'encendre' l'ordinador, com Déu mana.

---

### Post by wgarcia on 2015-10-06
Això de reiniciar des de Windows no hauria de ser un problema. A no ser que iniciïs una "recuperació" des de Windows, perquè en aquest últim cas Windows reescriu els sectors d'arrencada del disc i desapareix el grub.

---

### Post by fvilaubi on 2016-04-18
em va passar el mateix amb un Dell i7. Però jo vaig deixar UEFI i Secure Boot activats, i em pensava que per això em passava. La veritat es que després del "susto" de veure que no hi havia Ubuntu, vaig dir que em refés les particions amb el DVD d'instal·lació, i miraculosament em va tornar a aparèixer el Ubuntu perfectament carregat i configurat, com l'havia deixat. No se que més es pot fer per que la veritat es que NO he tornat a engegar el Windows 10 que porta de fabrica, per por a que em torni a deixar sense Ubuntu.

---

