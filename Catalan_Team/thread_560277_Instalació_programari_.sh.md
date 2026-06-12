---
title: "Instalació programari .sh"
date: 2007-09-26
forum: Catalan Team
---

### Post by prostata on 2007-09-26
He baixat aquest programa
 Xine-lib  1.1.8 i l'he tractat am file roller, un cop extrets tots el adirecotris arxiu i demés ara no sé com instalar-lo. Hi Ha un arxiu install.sh però.... ¿un cop de má, gracies....???

Salut

---

### Post by papapep on 2007-09-26
Vols dir que et cal una versió de llibreries que no és als repositoris oficials??
Per què les vols?

---

### Post by prostata on 2007-09-26
> **papapep said:**
> Vols dir que et cal una versió de llibreries que no és als repositoris oficials??
Per què les vols?

Doncs perquè l'interficie gràfica dels reproductors de video que son als repos. no m'agradan, ni totem i a més MPlayer movie paler no em funciona, així doncs és per això que voldria instal-lar aquest programa.

Salut

---

### Post by papapep on 2007-09-26
Doncs això que estàs intentant instal·lar no és un programa en si, són unes llibreries que fan servir altres programes.

Prova l'VLC, si no ho has fet ja:

```
sudo aptitude install vlc
```

Ves amb compte, si t'instal·les programes que no controles i no els instal·les de la manera "ubuntu" t'estàs jugant tornat-te a quedar amb un sistema que no et funcioni o tingui molts problemes.

---

### Post by prostata on 2007-09-26
> **papapep said:**
> Doncs això que estàs intentant instal·lar no és un programa en si, són unes llibreries que fan servir altres programes.

Prova l'VLC, si no ho has fet ja:

**Si, ja el tinc instal-lat, però amb tots els respectes, es que els trobo gràficament molt pobrets, i admeto que va bé però...a jo m'hagarden els gràfics, que vols que li faci ;-)**

```
sudo aptitude install vlc
```

Ves amb compte, si t'instal·les programes que no controles i no els instal·les de la manera "ubuntu" t'estàs jugant tornat-te a quedar amb un sistema que no et funcioni o tingui molts problemes.

**Si...si, ja hi compto amb aquesta "amenaça" i per això no ho he fet encara....**

---

### Post by Ferri on 2007-09-26
Tornant a la pregunta original:
```
./install.sh
```

---

### Post by patrickfromspain on 2007-09-26
les llibreries de xine son al synaptic... que vols fer exactament? Fins on jo se.. xine nomes es el motor, i la interficie grafica va a part.

---

### Post by papapep on 2007-09-26
Nois, crec que hem de tenir una miqueta de calma en contestar, que aquests últims dies el fòrum s'està tornant complicat de seguir i de que ens serveixi a tots plegats...

A veure, en próstata volia instal·lar el paquet Xine-lib 1.1.8  per que _es pensava que és un programa de reproducció de música_ o del que sigui.
Aleshores, no té sentit explicar-li com instal·lar-lo, ja que no li servirà de res.

próstata, si ho vols instal·lar fes-ho, però no et farà servei pel que tu vols. Com et diu en patrick, els motors de reproducció són poquets, i les interfícies gràfiques que hi posen com una "mascara" per a fer-nos-ho més bonic en són un munt, i no has de confondre una cosa amb l'altra.
Per que sigui més entenedor, és com si a un mateix motor de cotxe li fiques diferents carrosseries i de diferents colors. Segueix sent el mateix motor i correrà igual de bè o malament.

---

### Post by Ferri on 2007-09-26
Totalment d'acord. Crec que perquè no li calia instal·lar el xine-lib en qüestió ja ho heu deixat prou clar.
Tot i això, tard o d'hora és molt probable que es trobi amb algun altre *.sh que voldrà executar i ara ja sabrà com fer-ho, i per això ho he posat.
Hauria d'haver estat més clar i haver especificat primer que no cal, repeteixo, instal·lar el xine-lib. Disculpes si he causat alguna confusió.
Pel que fa a l'interès inicial, que era buscar una interfície millor que vlc o totem, suggereixo el kaffeine, tot i que és un programa per a KDE.

---

### Post by orestesmas on 2007-09-26
> **Ferri said:**
> Totalment d'acord. Crec que perquè no li calia instal·lar el xine-lib en qüestió ja ho heu deixat prou clar.
Tot i això, tard o d'hora és molt probable que es trobi amb algun altre *.sh que voldrà executar i ara ja sabrà com fer-ho, i per això ho he posat.

Jo hi hauria afegit que abans de provar d'executar-lo hauria d'haver activat el permís d'execució. Molts scripts d'instal·lació no el porten activat, i això és una font de maldecaps per als usuaris novells. O sia:

```
$ chmod u+x install.sh
```

I a més afegiré que probablement haurà d'executar la instal·lació amb permisos de superusuari si vol instal·lar a nivell de tot el sistema i no només per a ell:

```
$ sudo ./install.sh
```

> 
Pel que fa a l'interès inicial, que era buscar una interfície millor que vlc o totem, suggereixo el kaffeine, tot i que és un programa per a KDE.

Cadascú té els seus gustos amb els programes. A mi m'agrada el xine a seques perquè m'he acostumat a les seves dreceres de teclat.

---

### Post by prostata on 2007-09-27
Company papapep:

Doncs no. L'objectiu no es pas tant instal-lar un soft determinat, no. L'objectiu principal és com es tracten els scripts i/o els .sh que si fa o no fa son el mateix.
Si aprenc a fer això ja ho sabre per un altre vegada, sino i com molt bé deies en altre post (GRUB), ¿cóm vols que els no en sabem Linux aprenem??

No tot està dins els repos, ni dins mateix de Ubuntu. Això és una questió  molt personal i no és ni serà l'última vegada que em trobo amb .sh i vull saber què ès i com ès tracta, prescindin del soft. al que fa o faci referència. Això és tot

Salutacions

---

