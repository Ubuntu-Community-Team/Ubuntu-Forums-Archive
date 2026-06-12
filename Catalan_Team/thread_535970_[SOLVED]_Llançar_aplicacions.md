---
title: "[SOLVED] Llançar aplicacions"
date: 2007-08-27
forum: Catalan Team
---

### Post by Cocoguagua on 2007-08-27
Salutacions.

M'agradaria saber com puc 'llançar' aplicacions que es troben dins la carpeta '/opt'  amb el menú del gnome. Quan escric la ruta a l'editor del menú no es llancen, però en canvi si faig doble clic a la carpeta on es troben s'executen sense cap problema. La majoria dels programes són .bin o .sh. Algú sap com fer-ho perquè funcioni des del menú de gnome?

Gràcies.

---

### Post by ChAoS.ct on 2007-08-27
Hola Cocoguagua!
Doncs si el que interpreto és correcte, tu poses la ruta completa al llançador del menú oi?

Crec que el problema dels llançadors de gnome és que executen les comandes amb el home com a directori actual. Aquests programes necessiten trobar dades dins de la seva carpeta de opt?

Si és així sempre et pots fer un petit script sh del pal
```
#!/bin/sh
cd /opt/elmeuprograma/
./elmeuprograma.sh
```
Ja diràs si és això o no!
Salut

---

### Post by Cocoguagua on 2007-08-27
Hola ChAoS.ct.

Amb el teu script he aconseguit llançar l'aplicació des de l'escriptori, però a mi m'agradaria fer-ho des del mateix menú (no m'agrada tenir icones a l'escriptori). Es estrany perquè algunes aplicacions no em funcionen i d'altres si. 

Aquí pots veure l'enllaç (que no funciona) el menú del gnome.
[[IMG]http://img208.imageshack.us/img208/868/captura1hi6.th.png[/IMG]](http://img208.imageshack.us/my.php?image=captura1hi6.png)

---

### Post by papapep on 2007-08-27
Ja has repassat que tinguis els permisos necessaris per a executar l'script i els fitxers que aquest crida?

Apart, jo provaria a posar a ordre:

```
/opt/AssaultCube/**./**assaultcube.sh
```

Fixa't que hi ha un punt i una barra de més.

---

### Post by Cocoguagua on 2007-08-27
Doncs tampoc ha funcionat. He canviat els permisos de la carpeta, tot i que per altres aplicacions no tenia problemes, però tot segueix igual i les aplicacions no es llancen des del menú.

---

### Post by patrickfromspain on 2007-08-27
sh /opt/bla/bla.sh?

---

### Post by ChAoS.ct on 2007-08-27
> **Cocoguagua said:**
> 
Amb el teu script he aconseguit llançar l'aplicació des de l'escriptori, però a mi m'agradaria fer-ho des del mateix menú ]

Jo juraria que la forma hauria de ser lo mateix:confused:
jo faig servir també un programari xungo k el tinc posat a opt, vaig crear un fitxer llançador "executa.sh" amb el script d'avans. despres vaig crear una entrada al menúexecutant aquest escript i em va funcionar.

Quan intentes executar a través del menú es queixa o simpleent no s'engega?
Salut!

---

### Post by lluisanunez on 2007-08-27
Tens /opt/el_que_sigui al teu path?
```
gksudo gedit /etc/environment 
```

---

### Post by Cocoguagua on 2007-08-27
Problema resolt. :)

Com has dit ChAoS.ct he creat script, l'he deixat a la carpeta del programa i ja l'he pogut llançar des del menú.

Moltes gràcies.

---

