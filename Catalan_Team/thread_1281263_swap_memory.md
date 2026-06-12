---
title: "swap memory"
date: 2009-10-03
forum: Catalan Team
---

### Post by venusfenix on 2009-10-03
buenas,

bon dia,

tinc un portatil AMD Turion 64x2 amb jaunty 64 bits.
aacabo de donar-me conte que no tinc swap memory, quan hi vaig instal.lar el jaunty vaig particionar un disc dur de 2Gb per aixo, pero desconec el perque pero no funciona, o no está actiu.

com tinc que procedir??

Moltes gracies.

---

### Post by PatrickVogeli on 2009-10-04
pots enganxar el resultat de fer les següents ordres?

cat /etc/fstab

swapon -s

blkid

Salut

---

### Post by quitus on 2009-10-04
Amb el gparted pots veure totes les particions del teu dis dur, comprova l'existència d'aquesta partició que dius i si està activa (boto de la dreta sobre la partició)

salut

---

### Post by venusfenix on 2009-10-18
he probat aquesta opcio, el gparted i res. es deixa configurar pero al reiniciar, res de res.

quan pogui, provaré d'engaxar el resultat de les probes, ara tinc un altre problema amb el firefox

---

### Post by oriolsbd on 2009-10-18
Hola,

Si saps el nom de la partició que en principi vas destinar a Swap (pel que comentes, suposo que sí que ho saps), primer hauries de trobar el seu UUID. Per a fer-ho, executa la comanda següent:
```
vol_id /dev/sdxx
```
En aquest cas, substitueix el "sdxx" per la teva partició. D'aquí, agafa el valor del que et retorni la variable ID_FS_UUID. En el meu cas, per exemple, em retorna "8ec7de1a-33e2-44ad-b630". Ara, edita el fitxer /etc/fstab:
```
sudo gedit /etc/fstab
```
Afegeix-hi aquesta línia:
```
UUID=8ec7de1a-33e2-44ad-b630  none  swap  sw  0  0
```
Aquí hi has de canviar el UUID que poso pel de la teva partició. Desa el fitxer i torna a reiniciar.

Salut!

---

