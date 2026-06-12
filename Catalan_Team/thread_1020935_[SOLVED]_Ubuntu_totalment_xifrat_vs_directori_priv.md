---
title: "[SOLVED] Ubuntu totalment xifrat vs directori privat de 8.10"
date: 2008-12-24
forum: Catalan Team
---

### Post by Tomàs M. on 2008-12-24
Bon Nadal,
demà instal·laré, si tot va bé, una 8.10 a un Asus EEE 900.
M'agradaria saber la vostra opinió de les dues opcions. 
Buscant pel fòrum he vist que en [papapep]("http://ubuntuforums.org/member.php?u=280140") recomana [http://www.truecrypt.org/](http://www.truecrypt.org/) en [aquest fil]("http://ubuntuforums.org/showthread.php?t=426270") però és anterior a aquesta [nova funcionalitat]("https://help.ubuntu.com/community/EncryptedPrivateDirectory") de la Intrepid.
Així a primera vista, una cosa que hi veig és la incomoditat d'haver de posar manualment tot el que vulgui guardar de forma segura en aquesta carpeta. 
Què us sembla tot plegat?

Moltes gràcies.

---

### Post by CarlesOriol on 2008-12-25
Si aquest ordinador té un disc dur sòlid petit, t'aconsello usar el directori xifrat i així podràs tenir la carpeta /usr en squashfs amb un unionfs per tal de guanyar espai al disc.

---

### Post by Tomàs M. on 2008-12-25
> **CarlesOriol said:**
> Si aquest ordinador té un disc dur sòlid petit, 
oops... no, té disc dur "normal".

Gràcies!

---

### Post by marcoil on 2008-12-30
> **Tomàs M. said:**
> Així a primera vista, una cosa que hi veig és la incomoditat d'haver de posar manualment tot el que vulgui guardar de forma segura en aquesta carpeta. 
Què us sembla tot plegat?

Si només vols tenir un directori encriptat, crec que és millor emprar el que ve amb l'Intrepid.

Jo per motius de feina tenc tot el disc dur encriptat i és més complicat d'insta&#320;lar (has d'emprar el disc d'insta&#320;lació alternatiu i fer un munt de particions), però un cop ho tens en marxa te n'oblides.

Depèn del que necessitis, realment.

---

### Post by Tomàs M. on 2008-12-30
Ok, gràcies a tots dos; acabaré de decidir amb aquesta informació.

---

