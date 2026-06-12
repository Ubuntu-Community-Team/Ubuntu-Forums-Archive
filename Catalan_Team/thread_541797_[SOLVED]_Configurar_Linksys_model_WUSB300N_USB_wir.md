---
title: "[SOLVED] Configurar Linksys model WUSB300N USB wireless"
date: 2007-09-03
forum: Catalan Team
---

### Post by pep70 on 2007-09-03
Bones, soc un nou aterrat a Ubuntu, m'he comprat una targeta wireless usb.
Dons resulta que ubuntu no la veu mentres al Xp no tinc problema previa instalació de drivers.

La tarja es de l'empresa Linksys model WUSB300N

m'han pasat aquesta adreça:

[http://ubuntuforums.org/showthread.php?p=3268995](http://ubuntuforums.org/showthread.php?p=3268995)

tins els drivers però no se que fer amb ells ni com instalar-los, he entrat a la consola o terminal fent un sudo su

ponso el password i
# mkdir /opt/ndis

aixó molt be
però quan poso:

# tar xvf WUSB300N.tar -C /opt/ndis/
em surt
tar: WUSB300N.tar: Cannot open: el fitxer o directori no existeix
tar: error is not recoverable: existing now

i axis em quedo
em podeu ajudar?

gracies

---

### Post by papapep on 2007-09-03
Pep, he creat un nou fil amb el teu enviament per a no barrejar nous i castanyes.

---

### Post by pep70 on 2007-09-03
Gracies papapep, a veure si tenim sort i podem arreglar-ho.

salutacions

---

### Post by papapep on 2007-09-03
> # tar xvf WUSB300N.tar -C /opt/ndis/
em surt
tar: WUSB300N.tar: Cannot open: el fitxer o directori no existeix
tar: error is not recoverable: existing now

Com pots veure et diu que no troba el fitxer WUSB300n.tar que li has ordenat que descomprimís. El més probable és que l'estiguis executant a un directori on NO és el fitxer. I si tu no li dius, ell no el sap trobar :-)

Suposant que el tinguis a /home/usuari li hauries de dir:

```
tar xvf /home/usuari/WUSB300N.tar -C /opt/ndis
```

A veure si així pots adelantar ;-)

Per si et cal, i vols, [aquí]("https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/interpret_comandes")  tens un tutorial de l'intèrpret d'ordres que et pot servir a sortir-te'n millor amb el mateix.

---

### Post by pep70 on 2007-09-04
Merci, ja tinc un pas més, ara el problema està en que no tinc instalat el ndiswrapper.
Me l' he baixat en format .tar i he probat dos coses i cap d'elles em funciona.
$ sudo apt-get install ndiswrapper-utils-1.9
$ sudo aptitude install ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9 

a veure si poc a poc en sortim

gracies

---

### Post by papapep on 2007-09-04
Suposant que fas servir Feisty, els paquets de ndiswrapper que hi ha als repositoris oficials són els següents:

```
Package Search Results

You have searched for packages that names contain ndiswrapper in distribution feisty, all sections, and all architectures.

Found 3 matching packages, displaying packages 1 to 3.
Package ndiswrapper-common

    * feisty (misc): Common scripts required to use the utilities for ndiswrapper
      1.38-1ubuntu1: all

Package ndiswrapper-source

    * feisty (misc): Source for the ndiswrapper linux kernel module [universe]
      1.38-1ubuntu1: all

Package ndiswrapper-utils-1.9

    * feisty (misc): Userspace utilities for the ndiswrapper linux kernel module
      1.38-1ubuntu1: amd64 i386


```

t'ho dic, perquè crec que un dels paquets que intentes instal·lar no hi és.

