---
title: "crear carpeta amb contrasenya"
date: 2007-04-28
forum: Catalan Team
---

### Post by bikerbaixcamp on 2007-04-28
Bones,

M'agradaria saber si es pot fer que una carpeta (només aquesta) s'hagi d'obrir amb la contrasenya de l'usuari (el meu) que hagis entrat. Vaja, que no es pugui obrir directa i et demani la contrasenya.

Salut!

---

### Post by papapep on 2007-04-28
[Aquí]("http://www.truecrypt.org/")  trobaràs una eina que proporciona una funcionalitat semblant a la que demanes. De fet, el que fa és xifrar fitxers, particions o discs durs sencers, a fi d'utilitzar-los per emmagatzemar dades de manera segura.

Salutacions.

---

### Post by Syzygia on 2007-04-29
Hola,

no sé si això és el que t'interessa, però una solució senzilla és treure els permisos d'execució de la carpeta (chdir 0600 nom_carpeta). D'aquesta manera, només el teu usuari la podrà obrir (o un altre usuari fent un sudo)

---

### Post by bikerbaixcamp on 2007-04-29
> **Syzygia said:**
> Hola,

no sé si això és el que t'interessa, però una solució senzilla és treure els permisos d'execució de la carpeta (chdir 0600 nom_carpeta). D'aquesta manera, només el teu usuari la podrà obrir (o un altre usuari fent un sudo)

Bé, només tinc un usuari. A vegades ma cosina petita es posa a l'ordinador per jugar amb un programa d'aquests educatius. I es per a que no em remeni (per si de cas) la carpeta on tinc els arxius. No sé si existeix, però el que estaria bé es que quan anessis a clicar aquella carpeta et demanes la contrasenya. Tal com si fos quan hi ha actualitzacions noves que també te la demana.

Salut!

---

### Post by patrickfromspain on 2007-04-29
a sabes que tens alla...

guarro! ;)

ni idea del que preguntes, ho sento.. una solucio xapucera es fer una carpeta on nomes hi pugui accedir el root i fer un enllaç a l'escriptori, del tiups gksudo nautilus /la carpeta, llavors et demanaria password

---

### Post by bikerbaixcamp on 2007-04-29
> **patrickfromspain said:**
> a sabes que tens alla...

guarro! ;)

ni idea del que preguntes, ho sento.. una solucio xapucera es fer una carpeta on nomes hi pugui accedir el root i fer un enllaç a l'escriptori, del tiups gksudo nautilus /la carpeta, llavors et demanaria password

Entre d'altres coses.. fotos frikis amb els meus amics.. i clar per una nena de 7 anys no és massa saludable veure segons que... xD jejeje.

Això que dius sembla interessant. El root és el que s'ha de fer "sudo", no? Potser estaria bé.. el que passa es tan és si està a l'escriptori però sinó cal no cal. 

Com es faria això?

Gràcies! ;-)

---

### Post by patrickfromspain on 2007-04-29
podries fer alguna cosa aixi como sudo mkdir /privat, aixi tens una carpeta que nomes el root pot escriure. Despres, gksudo nautilus i mires les propietats de la carpeta i fas que nomes el root la pugui llegir i escriure. Per ultim, vas a l'escriptori, boto dret -> Crea llançadora, tipus aplicacio, nom que vulguis, i a Ordre hi poses: gksudo nautilus /privat i apa, fet.

Xapucero.. un rato, pro efectiu ;)

salut!

---

### Post by CarlesOriol on 2007-04-29
Per que no poses simplement un . abans del nom i deixes la carpeta oculta. No crec que cap nena de 7 anys la trobi.

/home/bikerbaixcamp/.fotosreuniodeveins

---

### Post by bikerbaixcamp on 2007-04-30
> **CarlesOriol said:**
> Per que no poses simplement un . abans del nom i deixes la carpeta oculta. No crec que cap nena de 7 anys la trobi.

/home/bikerbaixcamp/.fotosreuniodeveins

Uoo també, es que a vegades amb el més senzill no si pensa.. jejejeje

Gràcies CarlesOriol i també Patrick!

Doncs bé ocultarem les carpetes... jeje

;-)

---

### Post by Syzygia on 2007-04-30
Per fer que una carpeta només la pugui *atravessar* el root cal treure els permisos d'execució dels altres usuaris. Això es fa amb *chmod*:

Primer, es crea una carpeta amb propietari el root:
**sudo mkdir nom_carpeta**
Després es canvia els permisos:
**sudo chmod 0700 nom_carpeta**

Ara tothom pot veure la carpeta, però per entrar-hi cal ser el root
**sudo cd nom_carpeta**

Bé, espero que això et serveixi.

---

### Post by lluisanunez on 2007-04-30
I perquè no fas un usuari per la cosina? Només cal fer logout, sense rebotar el sistema i per tant és molt ràpid canviar d'usuari, i així és segur que no pot fer cap mal i pots encoratjar-la a explorar linux...

---

### Post by CarlesOriol on 2007-05-01
no cal ni fer logout. Pots canviar d'usuari al menu sortir i alternar entre ells amb ctrl+alt+f7 (f8...etc)

---

### Post by bikerbaixcamp on 2007-05-01
;-)

---

