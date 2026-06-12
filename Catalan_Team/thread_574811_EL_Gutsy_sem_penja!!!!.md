---
title: "EL Gutsy sem penja!!!!"
date: 2007-10-13
forum: Catalan Team
---

### Post by xdevent on 2007-10-13
He actualitzat la meva Festy a Gutsy, i al carregar es penja en diferents llocs del procès. He intentat baixar-me el live-cd (RC1) de Gutsy per arreglar-ho i fer una instal·lació nova, però també li passa el mateix!!!`

Algú que em pugui ajudar?

---

### Post by Ferri on 2007-10-13
Podries ser més específic?
On es penja concretament? Tens algun missatge d'error o potser els resultats d'un "dmesg" per poder tenir alguna pista més?

---

### Post by anigwei on 2007-10-13
Si se't penja durant l'arranc, treu-li els paràmetres splash i quiet de l'arranc (com fer-ho [http://uoc.eines.cat/wiki/doku.php?id=opcions_grub](http://uoc.eines.cat/wiki/doku.php?id=opcions_grub)) i sabrem en quin punt.

D'altra manera, prova la Alternate...

---

### Post by xdevent on 2007-10-13
Bé, he fet lo del grub i m'he quedat sorprès... se penja quan li dóna la **** gana. Ho he fet 5 cops i un a cada lloc diferent. No puc fer anar la consola ja que el recovery mode li passa el mateix.

M'oloro que és el kernel, us dóno més detalls que em fan pensar això:

[LIST]
[*]Al acualitzar m'ha quedat instal·lada una imatge del kernel de feisty que tenia abans, i des d'aquesta puc carregar sense problemes
[*]El CD de Ubuntu Gutsy RC1 que me baixat fa poc també em fa el mateix
[/LIST]

He enviat la incidencia al lloc de bugs de ubuntu, perque em sembla k pot ser molt greu, i estan a pocs dies de el llançament. Si ho areglessim ja avisaria a la web dels bugs.

També he de dir que és una x86 en un ordenador que fa anar un AMD de 64 bits, cosa que amb la feisty no donava problema. Faig anar la versio generic del kernel.

Espero les vostres respostes amb delit. A vere si ho podem solucionar aviat això i així no us molesto més ;)

---

### Post by Ferri on 2007-10-14
Quina és la versió de kernel que sí et funciona? I la que no?
Veig una mica estrany que et funcioni una kernel de Festy a Gutsy sense problemes.
Jo ahir vaig tenir un petit problema amb la darrera kernel de Gutsy (2.6.22-14-generic), en principi relacionats amb uns paràmetres de l'ACPI que faig servir perquè em funcionin algunes tecles del portàtil i se'm va arreglar reinstal·lant els paquets i fent els canvis que necessitava des de fora de X. No crec que tingui res a veure, però explico el que el va passar per si un cas. De fet, tampoc estic segur que fos necessari fer els canvis des de fora de X.

---

### Post by xdevent on 2007-10-14
La que em funciona és la 2.6.20-16, i la que no és la que has dit precisament tu, la 2.6.22-14

---

