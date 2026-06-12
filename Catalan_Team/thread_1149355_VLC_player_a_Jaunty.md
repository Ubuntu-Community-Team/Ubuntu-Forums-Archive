---
title: "VLC player a Jaunty"
date: 2009-05-05
forum: Catalan Team
---

### Post by Daerun on 2009-05-05
Això no és un veritable problema, però sí que és bastant empipador y també molest. Des que em vaig instal·lar la Jaunty, quan obro un vídeo amb el VLC, aquest es reprodueix en una finestra externa al reproductor. He probat d'anar a Eines > Perferències > Interfície i marcar la casella "integrar vídeo al reproductor" però segueix igual; a algú més li passa? :confused:

---

### Post by kukat on 2009-05-05
Si! a mí... (per descomptat :) ) però com funciona tan bé el reproductor que ve per defecte (abans amb l'Intrèpid no funcionava tan bé...) de moment no havia comentat res! 

Probablement siga degut als "drivers" de la targeta de vídeo (de l'ATI)...per que últimament estic tenint un munt de problemes per culpa d'aquesta. Incloent un X Server Fatal Error alguna que altra volta(igual relacionat amb el compiz)...seguirem informant...jeje

Salut!

---

### Post by torracastanyes on 2009-05-05
El meu fa el mateix, i no tinc ATI. Si no recordo mal, els primers díes obría la pantalla en la finestra del reproductor, però després va canviar. Esperem que la propera actualització torni a la "normalitat".

---

### Post by socderafel on 2009-05-05
iep! a mi també m'ho fa... passar no passa res, però m'agradava tindre-ho tot a la mateixa finestra encara que estiguera maximitzada...

---

### Post by Daerun on 2009-05-05
Ah, doncs ja veig que la cosa és "normal" com allò del gestor d'actualitzacions :lol:

Kukat, jo també he notat que el reproductor per defecte (que no té cap nom?) funciona de meravella :D

---

### Post by torracastanyes on 2009-05-05
Crec que el reproductor per defecte es diu "TOTEM". Es el que utilitzo més, però de vegades se l'hi travessa algún format i el VLC no sol tenir problemes per obrir-lo.

---

### Post by Daerun on 2009-05-07
Totem, això mateix :P

Ho he consultat, i sembla ser que això de no tenir el vídeo a la mateixa instància és una cosa que ve de sèrie des de la versió 0.9

[http://ubuntuforums.org/showthread.php?p=7231059#7](http://ubuntuforums.org/showthread.php?p=7231059#7)

Es veu que hi havia algun bug que els va obligar a que el vídeo es mostrés per separat. Una solució per qui ho vulgui com era abans, és instal·lar-se l'alfa de la versió 0.9.9 o la prèvia de la 1.0, afegint aquestes fonts a la llista de programari de tercers:

[I]0.9.9a
[https://edge.launchpad.net/~medigeek/+archive/ppa]("https://edge.launchpad.net/%7Emedigeek/+archive/ppa")
1.0
[https://edge.launchpad.net/~kow/+archive/ppa]("https://edge.launchpad.net/%7Ekow/+archive/ppa")
[/I]
Jo m'he instal·lat la 1.0 i sembla que no tinc cap problema :D

---

### Post by socderafel on 2009-05-12
d'on et baixes el programa? no el trobe a la web que has posat...

---

### Post by Daerun on 2009-05-13
A la part inferior de qualsevol dels dos enllaços hi ha un llistat, i una de les entrades és el vlc... De totes maneres, si hi cliques veuràs que et surten una vintena de paquets per baixar i instal·lar, de manera que el millor és afegir el repositori a la llista de programari de tercers: en ambdós casos és el requadre que hi ha a sota de la llista desplegable que diu "Display sources.list entries for"; aqui selecciones la teva versió d'Ubuntu, i després només cal que copiis la primera direcció als repositoris :D

---

### Post by simfomet on 2009-05-14
Vet aquí la solució pel tema que he trobat googlejant del VLC que he provat i va la mar de bé. S'ha tret un patch para resoldre-ho que té compilat el VLC con dicho patch. El repositori per Jaunty és aquest: [B]deb [http://ppa.launchpad.net/medigeek/ppa/ubuntu](http://ppa.launchpad.net/medigeek/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/medigeek/ppa/ubuntu](http://ppa.launchpad.net/medigeek/ppa/ubuntu) jaunty main[/B]

 I per afegir la clau que no se us oblidi això en una consola:
[B]
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com B5140445[/B]

---

### Post by marteljorge on 2009-05-14
> **simfomet said:**
> Vet aquí la solució pel tema que he trobat googlejant del VLC que he provat i va la mar de bé. S'ha tret un patch para resoldre-ho que té compilat el VLC con dicho patch. El repositori per Jaunty és aquest: [B]deb [http://ppa.launchpad.net/medigeek/ppa/ubuntu](http://ppa.launchpad.net/medigeek/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/medigeek/ppa/ubuntu](http://ppa.launchpad.net/medigeek/ppa/ubuntu) jaunty main[/B]

 I per afegir la clau que no se us oblidi això en una consola:
[B]
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com B5140445[/B]

Doncs jo duc uns anys com a administrador i és el primer cop que veig una cosa així, i es podria dir que tinc el nòbel en errades(sofrides per mi).
per afegir la línia al sources.list, res millor conec que un ```
sudo echo deb-src http://ppa.launchpad.net/medigeek/ppa/ubuntu jaunty main > /etc/sources.list
sudo echo deb http://ppa.launchpad.net/medigeek/ppa/ubuntu jaunty main 
```

---

### Post by papapep on 2009-05-14
> Doncs jo duc uns anys com a administrador i és el primer cop que veig una cosa així, i es podria dir que tinc el nòbel en errades(sofrides per mi).
per afegir la línia al sources.list, res millor conec que un 

És que això:

> sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com B5140445

és per afegir les claus gpg al sistema i poder validar el repositori, no per afegir les línies del repositori en sí a l'/etc/apt/sources.list, que es pot fer, entre moltes altres maneres, com t'ho has indicat :)

---

### Post by marteljorge on 2009-05-14
No, per obtindre les claus, faig ús del gnupg com a usuari "normal", i , després d'exportar-les, les importo com a usuari primari.

---

### Post by simfomet on 2009-05-14
Jo ja no entro en el que comenteu ja que em considero encara força novell en el tema. Senzillament ho he trobat googlejant i m'ha funcionat perquè VLC tingui només una finestra que és el que volia

---

