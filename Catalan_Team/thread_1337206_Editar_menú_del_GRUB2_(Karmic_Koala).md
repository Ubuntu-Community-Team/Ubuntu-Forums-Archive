---
title: "Editar menú del GRUB2 (Karmic Koala)"
date: 2009-11-25
forum: Catalan Team
---

### Post by badChecksum on 2009-11-25
Hola a tothom,

ara fa cosa d'un mes que vaig instalar-me l'Ubuntu 9.10 (reemplaçant el 8.04) i des de llavors que vaig bastant perdut amb el nou GRUB2.
En el seu moment vaig trobar aquest kiwi: [https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2") i vaig aprendre a canviar l'entrada per defecte i el temps d'espera abans de carregar-la automàticament, i amb això ja en tenia prou llavors.

El problema es que avui he actualitzat el kernel (2.6.31-15-generic) i igual que em passava amb el GRUB Legacy ara apareixen 2 entrades noves just al començament de la llista, i l'entrada que queda per defecte ja no és la que jo vull. Abans n'hi havia prou amb editar el menu.lst fent:
```

cd /boot/grub
sudo gedit menu.lst
```
I escriure #'s davant l'entrada del kernel antic per fer-lo desaparèixer de la llista però a la vegada tenir-lo guardat per si el kernel nou donava problemes llavors poder desfer el canvi.

I això és bàsicament el que voldria fer ara... el /etc/default/grub del GRUB2 ja no guarda aquesta informació i no m'acabo d'aclarar amb la wiki (el meu anglès no és tan bo xD).
Una solució poc elegant seria afegir un 2 al camp GRUB_DEFAULT, però m'agradaria saber *què/com* s'ha d'editar per aconseguir el mateix resultat que amb el GRUB antic.

Grax de hantevraso conpadres

---

### Post by Black_02 on 2009-11-25
És molt fàcil, tens que anar **Sistema->Administració->Gestor de paquets Synaptic** una vegada obert tens que buscar un paquet que es diu **startupmanager** en teoria la versió que t'hauria de sortir es la 1.9.12, la instal·les i ja està.
Després vas a **sistema->Administració->StarUp-manager** i d'allí pots configurar el que vulguis del grub: Sistema per defecte, temps limit per arrencar, imatge de fons,...

Jo ho he provat amb Ubuntu 9.10 i no he tingut cap problema, així que tu tampoc n'hauries de tenir cap ;).

---

### Post by badChecksum on 2009-11-26
Gràcies per contestar Black_02, he provat l'startupmanager i realment fa que configurar molts aspectes del GRUB sigui molt més fàcil (si aquest paquet ja existia fa un any i mig... no ho vull saber xD). 
Però aparentment sembla que no permet esborrar entrades de la llista (només em deixa triar quina vull per defecte de les que ja tinc), així que estic com al començament. :neutral:

---

### Post by papapep on 2009-11-26
badChecksum,

La llista que et mostra el GRUB2 reflexa els nuclis que tens instal·lats. Els que no vulguis que surtin, els desinstal·les i ja no sortiran. Ves amb compte a no carregar-te l'actual que et funciona... :)

---

### Post by badChecksum on 2009-11-26
Ara sí! Solucionat.

---

