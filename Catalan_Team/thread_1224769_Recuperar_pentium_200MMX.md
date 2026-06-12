---
title: "Recuperar pentium 200MMX"
date: 2009-07-27
forum: Catalan Team
---

### Post by astarothvg on 2009-07-27
Hola a tothom, es tracta de la pregunta del milió, els fòrums en van plens, quin sistema operatiu posar amb una "cafetera" d'aquest tipus perquè vagi a una velocitat una mica decent i puguis fer alguna cosa? (maleïda crisi).
Fins a vans d'ahir el "trasto" aquest funcionava amb un güindous 98 SE i la veritat era que, estava passable, ara be, quant li vaig provar de endollar un pendrive kingston de 8 Gb. (els senyors de kingston tenen un driver que no serveix per res), no me'n vaig en sortir, després hi vaig provar de endollar un wireless amb usb i també em va dir que me'l endolles per alla on tots ja sabem.
De seguida vaig pensar, linux! aquí hi haurà una sol·lució, be, si però, no correm tant, la màquina es la següent:
CPU Lentium 200MMX
128Mb Ram
3.2Gb de disc dur
Grafica: Matrox Mystique 2MB
L'usb de xarxa es un OvisLink i carrega el modul Ralink rt73usb (això ho se perquè tinc un altre equip amb ubuntu on l'utilitzo, i ho he pogut veure allà).

