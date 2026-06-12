---
title: "diccionaris"
date: 2010-05-28
forum: Catalan Team
---

### Post by tacubuntuforums on 2010-05-28
La veritat es que jo trobo bastant enredat i confús tot lo dels diccionaris, ja no diguem lo dels locales.
A sobre, ara, he descobert que dels diccionaris que tinc a:

/usr/share/dict/

tots estan perfectes excepte, quan no?, els de castellà i català. Tenen una barbaritat de paraules duplicades i no estan ben ordenades alfabèticament.

No sé com ha passat això i perdoneu si es un cas excepcional. En aquest moment estic mirant'ho en un pc amb Hardy que el va fer servir un altre persona (lingüista) uns anys, però els diccionaris mostren dates de modificació molt velles, del dia de la instal·lació mes o menys. De tota manera crec que n'hi hauria d'haver algun sistema de que el diccionaris estiguin nets i ordenats.

Mireu uns pocs exemples:

```

$ cat /usr/share/dict/american-english|wc -l
98569
$ cat /usr/share/dict/american-english|sort|uniq|wc -l
98569

$ cat /usr/share/dict/british-english|wc -l
98326
$ cat /usr/share/dict/british-english|sort|uniq|wc -l
98326

$ cat /usr/share/dict/spanish|wc -l
86016
$ cat /usr/share/dict/spanish|uniq|wc -l
86001
$ cat /usr/share/dict/spanish|sort|uniq|wc -l
85739

$ cat /usr/share/dict/catala|wc -l
[COLOR="Red"]704992[/COLOR]
$ cat /usr/share/dict/catala|uniq|wc -l
684978
$ cat /usr/share/dict/catala|sort|uniq|wc -l
576896


```

---

### Post by kimet on 2010-05-28
No serà la codificació de caracters mal configurada el que et fa que et surtin aquests resultats?

Salut.

---

### Post by tacubuntuforums on 2010-05-28
> **kimet said:**
> No serà la codificació de caracters mal configurada el que et fa que et surtin aquests resultats?

Salut.

No &#347;e què vols dir?
N'hi-han configuracions per tot arreu.
Com s'han ficat paraules repetides en els diccionaris? Al llarg de l'ús per part de l'usuari? ... Però si aquests diccionaris tenen dates de modificaciò molt velles.


```

$dir /usr/share/dict/
.....
-rw-r--r-- 1 root root  931467 2007-10-24 17:12 american-english
-rw-r--r-- 1 root root  929603 2007-10-24 17:12 british-english
-rw-r--r-- 1 root root 7688071 2006-05-18 02:39 catala
lrwxrwxrwx 1 root root       6 2007-12-17 16:14 catalan -> catala
-rw-r--r-- 1 root root     199 2008-04-21 10:04 README.select-wordlist
-rw-r--r-- 1 root root  834839 2006-06-19 14:05 spanish

```

No sé com trobar rapidament la data d'instal.lació però comparat amb:
```
$ dir /bin/ls /bin/more /usr/bin/less
-rwxr-xr-x 1 root root  92376 2008-04-04 08:42 /bin/ls
-rwxr-xr-x 1 root root  27752 2008-09-26 14:43 /bin/more
-rwxr-xr-x 1 root root 120884 2008-02-02 04:51 /usr/bin/less

```

Sembla que els diccionaris no els haigi tocat ningú.

---

### Post by kimet on 2010-05-28
Volia dir que si no tens els locals configurats a utf-8 al sistema, podria ser que tinguessis un error amb els accents al llistar les paraules o al trobar-ne de repetides. Es només una suposició.
En consola:
```
locale charmap 
```

---

### Post by tacubuntuforums on 2010-05-28
Exemple:
```

**$ grep "^arbr" /usr/share/dict/catala**
....
[COLOR="Blue"]arbr[/COLOR]
arbres
arbraries
arbrares
arbresses
arbraves
arbris
[COLOR="Olive"]arbrassis
arbressis[/COLOR]
[COLOR="Blue"]arbr[/COLOR]
arbrar
[COLOR="Blue"]arbr[/COLOR]
.....

```

Aixó es normal? Com pot arribar a passar?

---

### Post by kimet on 2010-05-28
Ni idea, no ho havia vist mai, ni havia vist mai un arxiu que no estigues en ordre alfabètic...

