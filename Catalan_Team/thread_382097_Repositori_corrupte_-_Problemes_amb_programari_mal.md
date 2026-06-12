---
title: "Repositori corrupte - Problemes amb programari mal instal.lat - Ajuda!!!"
date: 2007-03-11
forum: Catalan Team
---

### Post by peremayol on 2007-03-11
Fa unes setmanes vaig reinstal.lar-me un PC on tenia XP amb Ubuntu i he quedat molt i molt content i satisfet amb el canvi. Tot he anat de meravella fins que he provat d'instal.lar-me els drivers NDAS...
Ara el repositori se m'ha quedat fomut i em diu que el repositori està malmés i que cal reinstal.lar el paquet ndas-admin.
He provat tots els truc de --force de -remove, he provat de reinstal.lar...
Res!!!
Alguna idea salvadora! Vull que el meu repostori de programari torni a actualitzar-se solet!
Salutacions
Pere

---

### Post by marcoil on 2007-03-11
Per reinstal·lar un paquet has de fer
$ sudo apt-get --reinstall install *paquet*

Moltes vegades per reparar el sistema basta fer un
$ sudo apt-get dist-upgrade

Si provant això no s'arregla, posa'ns per aquí el que et digui l'apt-get, a veure quin és el problema concret.

Sort!

---

### Post by peremayol on 2007-03-11
Pel que fa al primer que em proposaveu

pere@pere-laptop:~$ sudo apt-get --reinstall install paquet
Password:
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
E: El paquet ndas-admin necessita ser reinstal·lat, però no se li pot trobar un arxiu.


El segon dóna un missatge semblant

pere@pere-laptop:~$ sudo apt-get dist-upgrade
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
E: El paquet ndas-admin necessita ser reinstal·lat, però no se li pot trobar un arxiu.


Alguna idea?

---

### Post by orestesmas on 2007-03-11
SI. Prova per aquest ordre:

1) "sudo apt-get -f install"

Si això no rutlla, mira de desinstal·lar per força el paquet ofensiu:

2) "sudo dpkg -r --force-all ndas-admin"

i després de la neteja fes un update i un upgrade. Això t'hauria de tornar a deixar el sistema en un estat estable.

Llavors el consell és que utilitzis l'aptitude per instal·lar el ndas-admin aquest. És una eina de consola però dóna molta informació sobre els conflictes de paquets que es poden produir, abans que es produeixin. Jo no em sabria estar sense.

---

### Post by marcoil on 2007-03-12
Crec que aquest error es pot donar perquè tenies el paquet en un repositori que o ha deixat de funcionar o ja no té el paquet ndas-admin.

Si aconsegueixes destal·lar-ho, fes un *sudo apt-get upgrade* i després possiblement trobaràs que *apt-cache search ndas-admin* ja no te troba el paquet.

---

### Post by peremayol on 2007-03-12
Quan faig un

sudo apt-get -f install

Rebo com resposta

S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
E: El paquet ndas-admin necessita ser reinstal·lat, però no se li pot trobar un arxiu.

Quan faig un
sudo dpkg -r --force-all ndas-admin

Rebo una resposta una mica més clarificadora...

dpkg - avís, no es tindrà en compte el problema per estar activa una opció --force:
 El paquet està en un estat molt dolent e inconsistent - el tindreu que
 reinstal·lar abans d'intentar desinstal·lar-lo.
(S'està llegint la base de dades ... hi ha 136559 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant ndas-admin ...
/etc/init.d/ndas: 14: Syntax error: "(" unexpected
dpkg: s'ha produït un error en processar ndas-admin (--remove):
 el subprocés pre-removal script retornà el codi d'eixida d'error 2
 System startup links for /etc/init.d/ndas already exist.
/etc/init.d/ndas: 14: Syntax error: "(" unexpected
dpkg: s'ha produït un error en netejar:
 el subprocés post-installation script retornà el codi d'eixida d'error 2
S'han trobat errors en processar:
 ndas-admin

Alguna idea de què vol dir aquesta resposta?

---

### Post by CarlesOriol on 2007-03-12
Pot ser per culpa del dash. A mi ja m'ha passat en més d'un paquet.

si vols provar pots fer això :

**AVIS!! Es tracta d'una bojeria i el més segur és que no funcioni i pots trencar-ho tot**

fas :

[B]cd /bin
sudo ln -sf bash sh[/B]

desinstal·les com ho feies i després tornes a l'estat notmal amb:

[B]cd /bin
sudo ln -sf dash sh[/B]

AQUEST DARRER PAS ÉS IMPORTANTISSIM EN QUALSEVOL CAS.

---

### Post by peremayol on 2007-03-12
Moltes Gràcies
Ha Funcionat
M'ha Desaparegut L'error I Ja Se M'han Actualitzat Els Paquets Pendents

---

### Post by CarlesOriol on 2007-03-13
;-)

---

### Post by orestesmas on 2007-03-13
Potser s'hauria de reportar l'error al bugtracking...

---

### Post by CarlesOriol on 2007-03-13
el canvi de bash a dash en la versió edgy ha produit molts d'aquests errors principalment en les comparacions, if major, menor i la gestió d'arrays.

Aquest paquet no està en cap repositori "standard" universe, multiverse, restricted... 

Si creieu convenient haurieu d'avisar al "mantenidor" del repositori des de el que s'ha instal·lat.

---

### Post by simonbcn on 2007-05-21
Yo he tenido el mismo problema.
El problema se produce en la línea siguiente del script de inicio /etc/init.d/ndas :
```
if [ "**${_version_/$s}**" != "${_version_}" ] ; then
```
En bash (la expresión en negrita) se interpreta correctamente, pero en dash no.
Así que los de Ximeta tendrían que cambiar este script para Ubuntu.

Por cierto, si dejo el enlace sh para que apunte permanentemente a bash en lugar de dash, qué problemas me puedo encontrar?

---

### Post by CarlesOriol on 2007-05-21
Bàsicament funciona igual.

El bash és més complet i bastant més pesat (gairebé 10 cops).

-rwxr-xr-x 1 root root 700560 2007-04-11 01:32 /bin/bash
-rwxr-xr-x 1 root root 80500 2007-03-05 07:00 /bin/dash

Però per tal de garantir la compatibilitat amb tot el que es vagi desenvolupant et recomano que mantinguis el dash. Aquells programes que per les causes que siguin no puguin canviar de shell ja ho indicaran a la primera línia amb un #! /bin/bash.

----------------------------------------------------------
[I]
Nota: Estàs en el forum de l'equip d'ubuntaires en català i la llengua oficial és el català. Pots usar l'eina apertium o el web [www.internostrum.com](www.internostrum.com) per ajudar-te a fer les traduccions.[/I]

--------------------------------------------------------

---

### Post by simonbcn on 2007-05-21
Però al ser bash major, això no implica que bash conté dash (en certa manera). Em refereixo que si alguna cosa funciona en dash, per força funcionarà en bash, no? 
Estic provant [http://www.internostrum.com/](http://www.internostrum.com/) i és realment útil. Gràcies.

---

### Post by CarlesOriol on 2007-05-21
Crec que no t'hi trobaras en cap cas que funcioni en dash i no en bash.

Els avantatges d'usar dash son clarament evidents. Gairebé 100 Kb davant de vora 1 Mb. El sistema és més lleuger.

---

### Post by simonbcn on 2007-05-21
Gràcies. He tornat a posar l'enllaç sh a dash. Mentre no corregeixin aquest problema els de Ximeta, hauré de fer els canvis cada vegada que faci actualitzacions.

---

