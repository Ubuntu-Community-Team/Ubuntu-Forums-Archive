---
title: "Sincronitzar Evolution i Palm Treo 650"
date: 2007-03-30
forum: Catalan Team
---

### Post by nachocan on 2007-03-30
Hola a tothom,

Fa una setmana que he adquirit una Palm Treo 650, i encara no he aconseguit que em sincronitzi correctament amb l'Evolution. 

Faig servir Ubuntu 6.10 Edgy Eft, i he untilitzat el gnome-pilot, però no aconsegueixo que em sincronitzi correctament. 

M'explicaré ho he aconseguit una vegada, però a sobre no he vist cap tipus de canvi ni a la Palm ni a l'Evolution. Amb el Gnome-pilot, he activat els pluggins corresponents a l'evolution. 

També he probat de fer-ho amb el J-Pilot i el Kpilot, però tampoc me'n surto. He buscat per totes les pàgines que conec sobre ubuntu i linux, i també al google, però totes les coses que he probat no em surten. Fins i tot he llegit un post en anglès en el que he entés l'ordre que haviem de seguir per connectar la palm, es a dir primer activar la palm i després el J-Pilot i a la inversa, però no ho aconsegueixo :( 

Us explico, a mi m'interessaria sincronitzar-ho tot: (Contactes, notes, calendari, tasques, missatges de correu electrònic, es a dir tot l'evolution), però si només es pot sincronitzar algunes coses doncs que hi farem. 

Pel que he llegit no pretenc fer una cosa impossible, però a mí m'ho sembla, ja que al connectar la palm al port USB, no passa res a l'Ubuntu, no hem dona cap tipus de missatge ni res. 

També he seguit els passos que s'indiquen a la guía Ubuntu, però res em segueix sortint el missatge d'error a la palm. En aquesta guia parlen del tema de redirigir el port USB, al port serie o algo així. Sincerament tot això hem supera una mica.

Bé gràcies per llegir aquest post.

---

### Post by orestesmas on 2007-03-31
No conec massa el tema de sincronitzar Palm, però sé que aquestes tenen la mania de no activar el USB fins que no li dius que sincronitzi.

Per això el Linux no fa res quan endolles el USB. SImplement el dispositiu no es presenta. Només ho fa quan intenta sincronitzar.

Per comprovar-ho, obre un terminal i fes "lsusb" abans i immediatament després d'apretar el botó de sincronitzar de la palm, i veuràs com el dispositiu "t'apareix".

Quant a fer-la servir, t'has d'assegurar que aquest model està suportat pel mòdul del kernel corresponent, que em sona que es diu "visor". Busca pel google a veure si ja l'han afegit.

---

### Post by lluisanunez on 2007-04-08
Hola,
acabo de passar a Ubuntu des de Fedora, i una de les coses que he solucionat ha estat la sync de la Palm amb linux. No ho havia aconseguit mai (la palm és una Sony clié).
Amb System>>Preferences>>PalmOS devices s'ha obert el wizard de configuració i ha funcionat el reconeixement del dispositiu (canviant sèrie per USB).  
M'he instal·lat el Pilot applet al panel de Gnome.
Clicant a l'applet del panel, s'obre un conduit manager. Cal configurar-lo per a totes les funcions (agenda, contactes, avantgo...)
A continuació ja es pot fer Sync amb el botó de la palm
S'han sincronitzat correctament els contactes, les cites i els meus canals avantgo.
:KS :KS :KS

---

