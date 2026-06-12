---
title: "[SOLVED] Canviar el nom a diversos fitxers amb rename"
date: 2007-11-17
forum: Catalan Team
---

### Post by lpargemi on 2007-11-17
Hola

Per culpa de l'herència de windows, que tant li fa majúscules com minúscules als noms del fitxers, em veig en la necessitat de canviar l'extensió d'uns fitxers .jpg a .JPG, deixant la resta igual

Ja he vist que la instrucció rename és la que toca.

Fent Info rename t'expliquen que has de posar una instrucció en PERL; però és que jo no en sé de PERL, i per tant m'és difícil de fer servir

Com a exemple posa: **rename 's/\e.bak$//' *.bak** per convertir fitxers a *.bak (suposo), però no sé què representa la s, ni les barres ni la e ni el Dòlar; i a més provant per arreu amb jpg i JPG tampoc no em va

Un altre exemple que hi ha és **rename 'y/A-Z/a-z/' ***, per passar de minúscules a majúscules. Aquí no sé què representa la y, i a més jo no vull canviar la resta de lletres dels noms, només les de l'extensió.

Algú sap quina és la frase màgica correcta?

O on expliquen què volen dir aquestes instruccions PERL... perquè la cosa no vagi de màgia

Lluís

---

### Post by papapep on 2007-11-17
Crec que et serà d'ajut fer un cop d'ull al tutorial de la línia d'ordres:

[https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/interpret_comandes#head-bac155ab4b7d91c8576df1766c0cee9e48363156](https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/interpret_comandes#head-bac155ab4b7d91c8576df1766c0cee9e48363156)

Per cert, la "màgia" de Perl es diu "expressions regulars", i pots trobar una bona introducció aquí: 

[http://bulma.net/body.phtml?nIdNoticia=770](http://bulma.net/body.phtml?nIdNoticia=770)

---

### Post by jerec on 2007-11-17
Aqui tens la pocima magica, fent servir el "ls" o "find", "perl" i "rename"
 
Amb el "ls":
```

# ls *.jpg | perl -ne 'm/((.*)jpg)/;rename$1,"$2JPG"'

```
o tambe amb el "find":
```

# find -name "*.jpg" | perl -ne 'm/((.*)jpg)/;rename$1,"$2JPG"'

```

Això et cambiarà les extensions de la sortida del "ls" o del "find" amb la de la expresio perl combinada amb el rename. Totes els fitxers .jpg, t'els deixarà a .JPG
Per curiositat, perque els necessites amb l'extensio "JPG" amb mayuscules?¿

---

### Post by lpargemi on 2007-11-18
Moltes gràcies als dos, a la part científica i a la màgica.

A la curiositat:

La meva càmera quan guarda les fotos deixa els fitxers amb majúscules. Des de Windows feia anar un paquet del fabricant de la càmera que em generava miniatures (Thumbs o així) i que deixava el nom amb minúscules.

Tinc una debilitat per complicar-me l'existència, així que enlloc de fer servir un dels programes standard per gestionar les fotos, me'n faig un a mida; tirant de php i mysql i Apache (això en Windows també anava). En realitat el què persegueixo és una transversalitat a l'hora de buscar les fotos que ens els programes standard no he sabut trobar. Per altra banda al programari standard no depèn de mi els canvis de versió formats i demés.

Quan vaig tenir el darrer daltabaix amb Windows em vaig passar a Linux, però això no em corria perquè tenia un munt de fotos (més de dues mil, escampades en una pila de directoris) on les miniatures tenien l'acabament diferent del què constava a la meva base de dades.

Amb Linux i una sola línia ha funcionat el canvi de nom, una meravella.

Lluís

---

### Post by lpargemi on 2007-11-19
Això per mi ja està resolt, però no he vist des d'on es posa l'etiqueta [SOLVED].

Ho he de fer jo (que vaig començar a descabdellar el fil), o és cosa dels moderadors?

Agraït

Lluís

---

### Post by papapep on 2007-11-19
Ho pots fer tu.

clica a "Thread tools" al capdamunt del fil, i després marca a "Mark this thread as solved"

---

### Post by lpargemi on 2007-11-19
> **papapep said:**
> Ho pots fer tu.

clica a "Thread tools" al capdamunt del fil, i després marca a "Mark this thread as solved"

Ok, ja ho he fet

Lluís

---

