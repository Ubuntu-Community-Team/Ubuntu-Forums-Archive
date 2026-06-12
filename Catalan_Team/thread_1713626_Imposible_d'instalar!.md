---
title: "Imposible d'instalar!"
date: 2011-03-24
forum: Catalan Team
---

### Post by greynell on 2011-03-24
Hola!
Soc un futur (ho això pretenc) usuari de Ubuntu, tenc un Dell Inspiron 1545. El meu problema consisteix en que quan l'hi dono a insatalar no aconsegueixo passar de la finestra a on selecciones el tamany de la partició :S.

No se molt bé que puc fer, he provat de seleccionar a la bios el sistema ATA, que havia llegit que podia ser l'error, però no he aconseguit res.

Ah, estic usant ubuntu 10.10, encara que ja ho vaig intentar amb la versió anterior vaig acabar desistint, encara que ara ho necessito per questions de treball.

Moltes gràcies!

---

### Post by akyra on 2011-03-24
Hola greynell,

Quin fallo et surt?
Ho es simplement que no selecciones cap partició i per això no pots continuar?

Pots posar les particions que tens?

En aquesta pàgina pots trobar una mica més d'informació, però no hauries de tindre gaires problemes per instalar ubuntu.

[http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download")

Ja diràs.

---

### Post by greynell on 2011-03-24
Doncs les particions si que les puc posar, es quan l'hi dono a "Instalar ara" que es queda pensant l'ordinador i no avança. L'he deixat una hora i res.

---

### Post by wgarcia on 2011-03-24
Suposo que estàs instal·lant des d'un "Live CD", oi? Potser seria útil saber com tens ara mateix particionat el disc, i en quina partició vols instal·lar Ubuntu. Has creat una d'especial o ja tenies espai al disc? Has reduït l'espai d'altres sistemes operatius que tens instal·lat o l'estàs dedicant tot el disc?

Una altra pregunta important: Has provat d'arrencar el Live CD sense instal·lar i funciona tot?

---

### Post by greynell on 2011-03-24
En principi pensava usar el sistema de crear particions propi d'Ubuntu, tenc espai de sobra a el disc dur, i es en el moment que ubuntu la crea que deixa d'avançar.
Estic usant un pendrive, i quan cancelo la instelació ja que no avança, puc usar ubuntu de forma normal, wifi inclós. 

El que m'extranya es que pel que he vist amb aquest dell no hauria de tenir problemes... veig que hauré de fer una maquina virtual a windows al final xD

---

### Post by wgarcia on 2011-03-24
Tot i que tinguis espai de sobres si tens altres sistemes operatius has de reduir l'espai de les seves particions, i crear una partició nova a l'espai lliure que es crea. Normalment el programa d'instal·lació et suggereix aquest procediment. 

Ara bé, si tens ja quatre particions primàries el procediment es complica una mica perquè no es poden crear més de quatre particions primàries, llavors s'hauria d'eliminar una de les primàries per crear una partició lògica i aquí crear les particions per a Ubuntu (a una partició lògica es poden crear tantes particions addicionals com es vulgui). 

És recomanable defragmentar l'altra sistema operatiu almenys un parell de cops abans de reduir el seu espai, i sobretot fer còpies de seguretat de tot. 

Si tot et funciona en mode "Live" no hauries de tenir problemes d'instal·lar.

---

### Post by akyra on 2011-03-25
Em sembla que aquest fil l'estem repetint un munt de vegades i sobre tot quan comença una persona nova a Ubuntu.

No sé si hi ha un manual fet o si caldria fer-ne un de nou, amb el cas concret de les particions que ocupen actualment el windows 7, però sembla un problema repetitiu.

---

### Post by wgarcia on 2011-03-25
Per això està el fòrum, si es posa un títol explicatiu i "Solved" quan es troba una solució, a més de fer un petit resum al final explicant com s'ha solucionat (cosa que per una altra part posa en les recomanacions d'ús), ja queda una espècie de manual. 

Quant a manuals, l'amic Miquel Ubuntero manté un en català des de fa unes quantes versions:

[http://ca.wikibooks.org/wiki/Guia_Ubuntu/%C3%8Dndex_10.10](http://ca.wikibooks.org/wiki/Guia_Ubuntu/%C3%8Dndex_10.10)

---

### Post by akyra on 2011-03-25
Sí, ja el coneixo i sembla una feina collonuda.

El problema és que en el nous casos d'ordinadors nous amb windows 7, que ocupen totes les particions primaries i has de fer unes tasques previes abans de poder instal·lar l'ubuntu, i que potser té més que veure amb coneixements d'informàtica que en el propi ubuntu, genera aquests dubtes.

Salutacions.

---

### Post by wgarcia on 2011-03-25
Sí, tens raó, sembla que ho facin a propòsit perquè no et puguis instal·lar cap altre sistema operatiu.

---

### Post by kukat on 2011-03-25
Crec que així és:  Ho fan a propòsit per a que siga més difícil encara instal·lar l'Ubuntu....
Sinó ja em direu qui és l'inútil que no va tindre millor idea que posar una partició del sistema de 100mB a banda...
per a matar-los....

---

### Post by greynell on 2011-03-26
Hola de nou! Hem sap greu haver obert el fil si ja n'existien d'anteriors, pensava a priori que seria culpa del Dell, promet que havia buscat primer pel foro i no n'he trobat cap.
He aconseguit instalar ubuntu, o sigui que moltes gràcies per l'ajuda!
Ara el problema es que no el puc obrir.. al arrancar no hem dona opció de seleccionar-ho i es va directe a Ubuntu.. pero quan he anat a reinstal.lar-lo he vist que Ubuntu ja estava a la partició.
He usat el live-pen drive pero no se molt bé que modificar, ja que si faig això no entra a la versió instalada.

---

### Post by Narcis on 2011-03-26
Hola. Abans de res, l'Ubuntu está instal.lat conjuntament amb un altre S.O.? si es així, això té pinta de  que el grub no s'ha instal.lat correctament, amb la qual només es tindría que tornar a reinstal.lar el grub, i que aixi et dones l'opciò de triar quin sistema operatiu vols. :)

---

### Post by quitus on 2011-03-26
No se si ho he entès bé, però sembla que encara tens el live cd en la lectora. L'has de treure, ja que el sistema sempre arrenca primer desde la lectora de cd.

salut

---

### Post by wgarcia on 2011-03-27
Crec que és important que s'expliqui amb detall els passos que es donen i què es veu, aquest fil ha estat més una tasca detectivesca que una altra cosa. Encara no se sap quins sistemes operatius hi ha, quantes particions, en quina partició s'ha instal·lat l'Ubuntu, etc. 

Aquí al fòrum hi ha gent que fa temps que fa servir l'Ubuntu i ha instal·lat uns quants sistemes amb més o menys encert, però cap telèpata que jo sàpiga.

---