Apart, quan ens expliques que "cap d'elles em funciona", si no ens poses la resposta del terminal ens perdem la part important de la pel·licula, ja que les teves observacions subjectives (símplement per manca d'experiència) poden ser errònies.

---

### Post by pep70 on 2007-09-04
Ups, tens raó a la nit et dic quin escrit em surt al terminal

fins ara, merci

---

### Post by pep70 on 2007-09-04
El terminal em diu aixó:

**sudo apt-get install ndiswrapper-utils-1.9**
Password:
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències... Fet
E: No s'ha pogut trobar el paquet ndiswrapper-utils-1.9

**sudo aptitude install ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9**
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències... Fet
S'estan inicialitzant els estats dels paquets... Fet
Building tag database... Fet
No s'ha pogut trobar cap paquet amb un nom o descripció que coincideixi amb "ndiswrapper-common"
No s'ha pogut trobar cap paquet amb un nom o descripció que coincideixi amb "ndiswrapper-modules-1.9"
No s'ha pogut trobar cap paquet amb un nom o descripció que coincideixi amb "ndiswrapper-utils-1.9"
No s'instal•larà, actualitzarà o suprimirà cap paquet.
0 paquets actualitzats, 0 instal•lats, 0 a suprimir i 0 a no actualitzar.
Es necessita obtenir 0B d'arxius. Després del desempaquetat s'utilitzaran 0B.
localepurge: checking system for new locale ...
localepurge: processing locale files ...
localepurge: processing man pages ...

No se, com o veus?
el problema es que al no tindre internet no puc actualitzar el gestor de paquets Synaptic (soposo que ajudaria)

gracies per la teva ajuda a veure si ens en sortim

---

### Post by papapep on 2007-09-04
> el problema es que al no tindre internet no puc actualitzar el gestor de paquets Synaptic (soposo que ajudaria)


Home de Deu....haver començat per aquí! :-D

Evidentment, si no tens connexió a internet no podràs instal·lar paquets  (a no ser que ja els tinguis en algun suport d'emmagatzematge local).

Una opció que tens és descarregar-los amb algún altre ordinador de la pàgina packages.ubuntu.com i passar-los a aquest ordinador amb, per exemple, una memòria usb. 

Un cop aquí, i suposant que has posat els paquets a /home/pep70, hauries de fer:

```
cd /home/pep70
sudo dpkg -i ndiswrapper-common ndiswrapper-source ndiswrapper-utils-1.9 
```

i si no tens cap problema de dependències ni res semblant, te'ls hauria d'instal·lar.

---

### Post by pep70 on 2007-09-05
Ahhhhhhhh!!! uf seguim el culebron.

he fet el que em dius i el terminal em diu aixo:

pep@pep-desktop:~$ cd /home/pep
pep@pep-desktop:~$ sudo dpkg -i ndiswrapper-common ndiswrapper-source
ndiswrapper-utils-1.9
dpkg: s'ha produït un error en processar ndiswrapper-common (--install):
no es pot accedir a l'arxiu: El fitxer o directori no existeix
dpkg: s'ha produït un error en processar ndiswrapper-source (--install):
no es pot accedir a l'arxiu: El fitxer o directori no existeix
dpkg: s'ha produït un error en processar ndiswrapper-utils-1.9 (--install):
no es pot accedir a l'arxiu: El fitxer o directori no existeix
S'han trobat errors en processar:
ndiswrapper-common
ndiswrapper-source
ndiswrapper-utils-1.9
pep@pep-desktop:~$

Em vaig vaixar aquests tres paquets:
Package ndiswrapper-common

    * feisty (misc): Common scripts required to use the utilities for ndiswrapper
      1.38-1ubuntu1: all

Package ndiswrapper-source

    * feisty (misc): Source for the ndiswrapper linux kernel module [universe]
      1.38-1ubuntu1: all

Package ndiswrapper-utils-1.9

    * feisty (misc): Userspace utilities for the ndiswrapper linux kernel module
      1.38-1ubuntu1: amd64 i386

i no se que més dir-te, em donaba opció a altres tipos de paquests i per defecte em donava els feisty i son els que vaig escollir.

anem parlant, merci

---

### Post by papapep on 2007-09-05
> pep@pep-desktop:~$ cd /home/pep
pep@pep-desktop:~$ sudo dpkg -i ndiswrapper-common ndiswrapper-source
ndiswrapper-utils-1.9
dpkg: s'ha produït un error en processar ndiswrapper-common (--install):
no es pot accedir a l'arxiu: **El fitxer o directori no existeix**

De sortida et diria que els fitxers dels paquets no els tens a /home/pep que és on executes l'ordre amb el dpkg.

---

### Post by pep70 on 2007-09-05
Els fitxers el tinc a la carpeta pep que ubuntu fabrica automaticament, es aixó la home, uf si no es aixó expliquem que es la home.

gracies i mil gracies, m'estas ajudant molt i també estic aprenent un munt de com mourem per UBuntu (m'està picant i el trobo molt interesant)

---

### Post by papapep on 2007-09-05
És molt fàcil saber si hi son o no:

```
cd /home/pep/
ls -la ndiswrapper*
```

Fent això veuràs una vista detallada del directori que has indicat i sabràs si, efectivament, hi són els paquets o no. :-D

Per a fer una llleugera empenta a les teves energies, fes un cop d'ull a un tutorial prou interessant que em vaig entretenir a traduïr: [http://tinyurl.com/3drv2e](http://tinyurl.com/3drv2e)

---

### Post by pep70 on 2007-09-05
bones, el terminal em diu el següent i pel que entenc si que tinc els arxius, que et sembla?

pep@pep-desktop:~$ cd /home/pep/
pep@pep-desktop:~$ ls -la ndiswrapper*
-rw-r--r-- 1 pep pep 198265 2007-09-03 21:24 ndiswrapper-1.47.tar.gz
-rwx------ 1 pep pep  18000 2007-09-05 00:44 ndiswrapper-common_1.38-1ubuntu1_all.deb
-rwx------ 1 pep pep 155658 2007-09-05 00:43 ndiswrapper-source_1.38-1ubuntu1_all.deb
-rwx------ 1 pep pep  32098 2007-09-05 00:43 ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb

---

### Post by papapep on 2007-09-05
Em sembla molt bé :-D

Ara només cal que quan li dius a **dpkg** que els instal·li li posis els noms correctes (cosa que abans no has fet ;-)):

