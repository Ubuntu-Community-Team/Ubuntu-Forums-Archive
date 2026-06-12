---
title: "Instal·lar desde dpkg --get-selections"
date: 2009-04-23
forum: Catalan Team
---

### Post by LitusMayol on 2009-04-23
Bona tardaa! (feliç Sant Jordi!)

En un [post de fa temps]("http://ubuntuforums.org/showthread.php?t=888037&highlight=CarlesOriol+actualitzar") en **CarlesOriol** m'ensenyava a usar el:
```
dpkg --get-selections
```

Però ara que el necessito em trobo amb problemes. Ell assegurava que "*després pots recuperar-ho fins i tot amb el synaptic.*". Algú sap com usar aquest *.txt* amb el *Synaptic*?

Mercii.

---

### Post by papapep on 2009-04-23
Fent:

```
man dpkg
```

entre moltes altres coses, surt:

```
--get-selections [package-name-pattern...]
              Get  list of package selections, and write it to stdout. Without
              a pattern, packages marked with state purge will not be shown.

       --set-selections
              Set package selections using file read  from  stdin.  This  file
              should  be in the format &#8217;<package> <state>&#8217;, where state is one
              of install, hold, deinstall or purge. Blank  lines  and  comment
              lines beginning with &#8217;#&#8217; are also permitted.


```

O sigui, que si primer vas fer:

```
sudo dpkg --**g**et-selections **>** nomdelfitxer.txt
```

ara hauries de fer:

```
sudo dpkg --**s**et-selections **<** nomdelfitxer.txt
```

per a importar la llista de paquets a instal·lar. Suposo que un posterior:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

hauria d'acabar de resoldre el tema. No ho he fet personalment, però segur que va per aquí el tema. En tot cas, si expliques una miqueta de res el teu problema, potser podem enfocar-ho millor...

---

### Post by LitusMayol on 2009-04-23
Ep!

Doncs a veure. Vaig a pams (ho sé **papapep**... xD M'hauria d'haver explicat millor!). El tema és que en aquest document *.txt* hi surten tots els paquets que tenia instal·lats abans. I pel que vaig entendre del **CarlesOriol** hi ha alguna manera de instal·lar-los de nou via *Synaptic*. 

Seguint pas a pas la recomanació d'en **papapep**, no ho he solucionat. Cada ordre que li he donat l'ha aplicat (és a dir, que no m'ha donat cap error), però fins hi tot després del "*sudo aptitude update && sudo aptitude safe-upgrade*" no ha passat re.

Alguna idea? 
[COLOR="SlateGray"]
(**papapep**, millor?:P)[/COLOR]

---

### Post by papapep on 2009-04-23
Prova amb:

```
sudo apt-get -u dselect-upgrade

```

---

### Post by LitusMayol on 2009-04-23
Una vegada més: **impressionant**. :popcorn:**Papapep**, magnífic! 

Sembla que ara sí que ha reaccionat:
```
0 actualitzats, 696 nous a instal·lar, 2 a suprimir i 0 no actualitzats.
Es necessita obtenir 1458MB/1462MB d'arxius.
Després d'aquesta operació s'empraran 3386MB d'espai en disc addicional.

```

El deixaré tota la nit treballant i si puc demà mateix poso el *SOLVED*.

Merci de nooouu!

---

### Post by LitusMayol on 2009-04-24
**SOLVED!**

Algu dels administradors pot marcar-lo com a tal? És que no em surt l'eina.
Merci. :)

---

### Post by SiscoGarcia on 2009-04-25
> **LitusMayol said:**
> **SOLVED!**

Algu dels administradors pot marcar-lo com a tal? És que no em surt l'eina.
Merci. :)

Litus, és que fa temps que no hi és... ja es va comentar per aquí. En fi, són "pegues" que ens posen des de la casa mare ;)

---

