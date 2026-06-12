---
title: "Menu principal desaparegut! URGENT!!"
date: 2010-12-11
forum: Catalan Team
---

### Post by merril on 2010-12-11
Hola, soc nou a l'ubuntu, ahir em vaig instal·lar l'Ubuntu 10.10 (nomes havia tingut el 8,4 durant 2 setmanes) i em va passar igual que a l'usuari badchecksum en aquest tread:
[http://ubuntuforums.org/showthread.php?t=1543539&highlight=menu+principal](http://ubuntuforums.org/showthread.php?t=1543539&highlight=menu+principal)
Però jo, sense preguntar a ningú, li vaig clickar sobre el nom "corrupte" i al apareixe'm un cartellet que deia: "tancar aquest quadre" li vaig donar i m'ha desaparegut el menú principal (el superior) de l'ubuntu. 
Tampoc sé com cridar un terminal, he provat de crear una llançadora i cridar des d'ella al terminal, però, realment soc un novell i no en tinc ni idea (encara) de com fer-ho...
He provat les combinacions de tecles [ctrl+fn] per fer aparèixer el terminal i no fa res...
Si us plau si algú em pot ajudar ràpidament li donaré ...:popcorn: crispetes!
Gràcies!

---

### Post by quitus on 2010-12-11
En el quadre inferior prem el botó de la dreta del ratolí, "quadre nou" i desprès "afegir al quadre" i pots escollir tots els accessoris que vulguis.

salut

---

### Post by wgarcia on 2010-12-11
Prova entrar ALT-F2, i a la finestra que s'obre entra:

killall gnome-panel

a veure si es reestableix el panell. De totes maneres potser ja l'hagis solucionat perquè si has tancat l'ordinador "a la força" i l'has tornat a obrir el panell s'hauria d'haver reestablert.

---

### Post by merril on 2010-12-11
> **quitus said:**
> En el quadre inferior prem el botó de la dreta del ratolí, "quadre nou" i desprès "afegir al quadre" i pots escollir tots els accessoris que vulguis.

salut

Hola, li he afegit una barra de menus, amb l'opció "menu principal" on em surten totes les opción standard (accesoris, grafics ofimàtica, internet...) però no es ben be això, ja que mola tenir totes les opcions de la barra principal (el correu, el nom d'usuari, els botons ben ordenats... etc...)
Igualment, quitus, aquí tens les crispetes: :popcorn:
Però a veure si algú mes em pot resoldre el problema...
També he provat a apagar l'ordinador i tornar-l a engegar, i res de res, i executant el "killall gnome-panel" amb alt+f2 tampoc...

---

### Post by wgarcia on 2010-12-12
D'acord, no havia entès que havies esborrat totalment el panell superior, simplement havia entès que el tenies "corrupte" encara (mea culpa de no llegir correctament el teu primer post). Aquí va un altre suggeriment. Ara que tens els menús clica a "Aplications -> Accessoris -> Terminal", i a la terminal que s'obre entra les següents instruccions:

gconftool-2 --shutdown

rm -rf ~/.gconf/apps/panel

pkill gnome-panel


Després de cada una d'elles òbviament entra "intro" perquè s'executin. A veure si això et restitueix el teu panell principal.

---

### Post by wgarcia on 2010-12-12
Per cert un altre suggeriment: Posar "URGENT!" al títol viola la regla 5 de les instruccions del fòrum: "El fet de posar paraules com: URGENT, AJUDA, SOCORS, etc... al títol no significa ni més ràpida ni millor resposta, o sigui que eviteu-les."

---

### Post by merril on 2010-12-12
> **wgarcia said:**
> D'acord, no havia entès que havies esborrat totalment el panell superior, simplement havia entès que el tenies "corrupte" encara (mea culpa de no llegir correctament el teu primer post). Aquí va un altre suggeriment. Ara que tens els menús clica a "Aplications -> Accessoris -> Terminal", i a la terminal que s'obre entra les següents instruccions:

gconftool-2 --shutdown

rm -rf ~/.gconf/apps/panel

pkill gnome-panel


Després de cada una d'elles òbviament entra "intro" perquè s'executin. A veure si això et restitueix el teu panell principal.

Oh! Ara si!
Wgracia, :popcorn: :popcorn: doble ració de crispetes!
I pel tema d'urgent, tens raó, però estava desesperat! ;)

---

