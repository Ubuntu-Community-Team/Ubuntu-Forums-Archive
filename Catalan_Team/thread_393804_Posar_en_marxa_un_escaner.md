---
title: "Posar en marxa un escaner"
date: 2007-03-26
forum: Catalan Team
---

### Post by sianeu on 2007-03-26
He connectat el escaner (Epson 2400) y el sistema el detecta (sistema/preferències/hardware information) però no el puc fer servir. 

Probablement em falti el software. A la pàgina de Epson hi ha un controlador que suposo que deu portar el mínim per usar-lo, però no se si el propi ubuntu te un bon software per el cas. Què m'aconselleu?

Salut

---

### Post by CarlesOriol on 2007-03-26
Has provat amb el kooka?

Es bastant immediat i amb l'escanner que dius no has de tenir cap mena de problemes.

---

### Post by sianeu on 2007-03-26
El programa m'agrada, gracies de nou. Però no acaba de funcionar. Al polsar  el botó de *vista prèvia de l'escaneig* va bé y mostra a la dreta l'escaneig; però el botó *finalitzar l'escaneig*, el menú *fitxer/desa la imatge* o els botons i*mprimir, rotar, invertir*.... no funcionen, no fan res.

He mirat l'ajuda *manual de kooka* y em diu que no pot engegar el *Centre d'ajuda KDE*, que *No s'ha pogut trobar el servei khelpcenter*. Es lògic si faig servir gnome. Aleshores potser fora millor fer servir un programa més compatible i amb l'ajuda més a l'abast...... a no ser que el problema sigui del Feisty.

Hi ha algun programa gnome de qualitat semblant?

Salut

---

### Post by CarlesOriol on 2007-03-26
Tens una mena d'estandard de **llibreries** twain anomenat sane per gnome. Crec que a més donen suport a l'openoffice, gimp, etc...

sane i sane-utils

Al fer la instal·lació t'afegeix el programa

xscanimage ( No es gaire maco. Pero funciona. )

---

### Post by CarlesOriol on 2007-03-26
Perdó:

i també instal·la xsane

que està força bé.

---

### Post by sianeu on 2007-03-26
Al final el problema era una cosa de resolució. Al principi estava a 2400 (Epson 2400), però es veu que aixó es massa. Al posar-la a 300 a anat molt be; al provar a 1200 ho ha fet però a patit (:) ) molt, amb uns grinyols aguts que m'han tingut amb mal de ventre fins que el pobre parato ha acabat i ha tardat molt moltissim. 

Está clar que es un problema de conceptes. El meu escaner te una resoluciò de fins a 2400ppp x 4800ppp. A la resoluciò de 1200 dona una imatge de 10200x14031 pixels i 3.2mb (només una mica de text escrit a mà). Això es massa resolució? quina es la equivalència ppp-resolució-pixels?

Salut

PD: Has contestat mentre escrivia. Provaré el que dius, gracies.

---

### Post by CarlesOriol on 2007-03-26
ppp = Punts per polzada en anglès dpi dots per inch)

Tot depén del que vols fer. No és el mateix escanejar tot un dina4 que un logotip ben petitet d'un racó.

300 dpi es molt acceptable per un document per imprimir, 150 per un document per enmagatzemar, 96 o 120 o 75 una mida de pantalla  1 a 1 (depén de la densitat de punts... sempre pots agafar el regle i mirar-ho) i si vols escanejar una mida d'un segell per despres treballar 600 pot ser molt correcte.

1200 és la resolució optica del teu scanner per tant tot el que epson et digui de mes es software... vaja que ni cas.

La gent que treballa professionalment en arts gràfiques també usa resolucions superiors però si no és el cas crec que et portarà més problemes que avantatges el usar més resolució de la que necessitis. 

Per fer ocr amb 150 n'hi ha prou.

El millor es que miris per cada cas que et va millor.

---

### Post by sianeu on 2007-03-26
Moltíssimes gracies, em serveix molt el que has explicat.

Les llibreries libsane i xsane ja les tenia instal·lades. He instal·lat sane i sane-útils i alguna més que no recordo. Amb això s'ha instal·lat *Escaner de imatges Xsane*, que també va molt bé. Ara també el Kooka em reconeix el meu escaner (avans el detectava com a  Epson GT-9300) i crec que va més fi.

Cada programa te el seu qué. El Xsane, per exemple admet reescalar la imatge com si fos un editor de fotos...... els usaré tots dos, ja veurem.

Gracies de nou.

Salut

---

### Post by orestesmas on 2007-03-26
> **sianeu said:**
> El programa m'agrada, gracies de nou. Però no acaba de funcionar. Al polsar  el botó de *vista prèvia de l'escaneig* va bé y mostra a la dreta l'escaneig; però el botó *finalitzar l'escaneig*, el menú *fitxer/desa la imatge* o els botons i*mprimir, rotar, invertir*.... no funcionen, no fan res.

He mirat l'ajuda *manual de kooka* y em diu que no pot engegar el *Centre d'ajuda KDE*, que *No s'ha pogut trobar el servei khelpcenter*. Es lògic si faig servir gnome. Aleshores potser fora millor fer servir un programa més compatible i amb l'ajuda més a l'abast...... a no ser que el problema sigui del Feisty.

Hi ha algun programa gnome de qualitat semblant?

Salut

Hola,

El Carles ja t'ha respost sobradament, jo només afegiré que en el Kooka, després de fer la vista prèvia has d'escollir la regió que vols escanejar (o dir-li mida A4, etc...) i després prémer el botó de "finalitzar l'escaneig", altrament no funciona.

Ara, que pel que dius, ja l'has fet funcionar, o sia que ja ho deus haver descobert tu.

---

