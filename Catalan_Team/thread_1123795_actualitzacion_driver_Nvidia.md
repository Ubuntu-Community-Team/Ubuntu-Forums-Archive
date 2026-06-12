---
title: "actualitzacion driver Nvidia"
date: 2009-04-12
forum: Catalan Team
---

### Post by venusfenix on 2009-04-12
bona nit,

Tinc un AMD 64x2 i tinc instal.lat un ubuntu 64 bits


m'acabo d'actualitzar el driver de la tarja de video.
de la versio 173 a la 180.

despres de fer l'actualitzacio, surt la pantalla de sessio, i quan comença a carregar l'escriptori, es torna tota la pantalla en negre, pel so, se que tot funciona be, excepte la pantalla o sigui el video, com puc fer per desfer l'ultima actualizacio.

gracies,

---

### Post by RainCT on 2009-04-13
Amb Ctrl+Alt+F1 pots acccedir a una terminal. Allà fes «sudo nano /etc/X11/xorg.conf» i al fitxer que se't obrirà busca la part que digui «Section "Device"» i modifica-la perquè quedi així (o si no hi és, afegeix-la):

```

Section "Device"
        Identifier    "Configured Video Device"
        Driver        "nv"
EndSection

```

Llavors desa amb Ctrl+O i Enter, i surt de l'editor amb Ctrl+X. Finalment, torna a iniciar els gràfics amb: ```
sudo /etc/init.d/gdm restart
```

Llavors estaràs utilitzant els controladors lliures i si vols tornar als d'NVIDIA pots fer-ho utilitzant la interfície gràfica.

---

### Post by MiquelBLL on 2009-04-16
A mi em va passar semblant, vaig actualitzar el driver al 180 i llavors al tornar a iniciar en sortia la resolucio a 800x600 cuan la tenia a 1280x800,pero al meyns s´en veia, vaig editar el xconfig i seguin lo que vaig trobar per internet i l´ajuda d´algu mes ho vaig sol.lucionar.

---

