---
title: "Començar des de sota zero"
date: 2011-01-08
forum: Catalan Team
---

### Post by JOPECO on 2011-01-08
Hola a tots!

He estat repassant tot el que he pogut entendre, tant per l'idioma com, sobretot, per a l'alt nivell que, per a mí, s'usa aquí.

No he trobat la manera de sortir-me'n.

-Ordinador OKI Anima 3300 (del Carrefur)
-Processador AMD Turion 64  ML-37 (x86 family 15 model 36 stepping 2) ... Per a mí aixó està en xino...
-Bios PHOENIX 2.33
-Audio compatible Azalia integrada (HDA) Compatible Soun Blaster Pro
-Teclat Win-Key
-Wlan Mini PCI 802.11
-Lan Ethernet 10/100
-Adaptador Gràfic nVidia C51MV

Pregunta:
-Què he de cremar i com. Ja estic fart de donar el meu cànon al 'Kabroncín' cremant discos...
Vaig començar a provar amb el CD 7.4. He provat la 10.10 i la 10.4.
Sempre surt el menú, peró es penja si intento qualsavol cosa, tant installant com arrancar de CD.
He cremat CD's i ho he carregat a Flash (tema d'economia)

Algú s'apiada?

---

### Post by wgarcia on 2011-01-08
Pots preparar una memòria USB amb l'última versió, i iniciar l'ordinador des de la memòria USB (per això tot bon punt iniciat l'ordinador mira d'entrar al menú de configuració BIOS, en molts ordinadors és amb la tecla F2 però el teu sistema t'ho indicarà i mira si a "boot order" està primer la memòria USB que el disc dur. També es pot fer cremant un CD amb l'última versió d'Ubuntu i iniciant des del CD (si no s'inicia automàticament també s'hauria de comprovar si a l'ordre d'arrencada està primer el CD que el disc dur). 

Un cop iniciat escull "provar Ubuntu" i el sistema hauria d'arrencar i es podrà veure si reconeix la teva targeta gràfica, si tens so, si tens xarxa, etc. Si tot va bé es pot escollir instal·lar i el menú es força auto-explicatiu, si vols conservar un altre sistema operatiu escull instal·lar a banda dels sistema operatiu, no escullis en aquest cas "utilitzar tot el disc". 

Les versions recents perquè funcionin des del principi en català les pots descarregar de:

[http://www.ubuntu.cat/node/341](http://www.ubuntu.cat/node/341)

El lloc oficial recomana instal·lar la versió de 32 bits però la versió de 64 bits ja funciona perfectament si vols aprofitar al màxim la potència del teu processador. 

En aquesta pàgina:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

a la secció 2 t'explica com crear una memòria USB d'arrencada o un CD d'arrencada segons el que prefereixis.

---

### Post by JOPECO on 2011-01-08
> **wgarcia said:**
> Pots preparar una memòria USB amb l'última versió, i iniciar l'ordinador des de la memòria USB (per això tot bon punt iniciat l'ordinador mira d'entrar al menú de configuració BIOS, en molts ordinadors és amb la tecla F2 però el teu sistema t'ho indicarà i mira si a "boot order" està primer la memòria USB que el disc dur. També es pot fer cremant un CD amb l'última versió d'Ubuntu i iniciant des del CD (si no s'inicia automàticament també s'hauria de comprovar si a l'ordre d'arrencada està primer el CD que el disc dur). 

Un cop iniciat escull "provar Ubuntu" i el sistema hauria d'arrencar i es podrà veure si reconeix la teva targeta gràfica, si tens so, si tens xarxa, etc. Si tot va bé es pot escollir instal·lar i el menú es força auto-explicatiu, si vols conservar un altre sistema operatiu escull instal·lar a banda dels sistema operatiu, no escullis en aquest cas "utilitzar tot el disc". 

Les versions recents perquè funcionin des del principi en català les pots descarregar de:

[http://www.ubuntu.cat/node/341](http://www.ubuntu.cat/node/341)

El lloc oficial recomana instal·lar la versió de 32 bits però la versió de 64 bits ja funciona perfectament si vols aprofitar al màxim la potència del teu processador. 

En aquesta pàgina:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

a la secció 2 t'explica com crear una memòria USB d'arrencada o un CD d'arrencada segons el que prefereixis.
Gracies per la ràpida resposta !

Tot el que m'indiques, ja ho he provat. 
He arrancat des de CD (el 7.04 és original) i surt el menú.
He provat d'installar el demo i a fer el procés per a arrancar des del CD i quan reinicio, en els dos casos, es queda penjat amb la pantalla en negre i, en el millor dels casos amb unes ratlletes horitzontals a tota la pantalla, peró res més.
Suposo que no reconeix la targeta gràfica.
Per aquest motiu, també he provat la versió alternate (10.4). Aquesta ni arrenca.

---

### Post by wgarcia on 2011-01-08
La versió 7.04 és molt antiga, de l'any 2007 mes 4 (això vol dir 7.04), estem per la 10.10 (any 2010 mes 10). Prova amb aquesta perquè potser el suport per a la targeta gràfica no estigués solucionat amb aquesta versió tan antiga.

---

### Post by JOPECO on 2011-01-08
> **wgarcia said:**
> La versió 7.04 és molt antiga, de l'any 2007 mes 4 (això vol dir 7.04), estem per la 10.10 (any 2010 mes 10). Prova amb aquesta perquè potser el suport per a la targeta gràfica no estigués solucionat amb aquesta versió tan antiga.
Ara acabo de provar la 10.10 tal i com m'indicaves.
L'he gravada en una memória dins d'un lector USB.

Arrancant l'ordinador des de la memória, es penja. Pantalla fosca i el prompt parpadejant a dalt.

Arrancant des del Win (XP) amb el WUBI:
-Surt el menú (Win / Xubuntu) Clico Esc. per a més opcions.
-Ting el menú GNU/GRUB
Clico a NORMAL ---> Es penja (Pantalla fosca i prompt.
Clico SAFE GRAFIC MODE ---> Pantalla amb dades que van camviant aleatóriament (sobreescriu) i es penja.
Clico ACPI WORKAROUNDS ---> Pantalla amb dades (ordenades) i acaba amb una línia on, després d'uns números posa BOOT VIDEO DEVICE.
Clico VERBOSE MODE ---> Igual que abans.
Clico DEMO MODE ---> Em respon com a la primera opció (NORMAL)

---

### Post by JOPECO on 2011-01-08
> **JOPECO said:**
> Ara acabo de provar la 10.10 tal i com m'indicaves.
L'he gravada en una memória dins d'un lector USB.

Arrancant l'ordinador des de la memória, es penja. Pantalla fosca i el prompt parpadejant a dalt.

Arrancant des del Win (XP) amb el WUBI:
-Surt el menú (Win / Xubuntu) Clico Esc. per a més opcions.
-Ting el menú GNU/GRUB
Clico a NORMAL ---> Es penja (Pantalla fosca i prompt.
Clico SAFE GRAFIC MODE ---> Pantalla amb dades que van camviant aleatóriament (sobreescriu) i es penja.
Clico ACPI WORKAROUNDS ---> Pantalla amb dades (ordenades) i acaba amb una línia on, després d'uns números posa BOOT VIDEO DEVICE.
Clico VERBOSE MODE ---> Igual que abans.
Clico DEMO MODE ---> Em respon com a la primera opció (NORMAL)
Em descuidava.
La versió gravada, que he provat, es la XUBUNTU 10.10 a 64 bits.

---

### Post by wgarcia on 2011-01-09
Veig dues possibilitats:

1) Esperar-te a una reunió d'instal·lació, on acabaràs amb un sistema instal·lat i funcionant de segur (hi ha una molt possiblement al febrer que s'anunciarà oportunament, i de segur hi ha haurà una quan surti la versió 11.04, tot i que aquesta pot ser en qualsevol lloc on es parli català). 

2) Provar amb una imatge "alternate":

[http://cdimage.ubuntu.com/xubuntu/releases/10.10/release/xubuntu-10.10-alternate-amd64.iso](http://cdimage.ubuntu.com/xubuntu/releases/10.10/release/xubuntu-10.10-alternate-amd64.iso)

per exemple, que és igual a les altres imatges però tota la instal·lació la fa amb una interfície de text i no gràfica i per tant si el que està impedint la teva instal·lació és la interfície gràfica, això ho solucionaria. 

Una altra possibilitat és usar la imatge de 32 bits, que encara és la recomanada "oficialment" per Ubuntu, per si de un cas fos aquest el problema.

---

### Post by JOPECO on 2011-01-09
Vagi per endavant la meva gratitud per l'ajuda!

He fet proves i arrenco des del disc dur.
-Si no clico res al triar XUBUNTU, es penja amb la pantalla negra. Peró si, mentre fa el compte, clico Escape, surt el menú GNU GRUB.
-Amb les opcions del menú faig el mateix d'abans.

-Si des d'aquí clico 'e' ting el quadre d'instruccions (no hi enteng ni papa)
-Ara clico Contr + x i veig 'BOOTING A COMMAND LIST', el Prompt i es penja.
Si clico Cont + c (en lloc de x) m'escriu 'GRUB>'
-Clico Escape i torno a GNU GRUB
-Ara clico 'c' i obting pantalla fosca i 'GRUB>'

Només falta saber qué escriure al bloc d'ordres...

---

### Post by wgarcia on 2011-01-10
Les instruccions per arribar a una línia on pots entrar comandes les pots seguir d'aquest altre comentari:

[http://ubuntuforums.org/showthread.php?t=1654383&page=3](http://ubuntuforums.org/showthread.php?t=1654383&page=3)

Si pots arribar a una línia d'ordres com diu el comentari, entra com diu el comentari:


sudo dpkg-reconfigure xserver-xorg

i després prova

sudo service xdm start

Si no arriba aquí fixa't en els missatges d'error que mostri just abans de quedar-se penjar i mostra'ls aquí a veure si algú pot esbrinar més.

---

### Post by JOPECO on 2011-01-11
> **wgarcia said:**
> Les instruccions per arribar a una línia on pots entrar comandes les pots seguir d'aquest altre comentari:

[http://ubuntuforums.org/showthread.php?t=1654383&page=3](http://ubuntuforums.org/showthread.php?t=1654383&page=3)

Si pots arribar a una línia d'ordres com diu el comentari, entra com diu el comentari:


sudo dpkg-reconfigure xserver-xorg

i després prova

sudo service xdm start

Si no arriba aquí fixa't en els missatges d'error que mostri just abans de quedar-se penjar i mostra'ls aquí a veure si algú pot esbrinar més.
He arribat al quadre on posa el seguent:
linux /ubuntu/install/boot/vmlinuz debian-installer/custom-installati n\
=/ ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/\
xubuntu-10.10-desktop-amd64.iso automatic-ubiquity noprompt quiet splas\
h  boot=casper ro debian-installes/locale=ca-ES.utf-8 console-setup/lay\
outcode=es console-setup/variantcode=--  rootfilags=sincio
initdr /ubuntu/install/boot/initrd.lz

Cambiant, tal com dius a l'altra fil, el "quiet splash" per "single" i arrancant de nou, treu el llistat que acaba amb:
0.329849] net:registered protocol family 2
0.330111] ip route cache hashtable entries:32768 (order:6, 262144 bytes)

... i penjat de nou.

Arrancant des de la flash i fent el que dius en l'altra fil, qualsavol cosa que escrigui em diu error.

Hi ha, per algun lloc, un llistat d'ordres com quan programàvem en DOS o en BASIC?
Suposo que be deu existir (encara que no l'he sabut trobar)


...I ARA, JO ALMENYS, A PENCAR, QUE JA VAIG DE TARD !!!

---

### Post by wgarcia on 2011-01-12
El grub que estàs veient suposo que és encara del sistema sense instal·lar, segons les línies que veus. 

Has provat d'intentar arrencar la versió "alternate" per veure si no es tracta d'un problema del sistema gràfic?

---

### Post by JOPECO on 2011-01-13
Ja ho vaig fer abans i em vaig quedar, mes o menys, igual.

---

### Post by wgarcia on 2011-01-15
Si ni tan sols del CD o imatge "alternatiu" pot arrencar, llavors s'haurà de mirar potser a alguna configuració del BIOS, però sembla una instal·lació no massa fàcil si és la teva primera vegada amb linux. Potser si et pots apropar a alguna festa d'instal·lació es podrà mirar amb calma.

Però igualment verifica que el CD s'hagi gravat bé (penso que també has provat des d'una memòria USB així que això no pot ser).

---

### Post by wgarcia on 2011-01-15
Si ni tan sols del CD o imatge "alternatiu" pot arrencar, llavors s'haurà de mirar potser a alguna configuració del BIOS, però sembla una instal·lació no massa fàcil si és la teva primera vegada amb linux. Potser si et pots apropar a alguna festa d'instal·lació es podrà mirar amb calma.

Però igualment verifica que el CD s'hagi gravat bé (penso que també has provat des d'una memòria USB així que això no pot ser).

---

### Post by JOPECO on 2011-01-16
Des que vaig començar al foro, només he fet servir la targeta per a gravar discos.

He provat totes les combinacions que m'has anat indicant i, en les primeres propostes, ja em vas indicar aquesta possibilitat.

Ara tornaré a provar l'alternatiu tant a 64 c0m a 32. Ja et diré qué passa.

El que no recordo es si sempre he desinstallat, abans, l'UBUNTU que tenia el disc dur. Ara ho provaré d'aquesta manera, desinstallant del tot l'anterior.

---

### Post by wgarcia on 2011-01-16
Que tinguis una instal·lació al disc dur no hauria d'afectar per iniciar tant des de CD o des de memòria USB en mode "Live".

---

### Post by JOPECO on 2011-01-19
He provat diferents versions 'ALTERNATE' (10.10, 10.4, ... ) Amb totes fa el mateix, al reiniciar, simplement ignora la flash i arrenca el Win.

No es problema del Boot de la Bios ja que les vegades que he provat les versions standard, les ha detectades sempre.

---

### Post by JOPECO on 2011-01-19
Arrenco des d'Alternate (10.10) !
Simplement he camviat d'entrada USB.
Ara ting el menú d'arrancada, peró no em deixa ni installar ni arrencar des d'USB.
Si que puc entrar a les altres opcions.

---

### Post by wgarcia on 2011-01-19
Com et deia, a veure si et pots apropar a alguna d'aquestes reunions d'instal·lació, on van participants de l'equip local d'Ubuntu que poden ajudar a fer les instal·lacions rebels:

    * Dissabte 29 de Gener,16.00h Ubuntu Install Party dins les II JORNADES ROBO.TIK
     o Jornades entorn les noves tecnologies, programari lliure, pantalles, oci i educació. SANTA EULÀLIA DE RONÇANA C.C:La Fabrica A càrrec de l'Àrea de tecnologia de l'Institut La Vall del Tenes i l'Equip UBUNTU.CAT. 

Lloc: [http://www.santaeulaliaroncana.cat/default.php?idcanal=3&idcategory=16&idsubcategory=0&iditem=676&bl](http://www.santaeulaliaroncana.cat/default.php?idcanal=3&idcategory=16&idsubcategory=0&iditem=676&bl)

    * Dissabte, 12 de febrer · 10:00,Allibera el teu ordinador, vina a instalar UBUNTU a Caldes de Montbui, CENTRE DEMOCRÀTIC I PROGRESSISTA,Vallès Central C/ Corredosos de Baix s/n, organitza: 
CALDERINS pel PROGRAMARI LLIURE

Lloc: [http://xecat.gencat.cat/equipaments/centre-democratic-i-progressista](http://xecat.gencat.cat/equipaments/centre-democratic-i-progressista)

    * Dijous 17 de febrer. 18.00 h Ubuntu Install Party a la biblioteca de Cardedeu

Lloc: [http://bibliotecacardedeu.blogspot.com/](http://bibliotecacardedeu.blogspot.com/)

    * 26 de febrer de 2011 - Festa d'instal·lació a la redacció de Vilaweb a Barcelona

Adreça: Ferlandina 43, Barcelona

    *  maig de 2011 (dia a determinar)- Festa de publicació de l'Ubuntu 11.04 - Natty Narwhal a Les Borges Blanques a "La Borrassa"

Lloc: [http://www.laborrassa.cat/contacte.html](http://www.laborrassa.cat/contacte.html)

---

### Post by quitus on 2011-01-21
Ep, no estava assabentat d'aquesta de Cardedeu, quina gràcia, teniu més informació, qui la munta, fins quin hora serà. Compteu amb mi, tinc un parell de problemets amb un tablet i la seva tarja gràfica...

salut

---

### Post by wgarcia on 2011-01-22
Totes les munta l'equip local de voluntaris d'Ubuntu, i si la de Cardedeu comença a les 18:00 doncs almenys fins les 20:00 hi haurà gent, tot i que si es tracta d'una instal·lació nova o una actualització si s'arriba massa tard no es podrà començar a fer perquè no donaria temps d'acabar-la.

---

### Post by JOPECO on 2011-01-22
Jo miraré d'escapar-me a alguna de les que anumeres. Per proximitat, crec que serà o la de Caldes o la de Santa Eularia.

Repeteixo les meves gràcies per a l'intent.

---

