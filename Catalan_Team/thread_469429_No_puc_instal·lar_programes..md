---
title: "No puc instal·lar programes."
date: 2007-06-09
forum: Catalan Team
---

### Post by da-beat on 2007-06-09
Hola!!!

**Introducció**

M'acabo d'instal·lar l'Ubuntu 7.04, i he anat provant el "Afegeix/Elimina..." programes.

He instal·lat un parell de jocs, el Trigger i el Nexuiz. Ha donat uns quants errors durant la seva instal·lació. Però no m'hi he fixat, ja que com a que m'era una mica igual...

El Nexuiz no s'ha instal·lat i el Trigger sí (fins i tot sembla que funciona).

Però aquest no és el problema, **EL PROBLEMA ÉS:**

Ara quan vull instal·lar (o desinstal·lar) qualsevol cosa em dona error, NO PUC INSTAL·LAR RES!!!

E: /var/cache/apt/archives/libxine1_1.1.4-2ubuntu3_i386.deb: files list file for package `trigger' is missing final newline

i la pantalla següent:

(S'està llegint la base de dades ...
dpkg: avís important: falta el fitxer de la llista de fitxers del paquet "libphysfs-1.0-0", s'assumirà que el paquet no té cap fitxer actualment instal·lat.
dpkg: s'ha produït un error en processar /var/cache/apt/archives/libxine1_1.1.4-2ubuntu3_i386.db ( - -unpack):
 files list file for package `trigger' is missing final newline
S'han trobat errors en processar:
 /var/cache/apt/archives/libxine1_1.4-2ubuntu3_i386.deb
Procés aturat per haver-hi massa errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ha fallat la instal·lació d'un paquet. S'està intentant la recuperació:



Gràcies per endevant!!!

---

### Post by orestesmas on 2007-06-10
> **da-beat said:**
> 
E: /var/cache/apt/archives/libxine1_1.1.4-2ubuntu3_i386.deb: files list file for package `trigger' is missing final newline


Segons es desprèn d'aquest missatge el paquet "trigger" estava mal fet i genera un error. No podràs seguir modificant la base de dades dels paquets fins que no ho arreglis.

Jo desinstal·laria el paquet "trigger", que és el que està xungo.

Obre un terminal i tecleja:

sudo aptitude purge trigger

A veure què tal. Després, si tot va bé, ja podràs instal·lar al que vulguis.

---

### Post by da-beat on 2007-06-10
Merci orestesmas

però no ha funcionat:

```

sudo aptitude purge trigger
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'estan inicialitzant els estats dels paquets... Fet
S'està generant la base de dades de marcadors... Fet
Els paquets següents se suprimiran:
  trigger{p} 
0 paquets actualitzats, 0 instal·lats, 1 a suprimir i 0 a no actualitzar.
Es necessita obtenir 0B d'arxius. Després del desempaquetat s'alliberaran 684kB.
Esteu segur de voler continuar? [Y/n/?] Y
S'està escrivint la informació d'estat estesa... Fet
(S'està llegint la base de dades ... 
dpkg: avís important: falta el fitxer de la llista de fitxers del paquet «libphysfs-1.0-0», s'assumirà que el paquet no té cap fitxer actualment instal·lat.
dpkg: s'ha produït un error en processar trigger (--purge):
 files list file for package `trigger' is missing final newline
S'han trobat errors en processar:
 trigger
Procés aturat per haver-hi massa errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
S'ha produït un error en la instal·lació del paquet. S'està intentant restablir.


```


Com veieu torna a aparèixer el «libphysfs-1.0-0», jo crec que tot rau en aquest fitxer... :(

---

### Post by AlexMuntada on 2007-06-12
Aquest problema ja va sorgir a la llista fa temps amb un altre paquet:
[http://article.gmane.org/gmane.linux.ubuntu.user.catalan/4389](http://article.gmane.org/gmane.linux.ubuntu.user.catalan/4389)

La solució és afegir el salt de línia allí on hauria de ser; en el teu cas:
```
sudo bash -c "echo >> /var/lib/dpkg/info/trigger.list"
```

---

