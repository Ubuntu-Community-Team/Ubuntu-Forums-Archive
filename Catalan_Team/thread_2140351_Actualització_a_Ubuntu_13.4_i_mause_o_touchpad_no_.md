---
title: "Actualització a Ubuntu 13.4 i mause o touchpad no funcionen"
date: 2013-04-29
forum: Catalan Team
---

### Post by rialler on 2013-04-29
Hola a tothom,

Vaig actualitzar el ubuntu a la versió més recent, la 13.4 (x64) i al fer-ho doncs hem trobo que tot funciona perfectament però el ratolí i el touchpad no hem responen. 
He provat de reiniciar-lo no fos cas que al estar ja connectat al iniciar-se doncs no el reconegués (no seria la primera vegada que amb altres computadores m'ha passat) però no don resultat.
EL ubuntu el tinc instal·lat en una partició i en l'altre tinc Windows 8 (x64), però no crec que influeixi en res ja que abans hi tenia el ubuntu anterior i funciona perfectament.

Si algú pogués donar-me alguna solució o recomanació seria de agrair, sinó hauré de tornar a la versió que ja tenia.

En tot cas moltes gracies.

Xavier Riu

---

### Post by wgarcia on 2013-04-29
Per poder esbrinar una mica què està passant hauries de donar el màxim d'informació sobre el sistema: marca, model, memòria RAM, targeta gràfica, etc.

---

### Post by rialler on 2013-04-30
El model es un HP Pavilion dv6 amb les caracteristiques següents:
- memoria ram de 4G
- QuadCore Intel Core i7 720QM   2766 MHz
- grafica: ATI Mobility Radeon HD 5000 Series (Microsoft Corporation - WDDM v1.20) (1024 MB)
- targeta de so: ATI Radeon HDMI @ ATI Redwood/Madison - High Definition Audio Controller

---

### Post by wgarcia on 2013-04-30
Dues preguntes:

1) Vas fer instal·lació nova o vas actualitzar la que tenies?

2) Tens un CD o USB amb el que provar la versió 13.04 sense instal·lar (el que es diu sessió autònoma o "live" en anglès)?

---

### Post by rialler on 2013-05-01
les dues coses, vaig actualitzar el que tenia i llevors al arrencar-se doncs es devia haver produit un error perque la pantalla quedava amb negre i amb alguna linea de text i feia pampallugues i no s'arrencava.
Llevors vist l'èxit, vaig reinstalar directament la versió nova a traves de un live i en el live el mause i tot anava correctaent, però una vegada instalat altre cop, al iniciar ho fa tot correcte pero el mause ni el touchpad no responen. El teclat respon a la perfecció pero si he de accedir a tota la interface a traves del teclat...

---

### Post by wgarcia on 2013-05-01
Tens unitat de CD? He vist alguns informes de gent que diu que creant el CD Live de la manera habitual (que és usant un programa que es diu "unetbootin") es van quedar amb alguns dispositius USB com el ratolí tàctil i normal sense funcionar, però creant-lo amb el "Creador de disc d'arrencada" els va funcionar. Suposo que ja no tens la versió anterior, perquè l'actualització també hauria de funcionar, el problema gràfic que vas tenir en iniciar potser era degut a què no es van reinstal·lar bé els controladors gràfics de la targeta ATI que tens.

---

### Post by rialler on 2013-05-01
doncs probare de crear el live amb el creador de disc d'arrencada aviam si puc conseguir que hem funcioni, gracies.
Si no hem funciona ja tornare a postejarho

---

### Post by wgarcia on 2013-05-02
I si et funciona comenta-ho també, així queda constància si a algú altre/a li passa

---

### Post by rialler on 2013-05-02
Al final ha funcionat perfectament, el que no arribo a concebre és el perquè des de usb falla i amb dvd no... En el cas de que no disposes de un lector de CD/DVD estaria ven fomut...

en tot cas moltes gràcies.

---

### Post by wgarcia on 2013-05-02
D'acord, estaria bé si poguessis marcar aquest fil de debat com a "Solved", cosa que es fa editant el primer missatge ,clicant "Advanced" i escollint "Solved" a "Prefix". 

Sembla un error a unetbootin, potser no posa els controladors necessaris per a alguns dispositius USB. Ara miraré a veure si hi ha un error reportat i si no hi ha intentaré reproduir-ho i entrar un.

---

### Post by wgarcia on 2013-05-03
He estat investigant i no he trobat cap informe d'error, però fent una cerca més general sembla que és una cosa que li passa a molta gent, i per això vaig trobar la solució que et vaig suggerir. Per tant estaria bé, si tens un moment, que entressis un informe d'error, i després tornessis aquí i entressis l'enllaç. T'indico els passos per entrar l'informe d'error:

1) Navega a [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu), i crea't un compte d'usuari

2) Entra ALT-F2 i a la finestra que s'obre entra 

```
ubuntu-bug unetbootin
```

Ves contestant les preguntes, i quan s'obre la finestra del navegador i et deixi escriure, a títol posa-li "Unetbootin not installing proper touchpad and mouse support in bootable USB", al resum posa "Creating a bootable USB with unetbin to install Ubuntu 13.04 let me without touchpad and mouse support, which was working on a live session for my system. Creating instead the image with 'Startup disk creator' worked perfectly".

---

### Post by rialler on 2013-05-03
he reportat el bug com m'has sutgerit, però per posar el thread com a solucionat seguint les teves indicacións no hem surt res de prefix, si que puc editar el titol del primer post però n hem surt pas la elecció de canviar el prefix. Fins i tot he buscat no fos cas de que fos un error de novato en aquest forum en la adreça [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

pero n hem surt tal opció

---

