---
title: "Lent de reflexes"
date: 2007-10-05
forum: Catalan Team
---

### Post by anigwei on 2007-10-05
Hola de nou!

En aquest ordinador habitualment faig servir Windows (confesso, sóc un dessertor de tant en tant) però també hi ha Ubuntu (actualment Gutsy) i funciona a les mil meravelles.

La única pega és que és "Lent de reflexes". Per exemple, al maximitzar o minimitzar finestres, tot el tema gràfic fa que treballar amb l'ordiandor sigui "cansino". (No tinc res de 3D, només les "animacions" que vénen per defecte).

L'ordinador no és extraordinari ni la gràfica tampoc (celeron 1800, 512 RAM, Geforce 32MB) però amb Windows confesso que de reflexes va molt bé.

Faig servir els drivers restringits d'nvidia, i l'acceleració funciona, pel que sembla.

Què suggeriu?

Gràcies

---

### Post by orestesmas on 2007-10-05
D'entrada jo miraria de descartar que algun procés descontrolat estés ocupant massa temps de CPU. Obre un terminal, executa l'ordre "top" i ves-t'ho mirant una estoneta (és entretingut i tot) a veure si a la part de dalt de la llista apareix algun procés amb el 100% de CPU. Si és així, digues-nos el nom.

---

### Post by anigwei on 2007-10-06
Hola Orestes,

No hi ha cap procés xuclant CPU, està tot correcte. És com si l'ordinador tingués una tarja gràfica SVGA de fa 15 anys, el CPU a l'hora de fer coses es nota ràpid.

Es poden desactivar completament les animacions al maximitzar i tots aquests petits efectes? Potser és això...

---

### Post by CarlesOriol on 2007-10-06
Pot ser que la gràfica tingui poca memòria?

Si la gràfica és en placa base comprova que tinguis prou memòria reservada.

També pot ser que estigui identificant malament la quantitat de memòria de la gràfica. Aquest problema va fastidiar durant força temps el compiz/beril/fusion en gràfiques nvidia.

Si la gràfica t'ho permet canvia el controlador d'nvidia **nvidia-glx** a **nvidia-glx-new** (synaptic)

També pots provar d'assignar manualment la mida de la memòria fent el ja clàssic sudo dpkg-reconfigure xserver-xorg (quan ho pregunti).

Per configurar el compiz insta&#320;la el **compiz-settings-manager** i tindras Sistema->Personal->Advanced Desktop Effects Settings

---

### Post by anigwei on 2007-10-06
Hola Carles,

La gràfica és una Nvidia antiga, la Geforce 256 (Té 32MB de memòria).

Provaré el que em comentes!!

Gràcies

> **CarlesOriol said:**
> Pot ser que la gràfica tingui poca memòria?

Si la gràfica és en placa base comprova que tinguis prou memòria reservada.

També pot ser que estigui identificant malament la quantitat de memòria de la gràfica. Aquest problema va fastidiar durant força temps el compiz/beril/fusion en gràfiques nvidia.

Si la gràfica t'ho permet canvia el controlador d'nvidia **nvidia-glx** a **nvidia-glx-new** (synaptic)

També pots provar d'assignar manualment la mida de la memòria fent el ja clàssic sudo dpkg-reconfigure xserver-xorg (quan ho pregunti).

Per configurar el compiz insta&#320;la el **compiz-settings-manager** i tindras Sistema->Personal->Advanced Desktop Effects Settings

---

### Post by patrickfromspain on 2007-10-08
jo en principi descarto que sigui res de la grafica, sino que diria que es del compiz. Assegura't que estas fent servir el metacity i no el compiz:

Aplicacions -> accesoris -> terminal i alla hi poses aixo:

metacity --replace

i a veure si va millor.

Salut!

---

### Post by CarlesOriol on 2007-10-09
clar que és amb el compiz. Evidentment els requeriments son superiors però segons explica hi ha algun cas en el que es "satura"... això és el que estem cercant no? 
Encara que ell digui que no té res de 3d és per què no enten el funcionament d'aquest però ja ho sobreenteniem oi?

---

### Post by anigwei on 2007-10-09
Bon dia,

Doncs resulta que el Metacity ja el tinc funcionant, ja que el Compiz no funciona perquè no troba acceleració :O:O

Tot i que el driver restringit està instal·lat i no dóna problemes. Vaig notar l'acceleració amb els salvapantalles 3D, abans em fotien la CPU a cent, ara van fins com la seda. Però:

```
root@estel:/etc# compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0100 (rev 10) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
```

Llavors, el driver que tinc en ús és:

```

Section "Device"
        Identifier      "nVidia Corporation NV10 [GeForce 256 SDR]"
        Boardname       "nv"
        Busid           "PCI:1:0:0"
        Driver          "nvidia"
        Screen  0
        Option          "NoLogo"        "True"
        Option          "AllowGLXWithComposite" "True"
EndSection
```


Quin hauria de ser per una tarja antiga, però amb acceleració? Els que comentàveu abans nvidia-glx?

Gràcies eh!!!!!!!!!!!

---

### Post by CarlesOriol on 2007-10-09
Llavors quan dius les "animacions que venen per defecte" a què et refereixes?

Pots copiar.-nos la pantalla d'efectes d'escriptori?

---

### Post by anigwei on 2007-10-09
Perdó, vaig ser molt poc explícit...

Quan deia animacions, no em referia a les meravelles d'avui en dia.

Sinó, per exemple, quan minimitzes, apareix el marc de l'aplicació que poc a poc es va fent petit i "amagant-se" a la barra de sota. Cosa que amb el portàtil és immediata, amb aquest ho fa més poc a poc.

O quan faig un canvi d'escriptori, es veu com va redibuixant les finestres de cada app. (hauria de ser instantàni també).

Gràcies

> **CarlesOriol said:**
> Llavors quan dius les "animacions que venen per defecte" a què et refereixes?

Pots copiar.-nos la pantalla d'efectes d'escriptori?

---

