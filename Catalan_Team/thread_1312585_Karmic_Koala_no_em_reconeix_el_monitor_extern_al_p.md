---
title: "Karmic Koala no em reconeix el monitor extern al portàtil"
date: 2009-11-03
forum: Catalan Team
---

### Post by arsenioLupax on 2009-11-03
Hola,

Soc nou en aquest fòrum. Fa ja més de dos anys que estic amb ubuntu però continuo essent bastant analfabet... No tinc massa temps, però de tan en quant (sobretot quan tinc problemes!) en dedico una mica a investigar jo solet.

[FONT=Verdana]Ja he fet la instal·lació del karmic koala (estic amb ubuntu studio) i no em reconeix bé
el monitor gran (de 17') amb el que treballo (treballo també amb un teclat i
mouse extern). Abans reconeixia els dos monitors, jo
escollia el de 17' i llavors en el del portàtil (més petit) tot quedava
enorme i no hi cavien totes les coses que tenia a l'escriptori (és ple
de coses). Bé, doncs ara en principi els reconeix però només puc
treballar en duplicació de pantalles i llavors ho veig al monitor gran
tal com abans quedava al petit: enorme i sense que hi càpiguen tots els
elements de l'escriptori. S'entèn? Uséase que tot es veu molt gran,
carpetes, barra de dalt, barra de baix, etc. I no crec que sigui una
qüestió de l'aparença, la veritat, perquè tot està com abans i no es
veia així. Està treballant com si el monitor de 17' fos de 15' (és el
que em sembla que té el del portàtil).


Quan acabava la instal·lació m'ha dit si volia suprimir un paquet
(mini-aplicació, deia) i he dit que sí perquè al principi de la
instal·lació m'ha avisat de què al final se'm demanaria suprimir alguns
paquets... No sé si té a veure amb això, però des de llavors la cosa ha
anat malament. He volgut que sel·leccionés el monitor de 17' (el que
continua sense fer) i llavors ja no ha tornat la imatge. He hagut
d'apagar i després de diferents intents, quan em demana l'usuari i
password, a baix em donava la opció d'obrir amb "gnome a prova
d'errors" i així ho he fet. Llavors he aconseguit veure alguna cosa al
monitor gran, fins aquell moment només si el desconnectava podia
treballar al portàtil. En aquells moments, en iniciar em deia que hi
havia algun error o algun paquet que no es podia llegir o una cosa
així, ara mateix no sé si tornarà a dir-ho...

El portàtil és un lenovo 3000 C200, el monitor extern un BENQ T720 17"

Se us acudeix alguna cosa?

Gràcies,

aL
[/FONT]

---

### Post by sordoman on 2009-11-04
Hola ArsenioLupax.

Jo sóc del nous amb ubuntu, pero el jo faria es fer servir l'xrandr

l'executes en un terminal pots posar

```


xrandr --addmode VGA-0 1024x768
xrandr --output VGA-0 --mode 1024x768


```on VGA-0 has de buscar la sortida correcte del teu pc y la resolució 1024x768 la ke et convingui posant xrandr et sortiran totes les pantalles i les resolucions posibles de cada una.

Vaig llegir ja fa temps ke depenent de la tarjeta gràfica no pots tenir dos resolucions diferents de tal manera ke ahures de desactivar la pantalla de portàtil , per si les mosques ahuries de fer-te una adraçera de teclat per tornar a activar la pantalla del portàtil en cas de necesitat.

per desconecta la pantalla del poràtil
```

xrandr --output LDVS --off

```espero ke et serveixi, ves amb compte ke jo soc nou amb el tema!!!:D

---

### Post by arsenioLupax on 2009-11-04
Doncs he fet el que m'has dit, el primer comando, i em diu...:

xrandr: cannot find output "VGA-0"

Posant xrandr surt el següent:

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0 +   75.0  
   1152x864       75.0  
   1024x768       75.1*    70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
   640x350        70.1  
LVDS1 connected (normal left inverted right x axis y axis)
   1024x768       60.0 +
   800x600        60.3  
   640x480        59.9  
