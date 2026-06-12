---
title: "Ubuntu net cada vegada que inicio PC"
date: 2009-02-10
forum: Catalan Team
---

### Post by camprodon on 2009-02-10
Hola,

Tinc un parell d'ordinadors que estan públics pq la gent els pugui usar. Voldria trobar una manera d'instal·lar ubuntu o derivat de manera que cada vegada que s'inici el PC estigui exactament igual que quan es va instal·lar. Ningu pugui guardar coses al disc dur, ni instal·lar programes ni moure les barres de eines ni les icones de l'escriptori.
Alguna idea de com fer-ho d'una forma senzilla i neta???

---

### Post by papapep on 2009-02-10
Hola Camprodon, benvingut/da.

Pel que comentes, sembla que símplement deixant l'usuari sense permisos ja tinguis la feina feta, no??

Potser seria interessant saber què sí poden fer, per tenir més clar on vols arribar.

Et convido, si no ho has fet ja, a passar pels diferents fils de capçalera i saber una mica més de nosaltres, i nosaltres de tu ;-)

Afegitó: igual l'usuari "Convidat" és el que busques. Jo faria proves amb ell.

Afegitó 2: potser el que busques és el paquet (**no** la distribució) [Sabayon]("http://packages.ubuntu.com/intrepid/sabayon"), que permet definir uns perfils per aplicar-los als usuaris.

---

### Post by camprodon on 2009-02-11
Hola,

des d'on es poden tocar els permisos d'un usuari de forma senzilla? Puc fer de manera que no puguin moure els elements de l'escriptori com barres d'eines i icones de l'escriptori?

---

### Post by Miquel Ubuntero on 2009-02-11
Bones.
Pel tema usuaris i permisos, ho trobaràs a "Sistema - Administració - Usuaris i Grups".

Si vols, també trobaràs més informació a la meva guia ubuntu en pdf que pots baixar-te des de el meu bloc [http://miquel66.caliu.cat](http://miquel66.caliu.cat)
al enllaç "guia ubuntu 8.10 pdf"

Molta sort i benvingut.

---

### Post by papapep on 2009-02-11
En aquesta vida, senzill senzill, poquetes coses.... :-)

T'has mirat alguna cosa del que t'he comentat abans? et cal algun aclariment sobre el meu apunt d'abans??

I no, Miquel, el que ell demana va més enllà que l'edició de permisos d'on indiques. Li cal o treballar via intèrpret d'ordres, o fer servir una eina estil Sabayon.

---

### Post by auska1714 on 2009-02-13
Bones,

si això no et sarveix pots mirar alguna forma de conjelar l'ordinador de tal manera que facin el que facin en tancar l'ordinador queda exactament igual a com l'havies conjelat. Amb el finestres ho havia vist, ara no se si es pot fer amb linux.

Salut!

---

### Post by RainCT on 2009-02-13
> **auska1714 said:**
> si això no et sarveix pots mirar alguna forma de conjelar l'ordinador de tal manera que facin el que facin en tancar l'ordinador queda exactament igual a com l'havies conjelat. Amb el finestres ho havia vist, ara no se si es pot fer amb linux.

I tant que ho és. Bàsicament consisteix en, cada cop que s'engega l'ordinador, esborrar el directori personal de l'usuari i substituir-lo per una còpia de com el tenies abans. Tenia un script per a fer-ho però no sé on el dec haver posat, però de totes maneres buscant una mica no ha de ser gaire difícil trobar informació al respecte...

---

### Post by torracastanyes on 2009-02-13
Fa temps vaig llegir aquest fil que parla del tema. Es per a SUSE, però igual us dona alguna idea:

[http://linkat.xtec.cat/portal/index.php?module=pnForum&func=viewtopic&topic=112](http://linkat.xtec.cat/portal/index.php?module=pnForum&func=viewtopic&topic=112)

---

### Post by RainCT on 2009-02-14
Per cert, acabo de veure que el [Deep Freeze](http://www.faronics.com/html/DFLinux.asp) (de pagament) ara també té versió per a SuSe.

La opció que diu en torracastanyes és més o menys com el que deia que tenia jo... T'hauria de funcionar sense problemes amb l'Ubuntu.

---

### Post by papapep on 2009-02-14
A mi em fa l'efecte que fins que el que ha obert el fil no expliqui una mica més què li cal (si és un cafè internet, si és un pc on només fa un passi de fotos, o de propaganda del que sigui, si és un centre educatiu, etc...) estem fent castells a l'aire.

Ah, per cert!! i el tema de pagar pel DeepFreeze (o qualsevol altre programa, i no ho dic per tu, RainCT) poguent-ho fer de franc i millor, doncs què voleu que us digui....ho trobo bastant innecessari (poseu el vostre adjectiu qualificatiu preferit en lloc de "innecessari", sempre que sigui pejoratiu i lleugerament insultant...:-P)

---

### Post by PatrickVogeli on 2009-02-15
tux on ice té la funcionalitat de restaurar una imatge cada cop que inicies el pc. Seria com si l'hibernessis i cada cop que l'arranquessis, es restauraria la mateixa imatge.

salut

---

### Post by indiosincracia on 2009-02-27
Catix té l'opció de copiar la imatge al disc dur i fer-ho bootable com si es tractes d'un DVD-Live, l'avantatge és que es que s'inicia mès ràpid que un dvd amb la configuració inicial, pots fer-te la teva propia distribució amb remastersys.

el que no queda clar es:
>ni instal·lar programes ni moure les barres de eines ni les icones de l'escriptori.

---