```
sudo dpkg -i ndiswrapper-common_1.38-1ubuntu1_all.deb ndiswrapper-source_1.38-1ubuntu1_all.deb ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb
```

i veuràs com fa la seva feina.

---

### Post by pep70 on 2007-09-05
Hay Pep no se si en surtirem, el paquet ndiswrapper coomon el tinc be els altres dos em diu que estan trencats al gestor de paquets de synaptic i al dir-li corregeig els paquets trencats l'unica opció que em dona es el·liminarl-os.

al terminal m'ha dit el següent:
pep@pep-desktop:~$ cd /home/pep/ pep@pep-desktop:~$ sudo dpkg -i ndiswrapper-common_1.38-1ubuntu1_all.deb ndiswrapper-source_1.38-1ubuntu1_all.deb ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb S'està seleccionant el paquet ndiswrapper-common prèviament no seleccionat.
(S'està llegint la base de dades ... hi ha 76312 fitxers i directoris instal•lats actualment.)
S'està desempaquetant ndiswrapper-common (de ndiswrapper-common_1.38-1ubuntu1_all.deb) ...
S'està seleccionant el paquet ndiswrapper-source prèviament no seleccionat.
S'està desempaquetant ndiswrapper-source (de ndiswrapper-source_1.38-1ubuntu1_all.deb) ...
S'està seleccionant el paquet ndiswrapper-utils-1.9 prèviament no seleccionat.
S'està desempaquetant ndiswrapper-utils-1.9 (de ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb) ...
S'està configurant ndiswrapper-common (1.38-1ubuntu1) ...
dpkg: problemes de dependències impedeixen la configuració de ndiswrapper-source:
 ndiswrapper-source depèn de module-assistant; tot i així:
  el paquet module-assistant no està instal•lat.
 ndiswrapper-source depèn de debhelper (>= 5.0.37); tot i així:
  Versió de debhelper en el sistema és 5.0.7ubuntu13.
dpkg: s'ha produït un error en processar ndiswrapper-source (--install):
 problemes de dependències - es deixa sense configurar
dpkg: problemes de dependències impedeixen la configuració de ndiswrapper-utils-1.9:
 ndiswrapper-utils-1.9 depèn de libc6 (>= 2.5-0ubuntu1); tot i així:
  Versió de libc6 en el sistema és 2.3.6-0ubuntu20.
dpkg: s'ha produït un error en processar ndiswrapper-utils-1.9 (--install):
 problemes de dependències - es deixa sense configurar
S'han trobat errors en processar:
 ndiswrapper-source
 ndiswrapper-utils-1.9
pep@pep-desktop:~$

---

### Post by papapep on 2007-09-05
No home. no, no t'esveris!! :-D

Si tinguéssis connexió a internet tot això s'hauria resolt automàticament, però com que no és així...doncs portarà un pèl més de feina.

Abans que res, no tens cap possibilitat de connectar, ni que sigui per una estona, aquest ordinador a internet per cable (vull dir que no sigui wifi)?

---

### Post by pep70 on 2007-09-05
tinc una tarja 4g de vodafone, pero soposo q tindria q configurar-la i no se si m'en surtiré. Vodafone dona el sofware de conexió per pc i mac i no per linux.
de totes maneres podria conectarme el fi de setmana a casa del meu germà, amb ell compartim el wifi i dient-li que tinc que conectar-me per cable no tindre problema.
diguem que tinc que fer un cop conectat i a veure si m'en surto.

gracies per la teva paciencia

---

### Post by papapep on 2007-09-05
Doncs bàsicament seria:

primer:

```
sudo aptitude update
```

i seguidament:

```
sudo aptitude install ndiswrapper-common_1.38-1ubuntu1_all ndiswrapper-source_1.38-1ubuntu1_all ndiswrapper-utils-1.9_1.38-1ubuntu1_i386 
```

Quan detecti els problemes de dependències et proposarà instal·lar els fitxers que les arreglen. 
En tot cas, i com a alternativa, és molt probable que aquest cap de setmana fem una trobada del [LoCo]("https://wiki.ubuntu.com/CatalanTeam") i podries acostar-te per arreglar-ho. Encara no sé ni el lloc ni l'hora, però seria una aposta segura ;-)

---

### Post by patrickfromspain on 2007-09-05
el source no el necessites per a res, borra'l i torna a probar.

segon: no estas fent servir feisty i t'has baixat paquets ndiswrapper per feisty. Baixat el common i el utils de la versió d'ubuntu que fagis servir (packages.ubuntu.com).

salut!

---

### Post by papapep on 2007-09-05
Ostres, és veritat patrick, té Dapper!!! No m'havia fixat.

Pep!! Que em portes ben despistat!!!! :-D
Perquè tens Dapper??? Ho has fet volent, o és el CD que tenies a mà??

Aleshores, tens un problema afegit, ja que per a Dapper no hi ha el ndiswrapper-common.

Hi ha algun impediment per actualitzar la versió de Dapper a alguna superior? T'estalviarà molts maldecaps.

---

### Post by patrickfromspain on 2007-09-05
papapep que estem despistats eh? ;)

