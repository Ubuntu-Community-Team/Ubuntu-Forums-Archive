---
title: "Afegir icones a l'escriptori gnome-panel"
date: 2012-07-16
forum: Catalan Team
---

### Post by Joan A. on 2012-07-16
Bon dia a tothom,

M'agradaria afegir alguns icones al meu escriptori com la carpeta personal, paperera i equip. Estic utilitzant el famós gnome-panel que ve amb Ubuntu 12.04. Si qualqú té alguna idea de com fer-ho li agrairia.

Gràcies!

---

### Post by akyra on 2012-07-16
Vols dir que estàs utilitzan l'Unity o l'escriptory gnome?

---

### Post by Joan A. on 2012-07-16
Escriptori gnome portat a GTK 3.  És el paquet gnome-panel. Aquest: [http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

---

### Post by akyra on 2012-07-16
Així ni idea, utilitzu Unity.

Adeu

---

### Post by Joan A. on 2012-07-16
I com ho fas a Unity?

---

### Post by wgarcia on 2012-07-16
Jo ho he fet amb el procediment que explico en aquest comentari:

[http://ubuntuforums.org/showpost.php?p=12045625&postcount=4](http://ubuntuforums.org/showpost.php?p=12045625&postcount=4)

---

### Post by Joan A. on 2012-07-16
D'acord, però jo el que vull afegir són l'icone de equip, carpeta personal, paperera i que aparegui a l'escriptori quan connect un dispositiu extern.

---

### Post by wgarcia on 2012-07-17
Has provat Ubuntu Tweak? El pots instal·lar des del centre de programari i permet configurar una sèrie de coses de l'escriptori.

---

### Post by Joan A. on 2012-07-17
Pareix una bona eina, però això és el que em molesta d'Ubuntu les dues o tres darreres versions. Ha perdut molta configurabilitat. Per fer qualsevol cosa que abans podies fer sense instal·lar res, ara has de cercar un programa o aplicació per aconseguir qualsevol tonteria.

---

### Post by wgarcia on 2012-07-17
Home, aquest no és un bon exemple, a l'escriptori per defecte tens totes aquestes eines al llançador lateral, per defecte. Ara bé, tu estàs fent servir un escriptori poc estàndard, que no és ni gnome-shell, ni Unity, ni KDE, ni cap altra escriptori estàndard. Per tant és normal que no estigui tot configurat. 

Per una altra part s'ha d'entendre que hi ha un compromís entre facilitat d'ús i configurabilitat. L'Ubuntu és una distribució que té per objectiu fer un Linux que pugui atraure els usuaris "endollar i jugar", que no s'hagin de preocupar per gaires configuracions. Si s'apliquen o no les estratègies correctes per això és una altra discussió, però aquesta és la idea. Quan hi ha massa possibilitats de configurar coses, a vegades l'usuari es perd. 

Però per sort es tracta de Linux i per aquesta raó sempre poden haver-hi usuaris avançats que introdueixin totes aquestes configuracions, i ens podem acabar saltants totes aquestes simplificacions si no ens agraden.

---

### Post by Joan A. on 2012-07-17
Sí, ja sé que no és un escriptori comú. També és veritat que l'han llençat fa poc, així que és normal que hi hagi errades i *bugs*. A jo el que més m'atrau és que és molt lleuger, per això m'agrada seguir utilitzant el Gnome Classic. Esper que aquest paquet no caigui en l'oblid perquè no hem d'oblidar que és un entorn gràfic que ha donat molt a Ubuntu.

---

### Post by Joan A. on 2012-07-20
Bé, pareix ser que l'única manera de posar les icones que cerc és mitjançant Ubuntu Tweak. L'he estat mirant i no està gens malament, però no és la manera que cercava. Així que donc el tema per sol·lucionat. Gràcies a tots!

---

### Post by AlbertJB on 2012-08-03
Jo també m'he trobat amb aquest problema anteriorment.. Lo curiós del cas és que algunes aplicacions les arrossegues i es crea la icona a l'escriptori, amb d'altres només es crea una fitxer.desktop buit. 

Sempre que en vull crear una, ho faig manualment, per línia de comandes amb:

gnome-desktop-item-edit –create-new ~/Desktop

Substituint Desktop per Escriptori si el tens en català.. És feixuc però funciona.

És una pena que deixin abandonat aquest paquet, esperem que els de Gnome replantegin la seva estratègia, perquè no tothom treballa amb tabletes i mòbils. En fi, no vull encendre un flame, perquè ja n'he parlat amb anterioritat :(
[INDENT]

[/INDENT]

---

