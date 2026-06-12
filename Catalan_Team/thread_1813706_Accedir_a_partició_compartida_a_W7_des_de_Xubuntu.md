---
title: "Accedir a partició compartida a W7 des de Xubuntu"
date: 2011-07-28
forum: Catalan Team
---

### Post by simfomet on 2011-07-28
Acabo d'instal·lar en un netbook Xubuntu 11.04 i voldria poder accedir a una partició ntfs que tinc compartida en la xarxa local en un pc que té com a sistema operatiu Windows 7  Ultimate. 
Aquesta partició ja està  compartida amb els permisos  corresponents com dic però no sé que he de fer a  Xubuntu perquè "es vegin". He  vist una aplicació anomenada Gigolo que crec pot servir  pel tema però  no sé com fer-ho. Em podria ajudar algú del fòrum?

---

### Post by wgarcia on 2011-07-28
Penso que per a compartir carpetes a la xarxa local l'aplicació és "samba", però no l'estic fent servir ara mateix, per tant a veure si hi ha algú o alguna que pugui donar una mà.

---

### Post by akyra on 2011-07-28
Hola,

Jo normalment comparteixo carpetes amb disc externs que estan a la xarxa de casa.
Necesites samba que normalment ja ve instal·lat per defecte en ubuntu, però no sé amb Xubuntu.

Has de saber a quin grup de treball pertany la carpeta que vols compartir, i segurament la i.p. de l'ordinador amb W7, amb això ja hauria de ser possible accedir-hi.

Jo no faig servir cap aplicació per accedir a carpetes compartides, amb el nautilus ja fas prou.
Amb Ubuntu hauries d'anar a "Llocs" i seleccionar "partició de windows" (no tinc l'ordinador davant, però si no te'n surts a la nit t'ho puc mirar).

Salutacions.

---

### Post by Miquel Ubuntero on 2011-07-28
Samba no bé insta&#320;lat per defecte al xubuntu, però es pot afegir fàcilment amb Synaptic. Penso que és el que et cal.
Salut!

---

### Post by simfomet on 2011-07-28
> **akyra said:**
> Hola,

Jo no faig servir cap aplicació per accedir a carpetes compartides, amb el nautilus ja fas prou.
Amb Ubuntu hauries d'anar a "Llocs" i seleccionar "partició de windows"  (no tinc l'ordinador davant, però si no te'n surts a la nit t'ho puc  mirar).


Crec recordar que Xubuntu no fa anar el Nautilus, per tant diria que no serveix.

> **Miquel Ubuntero said:**
> Samba no bé insta&#320;lat per defecte al xubuntu, però es pot afegir fàcilment amb Synaptic. Penso que és el que et cal.


Ostres vaig entrar a Synaptic conscient que feia falta Samba i al posar Samba el buscador tots els elements que van sortir figuraven com instal·lats i vaig donar per suposat que venia per defecte. Ho revisaré, però un cop instal·lat Samba que faig? Té alguna cosa a veure l'aplicació Gigolo?

Gràcies per l'ajuda.

---

### Post by gunyoles on 2011-07-29
mira en aquest enllaç

[http://www.dedoimedo.com/computers/xubuntu-natty.html](http://www.dedoimedo.com/computers/xubuntu-natty.html)

explicant com fer-ho

---

### Post by simfomet on 2011-07-29
> **gunyoles said:**
> mira en aquest enllaç

[http://www.dedoimedo.com/computers/xubuntu-natty.html](http://www.dedoimedo.com/computers/xubuntu-natty.html)

explicant com fer-ho

Moltes gràcies! M'ho miro i a veure si me'n surto i us comento.

---

### Post by simfomet on 2011-08-04
Finalment me n'he sortit de connectar Xubuntu amb la partició compartida que tinc al pc de sobretaula amb Windows 7. 

Es tracta de amb l'aplicació Gigolo crear una connexió amb els paràmetres:

[LIST]
[*]Recurs compartit de windows
[*]A servidor posar la ip del pc al que vols connectar
[*]A través de compartició busques el que tens compartit al pc al que vols accedir
[*]Guardes i tens l'opció de deixar que connecti automàticament cada cop que obres Gigolo.
[/LIST]
Per cert, cal Samba per poder fer la connexió com sabeu molts de vosaltres però com que ja venia per defecte amb els sistema, llestos!!! 

Més que res per si li serveix a algú.

---