Si no existeix ndiswraper-common..no es fa servir no? :)

En dapper et caldra nomes l'ndiswrappr-utils: [http://fr.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils_1.8-0ubuntu2_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils_1.8-0ubuntu2_i386.deb)

---

### Post by pep70 on 2007-09-05
Dapper?
jajajaja ara si que m'has mort, no si ni que es, estudio a la uoc i en van pasar als alumnes un cd live de ubuntu i aqui estic amb vosaltres.

que pasa amb el dapper? no va tant be?

que he de fer?

ara semblo el de qui soc, d'on vinc, a on vaig, :guitar:

---

### Post by pep70 on 2007-09-05
pep@pep-desktop:~$ cd /home/pep/
 pep@pep-desktop:~$ sudo dpkg -i ndiswrapper-utils_1.8-0ubuntu2_i386.deb

tot ok ja el tinc instalat, ara a seguir el proces de la tarja, ja us vaig explicant que tal em va la cosa.

nabrassada i gracies als dos

---

### Post by papapep on 2007-09-05
Fes un cop d'ull [aqui]("https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/Versions_Ubuntu") a veure si t'ajuda a aclarir els teus dubtes sobre el tema de les versions d'Ubuntu. ;-)

---

### Post by pep70 on 2007-09-06
Si m'ajuda, tinc la 6.04 i be he seguit amb la configuració del la tarja i un altre problema.

tot aixó okis:
# mkdir /opt/ndis
# tar xvf WUSB300N.tar -C /opt/ndis/
# cd /opt/ndis/Drivers

despres d'aixó em vaig quedar penjat

pep@pep-desktop:/opt/ndis/Drivers$ sudo ndiswrapper -i netmw245.inf
password:
sudo: ndiswrapper: command not found

a veure si tenim sort, per cert com t'he dit tinc la 6.04 de ubuntu quina m'aconselles?

parlem (com els de la caixa \\:D/)

---

### Post by papapep on 2007-09-06
Home, i no sóc de La Caicha..., qualsevol de les que està en verd són vigents fins la data de fi de manteniment. Però si no tens cap necessitat especial el millor que podries fer és instal·lar-te la Feisty (7.04) que és la actual estable no LTS i té els programes més actualitzats. A nivell de control·ladors i demés és la que té més probabilitats de funcionar-te correctament.
Si segueixes amb Dapper no és un problema, però clar, és probable que el maquinari més modern no hi tingui suport (tampoc et puc garantir que a Feisty o Gutsy si el tinguin, clar).

En conclusió després del totxo: si jo fos tu em passaria a Feisty, però fes el que et sembli, ja que és una tria personal. :-D

Respecte que no et trobi l'ndiswrapper, no sé què dir-te. Igual en Patrick té més coneixement de causa...

