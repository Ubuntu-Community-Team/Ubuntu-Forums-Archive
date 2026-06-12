---
title: "Dos perfils de monitors al Grub"
date: 2010-09-23
forum: Catalan Team
---

### Post by dmartinez116 on 2010-09-23
Com ja vaig explicar a un [post]("http://ubuntuforums.org/showthread.php?t=1573726") anterior, tinc dues gràfiques al sistema, amb dues eixides cadascuna. He instal·lat els últims controladors de 64 bits disponibles a la web de Nvidia.

M'agradaria saber si existeix la possibilitat de fer diferents entrades al grub per a fer que funcione una targeta (dos monitors d'escriptori) o l'altra (TV al menjador), es a dir... que segons l'opció d'inici que trie carregue una configuració de xorg.conf diferent.

Gràcies a tots.

---

### Post by kimet on 2010-09-25
Em sembla que no es possible, si de cas hauries d'instal.lar un nou sistema en una altre partició.
Una altre cosa seria la de posar un script a /etc/init.d o a .xinitrc si arrenques amb startx, que et donés la possibilitat d'escollir.

Salut.

---

### Post by wgarcia on 2010-09-25
Aquí hi ha una idea, prova-la si vols **sota la teva responsabilitat**, i estigues preparat per desfer la configuració des del LIVE CD o des de consola de text si no funciona, per poder tornar a l'entorn gràfic.

Si vols veure la font on ho he trobat és: 
[http://superuser.com/questions/191051/different-graphic-cards-drivers-while-booting-from-external-media](http://superuser.com/questions/191051/different-graphic-cards-drivers-while-booting-from-external-media)

Suposo que ja tens creat les dues versions de xorg.conf basades en la targeta que vols, anomena'ls per exemple:

/etc/X11/xorg.conf.nvidia1
/etc/X11/xorg.conf.nvidia2

Ara la idea és configurar dues opcions d'arrencada a  /boot/grub/grub.cfg i posar dos paràmetres diferents de nucli. Anomena'l per exemple "xconfig". La idea és que tot i que aquest paràmetre te l'has inventat i no fa res a la arrencada, s'escriu en un fitxer que un script després pot llegir per arrencar la targeta correcta. Es veuria d'aquesta manera (adaptant-lo als altres paràmetres que puguin tenir les teves línies d'arrencada):

menuentry "Ubuntu, Linux 2.6.32-24 nvidia1" {
  ...
  linux   /vmlinuz-2.6.32-24 root=UUID=885a6a07-fd6c-4638-aa17-d38997d477e1 xconfig=nvidia1 ro quiet splash
 ...
} 

menuentry "Ubuntu, Linux 2.6.32-24 nvidia2" {
  ...
  linux   /vmlinuz-2.6.32-24 root=UUID=885a6a07-fd6c-4638-aa17-d38997d477e1 xconfig=nvidia2 ro quiet splash
 ...
}

Com deia abans, els paràmetres de nucli que no es reconeixen a l'arrencada s'ignoren, però encara estan disponibles a /proc/cmdline. Usant això, pots escriure un script de bash que esculli l'arxiu xorg.conf correcte:

#!/bin/bash
rm -f /etc/X11/xorg.conf
config=`cat /proc/cmdline |sed -e 's/.*xconfig=\([a-z0-9]*\).*/\1/g'
ln -s /etc/X11/xorg.conf.$config /etc/X11/xorg.conf

Ara has de posar això en algun lloc del teu ordre d'arrencada, abans que comenci gdm.

Bé, aquesta és la idea, i em sembla que pot funcionar, però que consti que no ho he provat i com deia estigues preparat per desfer-lo i tornar a ser capaç d'arrencar si no funciona (i fes còpies de seguretat dels teus arxius xorg.conf per si no funciona l'script). 

NOTA: Si canvies el fitxer /boot/grub/grub.cfg, cada cop que actualitzis el nucli hauràs de tornar a actualitzar les línies corresponents. Les pots posar també a /etc/grub.d/40_custom (i fer "update-grub" des de la línia de comandes), però també les hauràs d'actualitzar quan s'actualitzi el nucli, perquè apuntin al nou nucli.

---

