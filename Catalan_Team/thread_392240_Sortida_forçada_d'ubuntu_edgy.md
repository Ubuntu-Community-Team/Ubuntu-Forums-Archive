---
title: "Sortida forçada d'ubuntu edgy"
date: 2007-03-24
forum: Catalan Team
---

### Post by ernestux on 2007-03-24
Hola a tots,

Voldria saber si hi ha alguna opció similar a ctrl+alt del , per ubuntu  en els casos en que es penja i no respon ni el ratolí.  Cas que m'ha passat més d'un cop. 

Gràcies

---

### Post by SoggyCornflake on 2007-03-24
> **ernestux said:**
> Hola a tots,

Voldria saber si hi ha alguna opció similar a ctrl+alt del , per ubuntu  en els casos en que es penja i no respon ni el ratolí.  Cas que m'ha passat més d'un cop. 

Gràcies

Hablo un piquito Español.  Hables Portugues? 

pressing ctrl+alt+del works in Ubuntu as far as I know.  When I press it I get the KDE logout dialog box.  (I have Ubuntu, but personaly perfer KDE to Gnome)

ctrl+alt+backspace will restart the Xserver.  This won't reboot the computer, but if X is still reponding, you can get back to your logon screen I think (I'd test it right now, but I'd lose this thread in the process)

I have on rare ocassions had Ubuntu lock up where ctrl+alt+del and ctrl+alt+backspace don't work.  At that point I decided that a hard reset of the computer is required.  Ususally you can force a hard shutdown by pressing and holding the power switch until the computer/laptop shuts down.

---

### Post by SoggyCornflake on 2007-03-24
> **SoggyCornflake said:**
> Hablo un piquito Español.  Hables Portugues? 

I just realized that you posted in the Catalan group.  Sorry to get that wrong.  No puedo escribar en Catalan.

---

### Post by CarlesOriol on 2007-03-24
No way!... we are very pleased to see your posts.

It's great to see the our language it's not and egde for the people likes to help. 

It could be usefull for you to know other way to brute force restart your ubuntu at kernel level: press Alt +  SysRq ( or "pet Sis" - same key as print screen) + B

(pressing At + SysRq + S forces a global disk sync)

---

### Post by MeneK on 2007-03-24
Amb "Ctrl + Alt + BckSp (esborrar)" es reinicia el servidor X. En molts casos fent això t'estalviaràs fer un reset total.

Si tens el sistema totalment penjat, la seqüència correcta per a fer un "reset" segur és:

Alt + SysRq + R (teclat en mode "raw")
Alt + SysRq + S (s'escriu el contingut de tots el buffers al disc)
Alt + SysRq + E (s'envia el senyal "terminate" a tots el processos)
Alt + SysRq + I (s'envia el senyal "kill" a tots el processos)
Alt + SysRq + U (es posen tots els sistemes de fixers en mode de només lectura)
Alt + SysRq + B (reset)

(Jo la recordo com "Raising Skinny Elephants Is Utterly Boring")

SysRq s'anomena "PetSis" als teclats espanyols i és la mateixa tecla que "ImprPant".

---

### Post by elbuit on 2007-03-24
Tal com ha dit abans Menek, es pot emprar Alt+SysReq+

Jo solc fer un Umount per a estalviar-nos corrupcions:
Alt+PetSis+U
I després un Boot o un Off (reinicia o apaga respectivament)
Alt+PetSis+B o Alt+PetSis+O

Encara que fer tot el procés de Menek sols es tarda 1segon més.
Depenent del teclat, la tecla es dirà SysReq o PetSis, sol ser la mateixa de Imprimir Pantalla

---