EDICIÓ: Tenint en consideració que tens Dapper i les instruccions que segueixes són per a Feisty és probable que els passos no siguin els mateixos. He trobat una pàgina on hi ha les instruccions per Breezy i Dapper a veure si et van millor: [http://elcanibal.com/?p=813](http://elcanibal.com/?p=813) (evidentment, canviant convenientment el noms dels paquets)

---

### Post by pep70 on 2007-09-06
Merci Pep, El que faré es això que em dius m’instal•laré la Feisty (7.04) i avanç de fer res connectar-me a internet i actualitzar-ho tot.

De totes maneres, ja t'aniré explicant que tal em va tot i a veure si d'aquesta manera me'n surto.

Gracies per la teva ajuda, potser ara seria un usuari d'Ubuntu decebut i frustrat i en canvi ara es tot el contrari, tinc moltes ganes de aprendre més i coneixe'l be

Per cert tots els links que m'has enviat estan molt be i son força entenedors, els tinc guardats com adreces d’interès.

nabrassada

---

### Post by pep70 on 2007-09-19
Molt bones ja m'he instalat l'ubuntu 7.04 Feisty Fawn i he tornat a començar el proces d'instal·lació del ndiswrapper i m'ha dit aixó el terminal:
pep@pep:~$ sudo dpkg -i ndiswrapper-common_1.38-1ubuntu1_all.deb ndiswrapper-source_1.38-1ubuntu1_all.deb ndiswrapper-utils_1.9_1.38-1ubuntu1_i386.deb

Password:

S'està seleccionant el paquet ndiswrapper-common prèviament no seleccionat.

(S'està llegint la base de dades ... hi ha 88002 fitxers i directoris instal•lats actualment.)

S'està desempaquetant ndiswrapper-common (de ndiswrapper-common_1.38-1ubuntu1_all.deb) ...

S'està seleccionant el paquet ndiswrapper-source prèviament no seleccionat.

S'està desempaquetant ndiswrapper-source (de ndiswrapper-source_1.38-1ubuntu1_all.deb) ...

dpkg: s'ha produït un error en processar ndiswrapper-utils_1.9_1.38-1ubuntu1_i386.deb (--install):

 no es pot accedir a l'arxiu: No such file or directory

S'està configurant ndiswrapper-common (1.38-1ubuntu1) ...

dpkg: problemes de dependències impedeixen la configuració de ndiswrapper-source:

 ndiswrapper-source depèn de module-assistant; tot i així:

  El paquet module-assistant no està instal•lat.

 ndiswrapper-source depèn de debhelper (>= 5.0.37); tot i així:

  El paquet debhelper no està instal•lat.

dpkg: s'ha produït un error en processar ndiswrapper-source (--install):

 problemes de dependències - es deixa sense configurar

S'han trobat errors en processar:

 ndiswrapper-utils_1.9_1.38-1ubuntu1_i386.deb

 ndiswrapper-source

pep@pep:~$ 

EM pensaba que ara tot seria més facil, però be soposo que tindrem q lluitar una miqueta més

Gracies

---

### Post by pespin on 2007-09-19
Sembla que et falta instal·lar certes dependències o bé tens una versió més antiga de la necessària.
```

sudo aptitude install module-assistant debhelper
```

---

### Post by pep70 on 2007-09-19
El terminal m'ha dit aixó, que he de fer per actualitzar-lo?

pep@pep:~$ sudo aptitude install moduel-assistant debhelper

Password:

S'està llegint la llista de paquets... Fet 

S'està construint l'arbre de dependències       

Reading state information... Fet           

Initializing package states... Fet

Building tag database... Fet      

Couldn't find any package whose name or description matched "moduel-assistant"

No candidate version found for debhelper

The following packages are BROKEN:

  ndiswrapper-source 

0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Need to get 0B of archives. After unpacking 0B will be used.

The following packages have unmet dependencies:

  ndiswrapper-source: Depén: module-assistant which is a virtual package.

                      Depén: debhelper (>= 5.0.37) which is a virtual package.

Resolving dependencies...

The following actions will resolve these dependencies:



Remove the following packages:

ndiswrapper-source



Score is -301



Accept this solution? [Y/n/q/?] y

The following packages will be automatically REMOVED:

  ndiswrapper-source 

The following packages will be REMOVED:

  ndiswrapper-source 

0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.

Need to get 0B of archives. After unpacking 209kB will be freed.

Do you want to continue? [Y/n/?] y

Writing extended state information... Fet

(S'està llegint la base de dades ... hi ha 88023 fitxers i directoris instal•lats actualment.)

S'està desinstal•lant ndiswrapper-source ...

pep@pep:~$

---

### Post by pespin on 2007-09-19
> 
Couldn't find any package whose name or description matched "moduel-assistant"
Com pots veure m'he equivocat al escriure jeje. el paquet es "module-assistant", no "moduel-assistant"

---

