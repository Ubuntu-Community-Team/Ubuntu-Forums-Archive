---
title: "no em detecta la càmera (Nikon Coolpix 4600)"
date: 2009-07-01
forum: Catalan Team
---

### Post by bikerbaixcamp on 2009-07-01
Bones!

Doncs com explicava en aquest fil: [http://ubuntuforums.org/showthread.php?t=1186279](http://ubuntuforums.org/showthread.php?t=1186279) he passat (a través d'actualització) a la 9.04. Doncs bé, abans em detectava la càmera (tinc una Nikon Coolpix 4600) i tenia el Digikam. Ara no em detecta la càmera ni pel Digikam; ni en definitiva em detecta al ficar-la, ni com USB, ni targeta ni res... 

Com ho puc solucionar? 

Salut!

---

### Post by PatrickVogeli on 2009-07-01
[http://ubuntuforums.org/showpost.php?p=6369481&postcount=4](http://ubuntuforums.org/showpost.php?p=6369481&postcount=4)

[http://ubuntuforums.org/showthread.php?t=972192&highlight=coolpix+4600](http://ubuntuforums.org/showthread.php?t=972192&highlight=coolpix+4600)

---

### Post by bikerbaixcamp on 2009-07-01
No ho he acabat d'entendre. He fet aquells dos codis al terminal i m'ha sortit això:

Disc /dev/sda: 320.0 GB, 320072933376 octets
255 heads, 63 sectors/track, 38913 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34333432

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1       38157   306496071   83  Linux
/dev/sda2           38158       38913     6072570    5  Estesa
/dev/sda5           38158       38913     6072538+  82  Intercanvi Linux / Solaris
sergi@sergi-desktop:~$  lsusb
Bus 001 Device 003: ID 0566:3004 Monterey International Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 005: ID 04b0:0130 Nikon Corp. Coolpix 4600 (ptp)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by PatrickVogeli on 2009-07-01
[http://ubuntuforums.org/showpost.php?p=6369481&postcount=4](http://ubuntuforums.org/showpost.php?p=6369481&postcount=4)

---

### Post by bikerbaixcamp on 2009-07-02
Buff.. es que l'anglès no és el meu fort i em perdo a la conversa. Algú tan amable a explicar-m'ho en català? 

;)

---

### Post by papapep on 2009-07-02
per sort l'era internètica ens dóna moltes eines, que cal emprar, clar...:

[http://translate.google.com](http://translate.google.com)

---

### Post by bikerbaixcamp on 2009-07-02
Gràcies, 

la cosa funciona utilitzant un altre mode la càmera el PTP aquest i no a través d'USB. 
La cosa es que ara es pot entrar, modificar.. però no me la detecta el "Digikam", he provat diverses maneres però res...

---