TV1 disconnected (normal left inverted right x axis y axis)

Què hauria de fer? Mmmmm... em sento analfabet.

Gràcies anyway!

---

### Post by sordoman on 2009-11-04
Hola arsenioLupax!! som-hi :popcorn:

Primer de tot un advertiment : Sóc autodidacta, aixis ke ........ hejem :rolleyes: 

Bé per començar, quant has posat xrandr l'informació ke t'ha tornat es la següent:

Tens el monitor extern conectat amb resolucío 1024x768 amb nom (VGA1) la seva màxima resolució es de 1280x1024
```
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0 +   75.0  
   1152x864       75.0  
   1024x768       75.1*    70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
   640x350        70.1  
```La pantalla de l'ordinador portatil (LVDS1) també conectada amb 1024x768
```
LVDS1 connected (normal left inverted right x axis y axis)
   1024x768       60.0 +
   800x600        60.3  
   640x480        59.9  
```i finalment la sortide de televisió (TV1) ke esta desconectada
```
TV1 disconnected (normal left inverted right x axis y axis)

```a partir d'aqui tenim pantalla externa (VGA1) pantalla portàtil (LVDS1) i finalment sortida de televisió (TV1)

ara per cambiar la resolució del monitor extern (VGA1) ahuriem de fer el següent

```
xrandr --addmode VGA1 1280x1024
xrandr --output VGA1 --mode 1280x1024 
```Peró atenció j'ha te explicat ke es posible ke la tarjeta gràfica no soporti dos resolucions diferents de tal forma ke si no t'ho accepta ahuries de apagar la pantalla del portatil amb l'orde
```
xrandr --output LDVS --off
```de totes formes estaria bé assegurarse de tenir una adraçera de teclat per si pases alguna cosa poder tornar a conectar la pantalla del portatil em sembla ke amb 
```
xrandr --auto
```n'hi ahuria suficient, (aquesta ordre asignarla a una adraçera de tecleat)

Ara bé, si tot això funciona el probelma es ke cada cop ke reiniciis l'orinador et tocara fer el mateix, jo em vaig fer un petit escript per automatiza-ho, l'unica diferencia es ke jo necesitava conetcar la sortida de tv.

se que també es pot posar a l'inici de sessió, però això es un altre tema

Be espero ke funcioni molta sort):P

---

### Post by arsenioLupax on 2009-11-05
Síiiiii!!! Sí senyor sordoman (no tant sordo, eh!). Ha funcionat. La veritat és que vaig pensar-ho, que en comptes de VGA0 havia de posar VGA1, que és el que apareixia fent xrandr, però estava tenint altres problemes amb la nova ubuntu i em feia por liar-la més...

Moooooltes mercès!!!

salut,

aL

---

### Post by sordoman on 2009-11-05
Fantastic!! 

ara et faig jo una pregunta.

Ets suporta dos resolucions diferents? ho has tingut ke apagar la pantalla del portatil?

i , podries dirme quina tarja gràfica tens? 

tot simplement per curiositat

Fins la proprera):P

---

### Post by arsenioLupax on 2009-11-05
En veritat no calia que apagués la pantalla del portàtil. De fet no t'ho he dit, però jo ja feia estona que el tenia apagat, l'he reencés amb el comando que m'has passat, i diria que després d'això he introduït els comandos per introduïr la resolució del monitor que no em reconeixia d'altra manera (és a dir amb la pantalla del portàtil encesa). I sí, ja abans del karmic koala em suportava les dues resolucions, jo sempre tenia les dos pantalles enceses (no se m'havia acudit que podia apagar la del portàtil!)... Bé, en realitat crec que aplica la resolució del monitor extern a la del portàtil si estan totes dues enceses, de manera que al portàtil tot es veu enorme i no hi cap tot el que sí que hi cap al monitor; si desenganxo el monitor, el portàtil, un cop reiniciat, recupera la seva resolució normal (1024x768).

La targeta gràfica, deu ser això, oi?:

Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

salut!

---

### Post by sordoman on 2009-11-05
ey! gracies! fins la pròxima):P

---

