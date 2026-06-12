---
title: "Konsole: no puc escriure"
date: 2009-05-11
forum: Catalan Team
---

### Post by vallibona on 2009-05-11
Hola a tots
Des de que el sistema ha passat a Kubuntu 9.04, entre d'altres problemes potser menors, no he pogut fer anar Konsole.
En concret, el que em passa és que l'aplicació engega bé, els menús funcionen...però no puc escriure (o no veig el que escric)
Per tant, no puc fer res per solucionar els altres problemes menors....
A algú li ha passat?

He buscat una mica i he trobat:
[http://www.mail-archive.com/debian-user-catalan@lists.debian.org/msg02128.html](http://www.mail-archive.com/debian-user-catalan@lists.debian.org/msg02128.html) (no puc esborrar l'arxiu que diu perquè no el tinc)
a [http://canllaith.org/articles/kde4-understanding-the-buzz/](http://canllaith.org/articles/kde4-understanding-the-buzz/) parla de l'existència de problemes de redibuixat a Konsole, però no aporta resposta...

Tinc un PIV 3'2ghz, amb gràfica Nvidia, Kubuntu 9.04 KDE 4.2.2
Moltes gràcies
Salutacions

---

### Post by mcako on 2009-05-11
En el primer link que has posat no t'està dient que esborris cap arxiu, simplement t'està dient que canviïs la font de lletra des de la configuració de Konsole i també que provis de canviar la font des des del Centre de Control.  
Ho has provat?

---

### Post by orestesmas on 2009-05-12
Això que dius és força estrany. Jo no m'hi he trobat en cap de les actualitzacions que he fet.

Has provat que no sigui que tens el mateix color de lletra que el fons? Si et funcionen els menús, pots anar a Arranjament -> Edita el perfil actual -> Aparença i escollir-ne una d'estàndard.

De tota manera, a mi em sona a algun problema en el sistema de paquets o les dependències.
Per veure què passa et diria que obrissis una consola, però com que no et funciona :-)

Mira, de moment pots instal·lar-te un altre programa de terminal, com per exemple xterm. Una vegada el tinguis operatiu, fes les següents coses:

1) Obre un xterm i digues quina versió de konsole tens:
```

dpkg -l konsole*

```

2) Per tal d'arreglar possibles paquets que t'hagin quedat sense configurar, fes:
```

sudo apt-get -f install
sudo dpkg --configure --pending

```

A veure si això millora alguna cosa.

---

### Post by vallibona on 2009-05-12
Hola Mcako i Orestes
Moltes gràcies per la vostra ajuda.
He provat a canviar la font i el color, i l'única cosa que he aconseguit és que el requadre previ al text em surta de color verd, tal i com li he dit, però no apareixen les lletres.

He afegit xterm des del repositori, però no sé com engegar-lo (a /usr/bin apareix un arxiu "xterm" que no respon a clicks.

He desinstal·lat i tornat a instal·lar Konsole des del gestor de paquets, però res....
No sé que pot passar....

---

### Post by orestesmas on 2009-05-13
Quan instal·les xterm no te'l fica en algun lloc del menú? És estrany...

De tota manera, és igual: Si prems Alt-F2 pots executar qualsevol ordre "a mà".

Això teu cada vegada sona més a algun problema de configuració. Jo provaria d'esborrar completament la configuració de Konsole per tal que la torni a regenerar de zero. Cal esborrar el fitxer:

```

/home/<el_teu_nom_d'usuari>/.kde/share/config/konsolerc

```

Després tornes a engegar konsole a veure què tal.

NOTA: Si vas via Dolphin tingues en compte que el directori ".kde" està ocult (té un punt davant) i que per veure'l li has d'indicar a Dolphin que mostri els directoris ocults (amb "Alt+.", o via menús)

---

### Post by vallibona on 2009-05-14
Moltes gràcies per l'ajuda
He fet el que m'has dit, amb el següent resultat:
-ALT+F2 (per executar via text l'aplicació xterm) : no passa res, no s'obri cap programa
-Borrar l'arxiu de configuració de Konsole: ho he fet, però al rearrancar Konsole tot continua igual....
Salutacions!

---

### Post by kimet on 2009-05-14
Per arrencar una aplicació gràfica has de posar "DISPLAY=:0.0" avans de la ordre.

alt+control+f1
```
DISPLAY=:0.0 xterm
```

Després tornar al mode gràfic amb: alt+control+f7

Salut.

---

### Post by indiosincracia on 2009-05-18
una altra opció és instal·lar-te el yakuake des d'els repositoris, és un emulador de terminal que un cop l'engeguis des del menú, prement la tecla F12 et baixarà al estil del famós videojoc quake.

---

### Post by vallibona on 2009-05-19
Gràcies Indiosincracia....he instal·lat Yakuake sense problema, però tampoc funciona....
Des de Yakuake he provat a canviar color, tipus i dimensions de la font, sense èxit...
Què passa?

---

### Post by vallibona on 2009-05-19
I el tema del DISPLAY=:0.0 xterm tampoc ha tingut èxit.....
En un primer intent, al teclejar-ho el sistema s'ha quedat "penjat?" sense respondre a cap instrucció, després d'anunciar "ERROR 32 (...) not enought ptys" de manera que he hagut de reengegar a les braves.
I ara, quan teclejo ctrl+alt+F1, la pantalla s'ompli de ratlles i prou....
La veritat, ja no sé que fer......

---

