---
title: "[SOLVED] Crear arxiu PDF"
date: 2007-11-16
forum: Catalan Team
---

### Post by Curial on 2007-11-16
Déu vos guard a tots,

Sabeu d'alguna aplicació que permeti crear un sol arxiu .pdf de diferents arxius .jpg, .pdf, etc.

:guitar:

---

### Post by lpargemi on 2007-11-16
Una manera, però d'un a un, seria instal.lant una impressora virtual en pdf.

Em volia fer *l'enterat* però resulta que no ho sé fer...

Si vas al Synaptic hi ha una impressora virtual que és un paquet anomenat **cups-pdf**. L'instal.les. 

Com que resulta que a la gestió d'impressores no hi apareix res de nou tot sol, li dius "Instal.lar una impessora nova. S'ho pensa i acaba apareixent la impressora **PDF Printe**r

Li dius seguir, i et demana d'instal.lar un connector. No surt a la llista. Però si pitges instal.lar un connector et demana que li diguis on hi ha el fitxer ppd. Bé, no ho sé on és això... però si torno a obrir el Synaptic, torno a triar el cups-pdf i li pregunto per les propietats, em mostra (a la pestanya no_sé_quina) la llista de fitxers que això ha instal.lat. Hi ha un ppd (en el meu cas a /usr/share/ppd/cups-pdf/ ) El trio, i acaba.

Tot molt bonic, però no va...  Quan vull imprimir no em surt a la llista. Aviciat d'anys de windows paro i engego la màquina... i tampoc.

Sento no poder-t'ho solucionar.

---

### Post by CarlesOriol on 2007-11-17
Des de comanda super-potent:

paquet: imagemagick
programa: convert

En mode gràfic similar a l'acrobat:

gscan2pdf

---

### Post by lluisanunez on 2007-11-17
> **Curial said:**
> Déu vos guard a tots,

Sabeu d'alguna aplicació que permeti crear un sol arxiu .pdf de diferents arxius .jpg, .pdf, etc.

:guitar:

* Scribus és un programa molt potent per a composar i crear PDF , admet importació d'imatges i textos, flux, paginació, etc
* PDFedit és específic per a manipular (tallar, enganxar, editar...) arxius PDF. 
Tots dos són als repos d'Ubuntu. Les solucions anteriors (impressora virtual i Imagemagick, que funcionen, només permeten convertir a PDF  cada document, no els pots annexar.

---

### Post by lluisanunez on 2007-11-17
> **lpargemi said:**
> ...Tot molt bonic, però no va...  Quan vull imprimir no em surt a la llista. Aviciat d'anys de windows paro i engego la màquina... i tampoc.


La impressora virtual funciona molt bé... prova de crear-la des de la interfície web del CUPS:
[http://localhost:631/](http://localhost:631/)
Jo li vaig afegir el driver PostScript-color, i ho fa molt bé.

---

### Post by lpargemi on 2007-11-17
Instal.lant-ho des d'aquí [del port 631] ha funcionat perfectament. 
No tenia ni idea de què la impressora es podia gestionar (i configurar) des d'aqui.
Moltes gràcies

Lluís

---

### Post by pserra on 2007-11-17
##La impressora virtual funciona molt bé... prova de crear-la des de la interfície ##web del CUPS:
##[http://localhost:631/](http://localhost:631/)
##Jo li vaig afegir el driver PostScript-color, i ho fa molt bé.

Per curiositat jo ho he probat, i a mí no em va...des de l'adreça  no connecta...
faig alguna cosa malament?

---

### Post by lluisanunez on 2007-11-17
Prova substituint "localhost" per la teva IP

---

### Post by lo gambusí on 2007-11-17
Sempre pots fer-ho punki: poses los arxius jpg en un document de l'open office i allavontes lo passes a pdf...

---

### Post by papapep on 2007-11-18
Curial: Hi ha un programa en Java que es diu pdfsam que permet juntar diversos pdf's i crear-ne un de sol i també separar-ne un en varis.

[http://www.pdfsam.org/](http://www.pdfsam.org/)

Jo l'he fet servir algun cop i va prou bé.

---

### Post by Curial on 2007-11-18
Caram!!

Gràcies de debó, ara estaré entretingut uns dies amb tot açò que m'heu aconsellat.

---

### Post by elbuit on 2007-11-18
Prova aquest:
gscan2pdf
Al marge de poder crear pdf des del scanner, també pots importar imatges.
La pega és que no pots importar pdf's.

---

### Post by CarlesOriol on 2007-11-18
Eps, no s'hi val repetir ;-)

---

### Post by Curial on 2008-01-03
Encara estic fent provatures amb els vostres consells...,però,

sabríeu dir-me per quin motiu el gscan2pdf no m'obre alguns axius d'imatge?

M'he fixat que els que tenen extensió .jpeg em fallen i no els de .jpg.
No crec que sigui pas pel tamany de l'arxiu.

No són tots dos format jpeg? Tan s'hauria de valer, no?

Gracies.

---

### Post by lluisanunez on 2008-01-03
És així, JPG i JPEG són el mateix format, que utilitza les dues extensions. A mi gscan2pdf me'ls obre indistintament. Mira són molt diferents de mides, crec que això sí que podria ser-ne la causa.

---

### Post by Curial on 2008-01-04
> **lluisanunez said:**
> És així, JPG i JPEG són el mateix format, que utilitza les dues extensions. A mi gscan2pdf me'ls obre indistintament. Mira són molt diferents de mides, crec que això sí que podria ser-ne la causa.

Lluïsa, no és pas pel tamany, això ja ho he comprovat.
També em donen problemes les que he escanerjat amb l'Xsane. 
El més curiós del cas és que quan escanejo amb el programa gscan2pdf va de perles.

(Per cert, vaig provar l'Scribus i no m'agafa els arxius .pdf i els .jpg no apareixen a la llista i tots dos em donen com format no vàlid.) ;)

Salut

---

### Post by lluisanunez on 2008-01-04
Scribus generalment no obre els PDF, sinó els PS (iguals però sense les capçaleres PDF).
Però sí que obre tots els formats d'imatge (adjunto captura)

---

### Post by Curial on 2008-01-05
No ho estava fent bé.

He vist la x dibuixada en la teva fulla (La de la imatge de mostra) i ja he deduït que s'havia d'inserir el "marc d'imatge".
Abans no ho feia i no em donava la opció importa-obtenir imatge.

Gràcies per la paciència.

Salut i bons Reis.

---

### Post by lluisanunez on 2008-01-05
Exàcticament!

Bons reis també per tu!
I noet descuidis de posar el SOLVED

---