---

### Post by tacubuntuforums on 2010-05-28
> **kimet said:**
> Volia dir que si no tens els locals configurats a utf-8 al sistema, podria ser que tinguessis un error amb els accents al llistar les paraules o al trobar-ne de repetides. Es només una suposició.
En consola:
```
locale charmap 
```

$ locale charmap
UTF-8

Perdona però no entenc què vol dir "un error amb els accents"

Em donarà els mateixos resultats si en aquest moment canvio la codificaciò de caràcters del sistema, no?
Potser vols dir que si uns caràcters es van guardar amb una codificació i uns altres amb una altre, poden quedar dos formes internes per la mateixa paraula.

---

### Post by tacubuntuforums on 2010-05-28
Buneo... sembla que si hi-ha brosa. Però com es va ficar?
Mira:

```

**$ for i in $(grep "^arbr" /usr/share/dict/catala); do echo $i|od -c ;done**
......
0000000   [COLOR="Blue"]a   r   b   r  \n[/COLOR]
0000005
0000000   a   r   b   r   e   s  \n
0000007
0000000   a   r   b   r   a   r   i   e   s  \n
0000012
0000000   a   r   b   r   a   r   e   s  \n
0000011
0000000   a   r   b   r   e   s   s   e   s  \n
0000012
0000000   a   r   b   r   a   v   e   s  \n
0000011
0000000   a   r   b   r   i   s  \n
0000007
0000000   [COLOR="Olive"]a   r   b   r   a   s   s   i   s  \n[/COLOR]
0000012
0000000   [COLOR="Olive"]a   r   b   r   e   s   s   i   s  \n[/COLOR]
0000012
0000000   a   r   b   r 340   s  \n
0000007
0000000   a   r   b   r   a   r 340   s  \n
0000011
0000000   a   r   b   r 351   s  \n


0000007
0000000   a   r   b   r   a   u  \n
0000007
0000000   a   r   b   r   e   u  \n
0000007
0000000   a   r   b   r   a   r   e   u  \n
0000011
0000000   a   r   b   r 340   r   e   u  \n
0000011
0000000   a   r   b   r 351   s   s   e   u  \n
0000012
0000000   a   r   b   r 340   v   e   u  \n
0000011
0000000   a   r   b   r   a   r 355   e   u  \n
0000012
0000000   a   r   b   r 340   s   s   i   u  \n
0000012
0000000   a   r   b   r 351   s   s   i   u  \n
0000012
0000000   a   r   b   r 340  \n
0000006
0000000   a   r   b   r   a   r 340  \n
0000010
0000000   a   r   b   r   a   r 351  \n
0000010
0000000   a   r   b   r 355  \n
.....

```

---

### Post by kimet on 2010-05-28
Volia dir que al no reconèixer els accents, aquests son substituïts per caracters especials i que podia ser que alteressin l'ordre alfabétic. Però si tens el sistema configurat a UTF-8 el problema no es aquest...
Pots provar:
```
#dpkg-reconfigure locales
``` i triar els locals.
O reinstal.lar els paquets d'idioma d'OpenOffice (no se si hi te res a veure).

---

### Post by tacubuntuforums on 2010-05-28
Algunes paraules no surten per pantalla de forma sencera.Segurament per algún caràcter intern que ho provoca.

```
**$ grep -n "^melo[cd]" /usr/share/dict/spanish** 
56855:melocot
56856:melocotonar
56857:melocotonero
56858:melod
56861:melodiosa
56862:melodiosamente
56863:melodioso
56864:melodrama
56865:melodram&#65533;tica
56866:melodram&#65533;ticamente
56867:melodram&#65533;tico
56868:melodre

**$ for i in $(grep "^melo[cd]" /usr/share/dict/spanish); do echo -n $i|od -c  ;done**
0000000   m   e   l   o   c   o   t 363   n
0000011
0000000   m   e   l   o   c   o   t   o   n   a   r
0000013
0000000   m   e   l   o   c   o   t   o   n   e   r   o
0000014
0000000   m   e   l   o   d 355   a
0000007
0000000   m   e   l   o   d   i   o   s   a
0000011
0000000   m   e   l   o   d   i   o   s   a   m   e   n   t   e
0000016
0000000   m   e   l   o   d   i   o   s   o
0000011
0000000   m   e   l   o   d   r   a   m   a
0000011
0000000   m   e   l   o   d   r   a   m 341   t   i   c   a
0000015
0000000   m   e   l   o   d   r   a   m 341   t   i   c   a   m   e   n
0000020   t   e
0000022
0000000   m   e   l   o   d   r   a   m 341   t   i   c   o
0000015
0000000   m   e   l   o   d   r   e 361   a

```

