---
title: "Sortida d'un procés"
date: 2007-04-04
forum: Catalan Team
---

### Post by CarlesOriol on 2007-04-04
Algú sap com fer si tenim un procés funcionant per redirigir la sortida d'aquest a la consola?

---

### Post by droijals on 2007-04-09
Bona tarda, Carles!

Així de memòria m'agafes ... suposo que seria quelcom semblant a fer servir el '>' per redireccionar la sortida del teu procés directament a consola, tot i que, si no recordo malament la sortida estandar ja és la consola (és a dir, fent simplement 

*>*

o sinò
[I]
1>[/I]

 (que és el mateix) t'hauria de servir, però bé, per si de cas podríes intentar quelcom '*patillero*'

*> $SHELL*

o potser 

*> tty X *

(essent X el número de consola del que parlem)

Si això no et funcionés -personalment no ho tinc molt clar (*)- el que sí que et funcionarà amb molta seguretat és passar el resultat a un arxiu i amb una tuberia llegir-ho per consola (fen-t'ho tot amb una sola línia de comandes)

>  resultat | (i aqui podríes ordenar-ho amb un sort si es tracta de dades, o llegir-ho, o llegir les últimes línies, o filtrar-ho, ... la veritat és que hi han moltíssimes opcions)

Salutacions.

(Editat: perdona, Carles. Rellegint el missatge veig que deies que el procés està funcionant, ... i provant un *ps -p* (amb el PID d'aquest procés)?

---

### Post by CarlesOriol on 2007-04-10
ps -p em mostra poca cosa més que l'id del process.

Al launchpad algú m'havia sugerit de mirar sudo ls -l /proc/<process_nr>/fd/1 per veure la sortida però quan és un pipe no sé com capturar-lo.

---

### Post by droijals on 2007-04-10
Carles, em dones un exemple per que em faci una idea?

---

### Post by CarlesOriol on 2007-04-11
Cap problema. 

Posem un proces llarg que executem en cron o llançat des de el nautilus. Actualització de repositoris / copies de seguretat rsync... etc...

Quan els llences a la consola et van mostrant a la stdio el % realitzat o les accions que estant fent.

Si s'executen en cron/nautilus desconeixes la seva activitat. Tenim un proces funcionant amb el seu ID i volem saber que escriu.

---

### Post by droijals on 2007-04-11
Carles, jo potser el que intentaria seria això:

1.- # tail -f /var/log/syslog

aqui ha d'anar dient cosetes.

2.- fer algun pipeline

$ proces > log.txt

(enviarà com saps tot l'estandard output a un fitxer log.txt, *sempre que es llenci des de consola*)

3.- editar el fitxer de configuració del cron des d'on es llença el procés i on posi

nom_proces posar al seu lloc nom_proces > log.txt

això hauria d'envïar l'estandard output a log.txt

para anar veient com va creixent el log.txt seria qüestió de fer

tail -f /pathonescreaellog.txt/log.txt

des d'una terminal.

son idees, ara bé: como fer-ho amb el nautilus ni idea, noi :D

---

### Post by CarlesOriol on 2007-04-12
Si, però no es tracta sols d'un problema concret que es podria solucionar perfectament amb qualsevol dels metodes que dius. 

Era més un dubte més genèric que creia que potser tindria una solució fàcil com punxar l'id amb una comanda veure que està fent. 

Cercaré informació algun forum de debianites a veure que em diuen i us tindré al cas.

Agraeixo molt el teu interes i les teves respostes.

---

