---
title: "No se com solucionar aquest problema: No s'ha pogut llegir la llista de les fonts."
date: 2018-05-27
forum: Catalan Team
---

### Post by negu on 2018-05-27
[COLOR=#666666][FONT=&quot]Hola a tots i totes[/FONT][/COLOR]
[COLOR=#666666][FONT=&quot]fa unes setmanes vaig canviar de [/FONT][/COLOR][COLOR=#666666][FONT=&quot]distribució[/FONT][/COLOR][COLOR=#666666][FONT=&quot] d'Ubuntu passant al [/FONT][/COLOR][COLOR=#666666][FONT=&quot]16.04[/FONT][/COLOR][COLOR=#666666][FONT=&quot] i ara estic actualitzant programes que no tenia.... avui estava intentant [/FONT][/COLOR][COLOR=#666666][FONT=&quot]instal·lar[/FONT][/COLOR][COLOR=#666666][FONT=&quot] l'[/FONT][/COLOR][COLOR=#666666][FONT=&quot]Avidemux[/FONT][/COLOR][COLOR=#666666][FONT=&quot] mitjançant la consola i (sense voler) l'he tancat inesperadament.[/FONT][/COLOR]
[COLOR=#666666][FONT=&quot]Davant[/FONT][/COLOR][COLOR=#666666][FONT=&quot] d'això no em permet actualitzar el programari apareixent-me aquest missatge:[/FONT][/COLOR]

[COLOR=#666666][FONT=&quot]E[/FONT][/COLOR][COLOR=#666666][FONT=&quot]:Malformed[/FONT][/COLOR][COLOR=#666666][FONT=&quot] [/FONT][/COLOR][COLOR=#666666][FONT=&quot]entry[/FONT][/COLOR][COLOR=#666666][FONT=&quot] 1 [/FONT][/COLOR][COLOR=#666666][FONT=&quot]in[/FONT][/COLOR][COLOR=#666666][FONT=&quot] [/FONT][/COLOR][COLOR=#666666][FONT=&quot]list[/FONT][/COLOR][COLOR=#666666][FONT=&quot] [/FONT][/COLOR][COLOR=#666666][FONT=&quot]file[/FONT][/COLOR][COLOR=#666666][FONT=&quot] [/FONT][/COLOR][COLOR=#666666][FONT=&quot]/etc[/FONT][/COLOR][COLOR=#666666][FONT=&quot]/[/FONT][/COLOR][COLOR=#666666][FONT=&quot]apt[/FONT][/COLOR][COLOR=#666666][FONT=&quot]/[/FONT][/COLOR][COLOR=#666666][FONT=&quot]sources[/FONT][/COLOR][COLOR=#666666][FONT=&quot].[/FONT][/COLOR][COLOR=#666666][FONT=&quot]list[/FONT][/COLOR][COLOR=#666666][FONT=&quot].[/FONT][/COLOR][COLOR=#666666][FONT=&quot]d[/FONT][/COLOR][COLOR=#666666][FONT=&quot]/[/FONT][/COLOR][COLOR=#666666][FONT=&quot]getdeb[/FONT][/COLOR][COLOR=#666666][FONT=&quot].[/FONT][/COLOR][COLOR=#666666][FONT=&quot]list[/FONT][/COLOR][COLOR=#666666][FONT=&quot] (Suite), E[/FONT][/COLOR][COLOR=#666666][FONT=&quot]:The[/FONT][/COLOR][COLOR=#666666][FONT=&quot] [/FONT][/COLOR][COLOR=#666666][FONT=&quot]list[/FONT][/COLOR][COLOR=#666666][FONT=&quot] [/FONT][/COLOR][COLOR=#666666][FONT=&quot]of[/FONT][/COLOR][COLOR=#666666][FONT=&quot] [/FONT][/COLOR][COLOR=#666666][FONT=&quot]sources[/FONT][/COLOR][COLOR=#666666][FONT=&quot] [/FONT][/COLOR][COLOR=#666666][FONT=&quot]could[/FONT][/COLOR][COLOR=#666666][FONT=&quot] [/FONT][/COLOR][COLOR=#666666][FONT=&quot]not[/FONT][/COLOR][COLOR=#666666][FONT=&quot] [/FONT][/COLOR][COLOR=#666666][FONT=&quot]be[/FONT][/COLOR][COLOR=#666666][FONT=&quot] [/FONT][/COLOR][COLOR=#666666][FONT=&quot]read[/FONT][/COLOR][COLOR=#666666][FONT=&quot].[/FONT][/COLOR]

[COLOR=#666666][FONT=&quot]No[/FONT][/COLOR][COLOR=#666666][FONT=&quot] [/FONT][/COLOR][COLOR=#666666][FONT=&quot]sé[/FONT][/COLOR][COLOR=#666666][FONT=&quot] com solucionar-ho.... alguna idea???[/FONT][/COLOR]

---

### Post by wgarcia on 2018-05-28
Sembla que tens un fitxer per a un dipòsit no estàndard a la carpeta /etc/apt/sources.list.d/ , que es diu "getdeb.list", i que està causant problemes.

1) Saps d'on pot provenir aquest fitxer i quin dipòsit representa? Sembla com si fos algun programa que has instal·lat d'un PPA o alguna altra font no oficial.

2) Pots fer:

```
cat /etc/apt/sources.list.d/getdeb.list 
```

per veure què conté?

---

### Post by negu on 2018-05-28
Hola wgarcia, 
gràcies per la resposta... crec que tot ve de que vaig intentar instalar l'Avidemux i "sense voler" vaig interrompre la seva total instalació.... des d'aleshores que m'aàreix aquest missatge.
Aquest code que em dius l'he de posar a la consola? amb alguna ordre prèvia?? perdona però no és que vagi molt avançat amb l'ubuntu

---

### Post by wgarcia on 2018-05-29
Sí, obre una terminal i entra l'ordre tal com està escrita. Et mostrarà el contingut del fitxer en qüestió, enganxa'l per veure que hi ha.

---

### Post by negu on 2018-05-29
Entenc, 
ho he fet i el que m'apareix es el següent:

> txotxi@txotxi-SATELLITE-PRO-C50-A-1C9:~$ cat /etc/apt/sources.list.d/getdeb.listdeb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) xenial-getdeb apps
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) xenial-getdeb apps
txotxi@txotxi-SATELLITE-PRO-C50-A-1C9:~$ 

---

### Post by wgarcia on 2018-05-30
No coneixia aquest dipòsit, "archive.getdeb.net". Potser l'has habilitat intentant instal·lar algun paquet no oficial.
[http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)

i aquí explica que és un dipòsit no oficial. L'hauries de deshabilitar. Jo el que faria seria:


```
sudo rm /etc/apt/sources.list.d/getdeb.list
```

seguit de

```
sudo apt update
```

i si aquesta última ordre no dóna error:

```
sudo apt upgrade
```

---

