---
title: "Sobtat mal funcionament d'un pen drive"
date: 2009-02-19
forum: Catalan Team
---

### Post by Jayhawker on 2009-02-19
Mentre estava copiant uns arxius, se'm va penjar el pen drive als quals els passava. No vaig tenir més remei que treure'l sense poder desmuntar-lo. Des d'aleshores que el linux no em reconeix el pen drive. Els altres que tinc continuen funcionant bé. Hi ha cap manera de poder fer que aquest pen drive torni a funcionar? 

Mercès.

---

### Post by thedavis on 2009-02-19
¿Pots probar de fer-lo servir dins d'un Windows?

Segur que s'ha fet malbé el sistema d'arxius...

---

### Post by Jayhawker on 2009-02-19
> **thedavis said:**
> ¿Pots probar de fer-lo servir dins d'un Windows?

Segur que s'ha fet malbé el sistema d'arxius...

Dins Windows l'únic que aconsegueixo és que me'l detecti com a "dispositiu desconegut", però fent gala de l'ortopèdia que és Windows, cap dels seus mecanismes de solució de problemes serveix per a res, tret de robar-te temps. 

Hi ha cap manera de solucionar això del sistema d'arxius?

Moltes mercès.

---

### Post by thedavis on 2009-02-19
Fes la prova amb el gparted a veure si encara que et monta el dispositiu, el detecta. 

Si el detecta podrás donar-li format de nou. 

Abans, però, intenta fer un "fsck.vfat" (suposo que la partició es Fat32).

Salutacions

---

### Post by Jayhawker on 2009-02-23
> **thedavis said:**
> Fes la prova amb el gparted a veure si encara que et monta el dispositiu, el detecta. 

Si el detecta podrás donar-li format de nou. 

Abans, però, intenta fer un "fsck.vfat" (suposo que la partició es Fat32).

Salutacions

Merci per la resposta però sóc una mica novell en això de linux. Com faig un gparted i com puc activar l'ordre que indiques més avall?

Merci

---

### Post by papapep on 2009-02-23
Hola Jayhawker,

Et recomano una bona llegida a aquest tutorial:

[https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes](https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes)

t'ajudarà a entendre moltes cosetes que ara et deuen semblar arameu ;-)

Potser serà més simple, per a aquest cop, mirar-te les particions des de l'intèrpret d'ordres. Obre un terminal (Aplicacions > Accessoris > Terminal) i enganxa-hi això (amb el pendrive endollat!):

```
sudo fdisk -l /dev/sd*
```

Enganxa aquí tot el que et surti en executar l'ordre.

---

### Post by thedavis on 2009-02-23
El gparted es un programa per editar particions del disc dur (és com el Partition Image..més o menys) 

El pots instalar directament fent click --> [apt://gparted]("apt://gparted")

Ves amb cura ja que amb el gparted et pots carregar tot un disc dur sense voler...

I tal i com comenta papapep posa la sortida de l'ordre sudo fdisk -l /dev/sd*

Salutacions

---

### Post by oriolsbd on 2009-02-23
Hola, al que diu en thedavis, només falta indicar com s'engega el programa. :-)

Pots fer-ho escrivint "sudo gparted" des del terminal o, quan l'instal·lis, el tindràs a través del menú "Sistema>Administració>Editor de Particions" (o alguna cosa semblant, ara no estic en un PC amb Ubuntu).

Sobretot, tal i com diu en thedavis, ves amb compte, perquè és molt senzill d'utilitzar i va molt bé, però aquest programa treballa directament sobre les particions del disc dur, i és perillós tocar res si no es té molt clar què s'està fent.

---

