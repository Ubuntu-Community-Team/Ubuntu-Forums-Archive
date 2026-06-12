---
title: "Missatge d'Error al muntar un arxiu .ISO"
date: 2011-09-20
forum: Catalan Team
---

### Post by idrojsnop on 2011-09-20
Hola,

Estinc intentant muntar un arxiu .ISO amb la comanda següent:
```
sudo mount -t iso9660 -o loop matu20Xa.iso /media/iso1
```

I em dóna el següent error:
```
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       En alguns casos, es pot trobar informació útil a syslog,
        proveu dmesg | tail o així
```


He provat diferents coses així com: 
- ignorar la part -t iso9660, però em diu que haig d'introduïr el format en què està l'arxiu.
- canviar el directori de muntatge, tampoc funciona.
- canviar el nom de l'arxiu iso, tampoc funciona.

Aviam si em podeu ajudar!
Moltes gràcies!

---

