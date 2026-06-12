---
title: "Sistema d'arxius"
date: 2007-03-16
forum: Catalan Team
---

### Post by Fang5 on 2007-03-16
Hola a totom!

Bé, només volia preguntar que em recomanaríeu, raiserFS o ext3?

Merci!

---

### Post by CarlesOriol on 2007-03-16
Em sembla que el raiserFS està mort des de que el seu autor va ser condemnat per matar la seva dona.

Novell (suse) tinc entès que deixa d'usar-lo

---

### Post by CarlesOriol on 2007-03-16
Em sembla que el raiserFS està mort des de que el seu autor va ser condemnat per matar la seva dona.

Novell (suse) tinc entès que deixa d'usar-lo

---

### Post by jordilin on 2007-03-17
ext3 per descomptat.

---

### Post by Fang5 on 2007-03-17
Osti, que bestia, no?

Bé, em decanto per ext3

---

### Post by jordilin on 2007-03-18
bestia el què?

---

### Post by RainCT on 2007-03-18
Això, no?

> **CarlesOriol said:**
> Em sembla que el raiserFS està mort des de que el seu autor va ser condemnat per matar la seva dona.

---

### Post by sianeu on 2007-03-18
Jo faig servir raiserfs, per que m'han dit que respecta molt més els disc durs, que no pateixen tant per a l'hora de formatejar-los.

Salut

---

### Post by Ferri on 2007-03-19
Teòricament Reiserfs és més ràpid, tot i que la diferència que hi ha dubto que es noti en una màquina moderna. La meva /home la tinc en ext3 i l'arrel en Reiserfs.
De totes maneres, el sistema per defecte que fan servir la majoria de grans distribucions és ext3, excepte SUSE, que sembla que també l'adoptarà, de manera que suposo que es pot dir sense ningú s'enfadi que probablement ext3 és una elecció més segura.

---

### Post by orestesmas on 2007-03-19
S'ha de vigilar amb aquests consells, perquè no sé si tenen massa fonament. D'entrada no sé què vol dir que un disc "pateix" durant el formateig i, encara que fos així, el procés de formatejat té una durada insignificant comparat amb la vida útil del disc, o sia que aquest "patiment" seria negligible.

Jo fa temps vaig fer unes proves per veure la velocitat de transferència de dades en una partició formatejada amb 3 sistemes de fitxers diferents: Ext3, Reiser4 i XFS. Reiser quedava l'últim amb diferència. Això va donar peu a una discussió molt interessant sobre el tema.

Pots trobar el fil en aquest enllaç:
[http://lists.debian.org/debian-user-catalan/2006/02/msg00030.html](http://lists.debian.org/debian-user-catalan/2006/02/msg00030.html)

A veure si en pots treure l'entrellat...

---

### Post by CarlesOriol on 2007-03-20
Orestes:

He llegit el teu post i...

NO estic d'acord en la forma com has realitzat el test.

Crec que treballar en mode sync pot ser un bon sistema per testejar la velocitat d'un disc dur però no per fer-ho a un sistema d'arxius. Ja que no estem controlant el que triguem en escriure un fragment d'informació sinó que volem valorar el rendiment d'un sistema en un us normal, aprofitant les optimitzacions que s'hagin realitzat.

El comput vàlid hauria de ser el total de la transferència (prou llarga per sobrepassar de llarg la cache de memòria + el temps del sync final). 

A... i seguint el fil principal... el patiment dels discs val a dir que és una cosa molt trista. :-) més pateix el llamantol quan el posem a la caçola. he he. (vaja... que ni cas!)

---

### Post by sianeu on 2007-03-20
Sou tremendos  :) . De fet, per a ser precis, el que m'ha dit un profe d'informàtica, es que reiserfs castiga :)  menys el disc dur al ser formatejat (em sap greu no recordar les raons que justificaven l'afirmació, tenia la seva lògica i m'ho vaig creure) . Si es un disbarat, dons perdó, però ja he començat amb un "m'han dit..." que es qualsevol cosa menys un consell, em sembla. 

Una cosa que tenia entesa de llegir-ho pels foros es que si un disc dur es formateja molt (i em refereixo a molt, que ningú pensi en 12 ó 15 vegades sino molt més), dura menys. Aquesta dada em va quedar per que de sempre he tingut un sistema operatiu de "proves" al que toca un formateig cada 2 ó 3 mesos. Ara estic aprenent Linux, i en cinc mesos dec d'haver-ne  instal·lat una vintena (no només ubuntus). Al dir-me allò del reiserfs no m'ho penso, es clar. Però que quedi clar que sempre he formatejat sense cap mirament, si el disc pateix que es foti :) , per que paga la pena.

Salut

---

### Post by CarlesOriol on 2007-03-20
El formateig del disc dur l'afecta cm qualsevol altre escriptura en aquest.

Pot ser que haquesta sigui una mica duradora (si el formateig escriu totes les pistes de nou esborrant el contingut) i que durant aquest temps el disc s'escalfi més que en un ús normal... però no treballarà més que si copiem la mateixa quantitat de dades (películes, repositoris, compilem....)

Com et deia abans, no cal que pateixis per res.

Si et preocupa coneixer l'estat físic del disc ja fa anys que aquests porten implementat un sistema de control anomenat s.m.a.r.t (Self-Monitoring, Analysis and
Reporting Technology System) i hi ha eines per comprovar-ne l'estat (smartmontools)

---

