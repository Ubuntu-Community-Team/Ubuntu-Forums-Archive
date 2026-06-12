---
title: "Clau usb amb unitat de cd virtual"
date: 2009-03-10
forum: Catalan Team
---

### Post by SiscoGarcia on 2009-03-10
Com puc eliminar d'una clau usb la unitat virtual de cd amb un sistema de fitxers cdfs que crea un fitxer autorun.inf i s'autoexecuta (a més d'ocupar cert espai de memòria). He provat amb el gparted i no me'n surto.

L'aparell és un Memorex Traveldrive mini 2 GB, amb el sistema U3 smart.

Merci.

---

### Post by papapep on 2009-03-10
> He provat amb el gparted i no me'n surto

Perquè?? l'únic problema, en teoria, que pots tenir és que el tinguis muntat. Desmun-ta'l i no hauries de tenir cap problema en esborrar o formatar la partició.

---

### Post by SiscoGarcia on 2009-03-10
Doncs no sé perquè, per això ho pregunto, però no me'n surto. De fet el problema és que amb el Gparted no puc veure la unitat virtual, de manera que després d'haver-lo desmuntat, l'he formatat amb gparted i em torno a trobar amb aquesta unitat de CD virtual que llença la clau usb i "toca la pera".

Adjunto captura.

---

### Post by papapep on 2009-03-10
No sé Sisco, no entenc de què estàs parlant amb això del CD virtual. Però no importa, si el que vols és fer net, endolla el pendrive, _assegurat de que no està muntat_ i, sabent quin dispositiu és (sdX), fes:

```
sudo mkfs.vfat /dev/sdX
```

essent X la lletra que pertoqui (a, b, c, d...)
Evidentment procura no equivocar-te de lletra, que et carregaràs el que hi hagi en aquell dispositiu, sigui el que sigui :)

Fet això, hauries de tenir el pendrive USB net i polit.

---

### Post by SiscoGarcia on 2009-03-11
> **papapep said:**
> No sé Sisco, no entenc de què estàs parlant amb això del CD virtual.

M'ho puc imaginar però no sé com expressar-me. Resulta que la icona que munta és com un CD, i és aquest el que té fitxers executables (és el que a d'altres sistemes operatius apareix com un paquet de gestió del contingut de la clau USB, per tal d'accedir-hi millor (sic) al seu contingut (Adjunto captura de la icona un cop muntada).


> **papapep said:**
> Però no importa, si el que vols és fer net, endolla el pendrive, _assegurat de que no està muntat_ i, sabent quin dispositiu és (sdX), fes:

```
sudo mkfs.vfat /dev/sdX
```

essent X la lletra que pertoqui (a, b, c, d...)
Evidentment procura no equivocar-te de lletra, que et carregaràs el que hi hagi en aquell dispositiu, sigui el que sigui :)

Fet això, hauries de tenir el pendrive USB net i polit.

Doncs em sembla que no n'hi ha prou, perquè ja ho he fet sobre sdb:

```
Disc /dev/sdb: 1994 MB, 1994292736 octets
62 heads, 62 sectors/track, 1013 cylinders
Units = cilindres of 3844 * 512 = 1968128 bytes
Disk identifier: 0x00000000
```

i em retorna el següent missatge:

```
root@usuari-desktop:/home/usuari# sudo mkfs.vfat /dev/sdb
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: Will not try to make filesystem on full-disk device '/dev/sdb' (use -I if wanted)
```

Faig el que em proposa:

```
root@usuari-desktop:/home/usuari# sudo mkfs.vfat -I /dev/sdb
mkfs.vfat 2.11 (12 Mar 2005)
```


... i em quedo igual :(

---

### Post by SiscoGarcia on 2009-03-11
NO sé si hi hauria alguna manera alternativa d'accedir-hi a través dels ports usb. El que hi ha connectat ara mateix és:

```
usuari@usuari-desktop:~$ sudo lsusb
Bus 005 Device 006: ID 08ec:0020 M-Systems Flash Disk Pioneers TravelDrive
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 413c:3016 Dell Computer Corp. 
Bus 001 Device 005: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

I sembla que el que dóna problemes és al Device 006, no?

---

