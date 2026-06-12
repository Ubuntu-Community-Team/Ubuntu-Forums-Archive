---
title: "Compartir unitat de cd amb windows"
date: 2009-08-16
forum: Catalan Team
---

### Post by socderafel on 2009-08-16
Bones a tots!

Li he comprat una netbook a la meua germana, una asus Eee.
Ve amb windows xp, i no lil puc llevar perque es connectara a una xarxa corporativa que sols accepta Windows. 
El problema es que, com tots sabeu, no té lector de CD. 
La meua intenció és compartir l'unitat de CD del meu PC amb ubuntu Jaunty i que accedeixca a ella desde la Netbook, per a poder instal.lar el que vulgui. 
Supose que es podrà fer, pero no se com...

---

### Post by papapep on 2009-08-16
Per això et cal SAMBA.

Instal·les el servidor:

```
sudo aptitude install samba
``` 

Edites el fitxer de configuració /etc/samba/smb.conf, i treus els punts i coma de davant de les següents línies:

```
# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

```

Si et cal, configures algun altre paràmetre del fitxer, com el grup de xarxa. El fitxer té molts comentaris que faciliten molt la configuració.

Un cop estiguis, deses i reinicies el dimoni de SAMBA:

```
sudo /etc/init.d/samba restart
```

I des de qualsevol ordinador amb protocol [SMB]("http://ca.wikipedia.org/wiki/Samba_(inform%C3%A0tica)") ja s'hauria de veure la unitat de CD compartida.

---

### Post by socderafel on 2009-08-16
Això inclou XP???

en arrivar a casa dema de mati ho prove i ja us dic alguna cosa.
Moltes gràcies!

---

