---
title: "/etc/default/grub no hi és en el meu 12.04"
date: 2012-09-29
forum: Catalan Team
---

### Post by jinglada on 2012-09-29
El fitxer /etc/default/grub no hi és.  És greu?

---

### Post by wgarcia on 2012-09-29
És possible que encara tinguis la versió antiga de "grub". Què surt quan des d'una terminal fas

```
sudo dpkg -l grub-common
```

---

### Post by jinglada on 2012-09-29
> **wgarcia said:**
> És possible que encara tinguis la versió antiga de "grub". Què surt quan des d'una terminal fas

```
sudo dpkg -l grub-common
```

joan@joan-laptop:~$ sudo dpkg -l grub-common
[sudo] password for joan: 
Desitjat=desconegUt/Insta&#320;la/supRimeix/Purga/retín(H)
| Estat=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Estat,Err: majúsc.=dolent)
||/ Nom            Versió        Descripció
+++-==============-==============-============================================
ii  grub-common    1.99-21ubuntu3 GRand Unified Bootloader (common files)
joan@joan-laptop:~$

---

### Post by wgarcia on 2012-09-29
Les dues "ii" a l'última línia diu que sí que tens instal·lat el grub actual. 

Aleshores sí que hauries de tenir el fitxer /etc/default/grub. Què surt quan des d'una terminal fas:

```
cat /etc/default/gub
```

?

---

### Post by jinglada on 2012-09-29
> **wgarcia said:**
> Les dues "ii" a l'última línia diu que sí que tens instal·lat el grub actual. 

Aleshores sí que hauries de tenir el fitxer /etc/default/grub. Què surt quan des d'una terminal fas:

```
cat /etc/default/gub
```

?

Mira:

joan@joan-laptop:~$ cat /etc/default/gub
cat: /etc/default/gub: El fitxer o directori no existeix
joan@joan-laptop:~$ 


El directori sí que existeix:

joan@joan-laptop:~$ cd /etc/default
joan@joan-laptop:/etc/default$ ls g*
google-chrome  google-talkplugin
joan@joan-laptop:/etc/default$

---

### Post by wgarcia on 2012-09-29
Volia dir 

```
cat /etc/default/grub
```

però segons el que dius després, la verificació que fas sembla confirmar que no tens el fitxer /etc/default/grub.

En principi si el sistema està iniciant correctament no sembla greu que no tinguis aquest fitxer. Es fa servir per introduir canvis en el menú d'arrencada grub. Suposo que una reinstal·lació del paquet "grub-common" el reinstal·laria, però pot quedar així de moment.

---

### Post by jinglada on 2012-09-29
> **wgarcia said:**
> Volia dir 

```
cat /etc/default/grub
```

però segons el que dius després, la verificació que fas sembla confirmar que no tens el fitxer /etc/default/grub.

En principi si el sistema està iniciant correctament no sembla greu que no tinguis aquest fitxer. Es fa servir per introduir canvis en el menú d'arrencada grub. Suposo que una reinstal·lació del paquet "grub-common" el reinstal·laria, però pot quedar així de moment.

Tampoc hi és (no m'havia fixat en la manca de la "r")

joan@joan-laptop:~$ cat /etc/default/grub
cat: /etc/default/grub: El fitxer o directori no existeix
joan@joan-laptop:~$

---