Be, a hores d'ara ja he provat, xubuntu (es va instal·lar i després de quasi 4 hores de instal·lació arrenca i no ha agafat el ratolí i no em deixa entrar com a user):(, el DammSmallLinux, va ràpid però no tinc suport per el modul de la wireless ni se com instal·lar-lo, el Puppylinux, aquest es el que millor ha anat, ho ha carregat tot, fins hi tot la wireless peró quant el vaig instal·lar al disc dur va començar a anar lent, he baixat el debian xfce liveCD i, em diu que la meva bios no es compatible amb el kernel i ni engega.
Pel que he vist fins ara m'aniria be un sistema tipus DSL però amb la compatibilitat del Puppy, la funció que li vull donar a la "cafetera" aquesta es escoltar musica (mp3, wav, algun CD potser) i baixar algun arxiu d'Internet o consultar el correu (amb dillo es clar, si engego el firefox ja puc anar a fer la birra, que, amb una mica de sort, quant torni haurà acabat d'aixecar-lo:)). pel demés ja tinc altres maquines.
Alguna idea de que posar-hi?:roll:.

Salutacions i gracies.

---

### Post by indiosincracia on 2009-07-28
pots instalar-te la minimal CD ubuntu:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
i un cop instal·lat reinicies amb conexió internet i poses un escriptori lleuger desde la consola
sudo apt-get install xorg xterm wdm fluxbox
[http://www.wikihow.com/Install-Minimal-Ubuntu-Linux](http://www.wikihow.com/Install-Minimal-Ubuntu-Linux)

navegador, instal·la el 
sudo apt-get install links2
desde la consola links2 -g
nivell de friquisme és comparable a la seva rapidesa

quin ratolí tens?

---

### Post by pauelmaco on 2009-07-28
Pots fer servir una versió de puppy que encara és més lleugera que l'original. És la puppyFluxLite i el nom és bastant aclaridor. No gasta res i, jo també tinc un rt73, et puc dir que funciona en un tractor d'onze anys amb 64mb ram i un processador de 266mhz. La veritat és que va molt lleuger. Porta un navegador web gràfic molt lleuger i un per consola.

Aquest és el link:

[http://puppylinux.ca/members/PupFluxlite/pupfluxlite.iso](http://puppylinux.ca/members/PupFluxlite/pupfluxlite.iso)

Per a més informació:

[http://www.puppylinux.org/downloads/puplets/pupfluxlite](http://www.puppylinux.org/downloads/puplets/pupfluxlite)

Sort!

---

### Post by astarothvg on 2009-07-28
Bones, gracies per els vostres consells, ratolí tinc un logitech de 3 botons serial port, pel mouse no hi pateixo es bastant normal, la tarja de so es una sound blaster ISA i tinc una "perla" de Gravis ultrasound que no la munto perquè es mas gran que la placa base i, la veritat, es una reliquia, (un dia d'aquests haure de fer una exposició).

En quant a la minimal, quina? la 6.06 Dapper, o la Hardy?, em detectara i carregara el modul del wireless?, es que despres un cop instal·lat, sense xarxa, feina a instal·lar mes paquets.

No puc accedir als enllaços que em poses Pau  no se que passa però sencillament dona error de càrrega, en quant al puppy he baixat la versió 3.01 i sembla que va quelcom millor però als 15min. de funcionament el "trasto" es "glaça" i l'haig de apagar a lo bestia.

Em faria gracia probar el fluxlite, tambe mirare lo del minimal.
Gracies de nou.
Siau

---

### Post by indiosincracia on 2009-07-28
Baixa't la Ubuntu 8.04 "Hardy Heron" Minimal CD, un cop tinguis la .iso i et disposis a instal·lar hauries de conectar el PC a la red per cable, i iniciar la instal·lació, et detectarà el maquinari i et baixarà els mòduls que necessitis, la conexió del ratolí suposo que és "serial" de bola, haurás de reconfigurar (sudo dpkg-reconfigure xserver-xorg), pel que se la DSL és la única distribució que no dona problemes amb aquests ratolins.

Per la tarja de so, els eslots ISA donaven moltsmalsdecaps si no et detecta a la primera prova això:
[http://rverdugo.blogspot.com/2009/01/configurar-audio-isa-sound.html](http://rverdugo.blogspot.com/2009/01/configurar-audio-isa-sound.html)

una altra opció és xubuntu "Alternate Install CD"
[http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/](http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/)

vaja, n'hi ha per passar-hi la tarda, un dia haurem d'organizar la "Low Tech Friki's Party", ferramentes, cafeteres, olles, i pedals, totes funcionant, seria bo per intercanviar coneixements sub tecnològics.

---

### Post by ilku on 2009-07-29
En cas que no puguis connectar-te per cable amb aquesta maquina, però tinguis una altre que si pugui, pots descarregar-te el aptoncd i gravar-te els paquets que necessitis en un cd.

---

### Post by astarothvg on 2009-07-29
Ostres!!! veig que l'abandonware te mes adeptes del que em pensava.
Senyors agraeixo els vostres esforços però us haig de donar una mala noticia, el trastet ha mort [-o<, te una avaria de hardware que dificilment reparare, m'explico, resulta que la pila de la bios es d'aquelles que van en una caixa damunt d'un xip i, quant es va esgotar, ja vaig haber de fer un invent amb una pila botò soldada com vaig poder amb fils rigids per que la podessin aguantar, ahir al posar la targeta de xarxa la vaig fregar una mica i... , despres de probar de soldarla un altre cop ha deixat de funcionar.
Sent practic veig que per una pila nova em clavaran 3€ i el trasto aquest, que val?, si provant de soldar-la me la carrego, 3€ mes, no val la pena.
Em sap greu pel munt de ferramentes isa que encara volten per aquí casa però, ja mirare de contactar amb algun amic que es dediqui a la reparació de pc's que, de ben segur aquests mes d'una placa tindran tirada "por hay".

Hei! aviseu quant feu la "Party", tinc un 286 amb sense disc dur (2 disqueteres de 3-1/2, una pel S.O. i l'altre per programes) amb monitor verd marcià de 12" el qual vaig salvar de la crema, que sería el rei de la festa.

Salutacions i gracies a tots.

---

### Post by ilku on 2009-07-29
Asta si vols un parell d'andròmines que funcionen jo en tinc, passes per Barcelona i son teus. Son dos k-7 amb 256 mb de ram discs durs, disketeres, i altres. Fins fa poc havien funcionat amb hardy. pero anaven un pel lents i les vaig jubilar. Anava a llençar-los a la deixalleria, aixi que tens aquesta setmana per recollir-los. Capellades no cau tan lluny home :).

Avisa'm si els vols que aguantare aquesta setmana.

---

### Post by astarothvg on 2009-07-31
Perdoneu per no contestar mes aviat.
Ostres!, gracies per l'oferiment ilku però hi han 2 problemes, el primer es que si, tens raó, Capellades no es tant lluny però ... quant hem de baixar a la "capital" ja ens posem malalts, entre els radars la limitació de velocitat i el transit, es un trauma](*,), i el segon es que si porto mes trastos a casa la dona em fa fora ;).

Si aconsegueixo un altre andròmina ja tornaré a demanar-vos consell, gracies a tots pel interès que heu mostrat.

Siau.

---

