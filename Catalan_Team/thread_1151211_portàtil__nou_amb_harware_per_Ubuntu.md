---
title: "portàtil  nou amb harware per Ubuntu??"
date: 2009-05-06
forum: Catalan Team
---

### Post by pserra on 2009-05-06
Hola,
tinc un portàtil de 6 anyets que ja demana la jubilació... estic mirant un portàtil de preu no superior a 600€, amb teclat numèric,
pantalleta si pot ser, més gran de 15"...
Que m'aconselleu??
-Avui he estat mirant un HP, però el venedor em diu que li sembla 
que tindre problemes de drivers en aquesta marca.....
- he mirat Asus que diuen que tot ho suporta... però la gama 'baixa' es sense teclat numèric...
També estic mirant un Compaq..un Packard Bell....
Que m'aconselleu companys??
Merci.

---

### Post by SiscoGarcia on 2009-05-06
A part de mirar què tenen a gnuinos, per exemple, has remenat el wiki d'ubuntu relacionat precisament amb la teua pregunta? És [https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

---

### Post by pserra on 2009-05-06
Me

---

### Post by pserra on 2009-05-06
Merci sisco per la resposta...
aquesta pàgina ja l'havia trobat amb sant google pero m'ha semblat 
que potser esta en moltes opinions una mica 'anticuada'...

Mes que rés, vull saber si hi ha alguna marca, o si he de mirar algun 'tipus de harware' en cocret per evitar-me problemes  
més endavant...
Merci

---

### Post by papapep on 2009-05-06
Actualment ja hi ha molts ordinadors amb un maquinari que funciona al 100%, o molt aprop, amb l'Ubuntu.

Un altre recurs és mirar a: [http://www.linux-laptop.net/](http://www.linux-laptop.net/)

La majoria de portatils Dell, Hp, Lenovo/IBM (especialment la sèrie Thinkpad) Compaq, Asus, Toshiba, etc.. funcionen correctament amb les versions modernes de Gnu/Linux.
També hi ha certs "clonics", o de marques ensambladores, com Ahtec i similars, que també tenen considerable èxit en aquest sentit. Un parell d'ubuntaries n'han comprat no fa massa.

Això no vol dir que no puguis tenir problemes amb certes gràfiques o amb algunes plaques de wifi (fes una repassada als fils del fòrum al respecte d'aquests temes i veuràs que s'emporten la palma). El tema rau en que un cop li has posat l'ull a un parell o tres de màquines, miris quina compatibilitat o problemes concrets tenen. Fer-ho a l'inversa (dir quines màquines o plaques van bé) és més complicat, ja que és possible, a la velocitat que va tot aquest tema, que tu no tinguis manera de trobar la mateixa combinació de maquinari que una altra persona tingui.

Una altra opció, si vas a una botiga "Ubuntu friendly", és portar un pendrive USB i provar a veure com es porta amb la versió Live de l'Ubuntu abans de comprar-lo. :)

---

### Post by dafaktor on 2009-05-07
Jo tinc un HP Pavilion DV7 1110es i funciona tot sense cap mena de problema.

La única cosa una mica punyetera és la wifi, que no funciona bé amb el control·lador privatiu i l'a faig anar amb el control·lador *ath5k*. La resta, tot perfecte, inclosa la webcam integrada.

A més, també tinc un Packard Bell de 3 anys i tambe funciona tot semse problemes.

---

### Post by pserra on 2009-05-07
Hola,
Merci pels consells amplis sobre els portàtils.... el portàtil 'vellet' que vull jubilar es un Toshiba i al seu dia gràcies a vosaltres i a l'ajuda del Cubells  ho vaig 'engegar' gairabé tot, l'unic que va ser impossible va ser el mòdem intern i el lector de tarjetes SD que s'han resistit....

---

### Post by pserra on 2009-05-07
Hola,
vull donar el fil per tancat (SOLVED) i a l'opció Thread TOOLs no m'apareix l'opció SOLVED quan ja estic registrat....
Merci

---

### Post by PatrickVogeli on 2009-05-07
jo, de primeres, t'aconsellaria mirar un portatil amb el processador, el chipset, la tarja wifi i la grafica d'Intel. Avui per avui es una combinacio molt ben suportada. L'unic pero es la grafica, que el driver actual i una serie de coses mes tenen algun problema de rendiment (sigui com sigui, jo n'estic satisfet, tinc un intel 965GM, grafica X3100).

L'unic dubte que em plantejaria jo es: quina grafica? Intel, Ati o Nvidia? Sembla que avui dia, cap funciona massa bé, i es que el forum esta plagat de gent amb problemes d'ati, nvidia i intel, aixi que... ati i intel tenen driver lliure, aixo si!

salut

salutacions!

EDITO: opinió personal: apuja el pressupost o espera't... 600&#8364; es molt poqueta cosa trobo.

---

### Post by friviere01 on 2009-05-08
Aquí teniu una relació de []"]comerços que venen ferralla sense ruindou$]("http://pacoriviere.googlepages.com/TornarElUindous.html#[[Compra%20un%20ordinador%20sense%20ruindous):

[]"]http://pacoriviere.googlepages.com/TornarElUindous.html#[[Compra%20un%20ordinador%20sense%20ruindous]]]("http://pacoriviere.googlepages.com/TornarElUindous.html#[[Compra%20un%20ordinador%20sense%20ruindous)

Si trobeu algun enllaç que no estigui actualitzat, digueu-ho!

---

### Post by pserra on 2009-05-28
Hola,
doncs ja he canviat el portàtil, al final m'he comprat un HP (compaq) presario CQ71  que esta dintre els paràmetres anteriorment cercats...
Doncs bé, avui he instal·lat el Ubuntu, al moment de fer les particions he escollit l'opció (crec que es deia paralela) que el mateix programa escull..
Doncs ja l'he provat i gairabé tot va bé( de moment em fallen els altaveus i la impresora)  el wifi l'he provat i va bé...
Un problema que m'ha sortit es el tamany de les particions, al fer-lo automàtic m'ha deixat molt poc esapi a Ubuntu i no em deixa actualizar ja que em surt el missatge de error de falta d'espai.....
Ho he provat des de el GPARTET i em diu que el hda5 s'ha de desmuntar manualment.
adjunto pantalla del gparted...[IMG]http://home/pere/Escriptori/captura.png[/IMG]
la meva uuid es:
lrwxrwxrwx 1 root root 10 2009-05-28 23:16 1326BF044B43F4E8 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-05-29 00:16 59334d10-a89f-4730-a0ae-960ffecdfad7 -> ../../sda6
lrwxrwxrwx 1 root root 10 2009-05-28 23:16 cd226bd7-119f-455f-af2b-599f04a20d79 -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-05-29 00:25 CEF402D5F402C027 -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-05-29 00:43 E0FD-1813 -> ../../sdc1
en aquest cas quines comandes he d'utilitzar?
Vull crear una particio GRAN compartida entre els dos sistemes.... com es 
fa??
merci

---

### Post by oriolsbd on 2009-05-29
Hola, pots provar amb el mateixGparted, però arrancant el PC des d'un LiveCD. Això té l'avantatge que no et munta les particions (o com a mínim, les pots desmuntar sense problemes).

Salut!

---

### Post by pserra on 2009-06-01
Merci oriolsbd,
si que es fàcil fer-ho des de el CD... 
Merci.

---