Però de totes maneres n'hi-ha un munt de paraules repetides.

---

### Post by tacubuntuforums on 2010-05-28
Em sembla que l'oppen-office no te res a veure. Jo crec que aquests diccionaris venen amb els paquets aspell o ispell o spell o què sé jo perque es un lio bastant gran.

No sé si alguna vegada aquest sistema va treballar amb un altre codificació però ho dubto i, com et dic, els arxius dels diccionaris mostren unes dades de modificació molt velles. Pot ser enaquell época si hi-havia aquest lio. No sé si hauria de esborrar i tornar a instal.lar algún paquet.

---

### Post by tacubuntuforums on 2010-05-28
No entenc què fa el *dpkg-reconfigure locales*. Pensava que m'anava a preguntar les meves preferencies. Però ha fotut una llista:

```
**$ sudo dpkg-reconfigure locales**

Generating locales...
  ca_AD.UTF-8... up-to-date
  ca_ES.UTF-8... up-to-date
  ca_ES.UTF-8@valencia... up-to-date
  ca_FR.UTF-8... up-to-date
  ca_IT.UTF-8... up-to-date
[COLOR="Red"]  en_AG.UTF-8... cannot open locale definition file `en_AG': No such file or directory
failed[/COLOR]
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  ..........
  es_VE.UTF-8... done
Generation complete.

```
No sé què ha fet i perquè ha fallat en un.

---

### Post by tacubuntuforums on 2010-05-28
A lo millor aquest tio va agafar diccionari d'altres llocs (com Windoze, que no fa servir utf8 ) i els va ficar. Però sembla estrany que estigui mjig ordenat-mig no. Seria molta casualitat que paraules repetides ocupesin llocs propers a la llista. No?

---

### Post by kimet on 2010-05-29
Veig que a ubuntu dpkg-reconfigure locales funciona de forma diferent a altres ditribucions.

Primer s'han de posar els locals a generar al fitxer: var/lib/locales/supported.d/local i despres fer el dpkg-reconfigure.
Pots provar d'esborrar (previa copia de seguretat) aquests fitxers amb errors i després córrer el dpkg-reconfigure locales a veure si te'ls genera correctament.

---

### Post by tacubuntuforums on 2010-05-30
> **kimet said:**
> Veig que a ubuntu dpkg-reconfigure locales funciona de forma diferent a altres ditribucions.

Primer s'han de posar els locals a generar al fitxer: var/lib/locales/supported.d/local i despres fer el dpkg-reconfigure.
Pots provar d'esborrar (previa copia de seguretat) aquests fitxers amb errors i després córrer el dpkg-reconfigure locales a veure si te'ls genera correctament.

Hola kimet: No sé per què penses que tinc malament els locals.. Jo lo que crec es que aquests diccionaris estan malament quan tels baixes. Hauriem de començar per veure si altre gent els te així.

Per començar, aquests diccionaris no venen de l'office (però ves a saber si l'oofice o quins programes els fan servir. Ja dic que això dels diccionaris es molt confús), venen dels següents paquets:

wbritish, wcatalan, wspanish, wamerican, ...

---

### Post by kimet on 2010-05-31
> Hola kimet: No sé per què penses que tinc malament els locals
No dic que tinguis malament els locals, el que dic es que es possible que la codificació d'aquest diccionaris no coincideixi amb la del sistema. Per això no sembla estar en ordre alfabètic al haver-hi caracters extranys.
Segurament aquests paquets w* que dius, s'intal.len com a dependència al instal.lar el paquet d'idioma corresponent, per qixò et deia d'esborrar-los i reconfigurar els locals.
Tanmateix, si sospites que estan corruptes, només has de reinstalarlos per saber-ho. ( els meus estan correctes).

Salut.

---

### Post by RainCT on 2010-06-01
Prova tornant a insta&#320;lar els paquets **wcatalan** i **wspanish**.

---

