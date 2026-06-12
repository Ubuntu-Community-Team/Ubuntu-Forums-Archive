---
title: "Base Ooo no m'obre cap formulari"
date: 2009-08-28
forum: Catalan Team
---

### Post by RicardKp on 2009-08-28
Auxili, la setmana entrant començo un curset de bases de dades i ara em trobo que l'aplicació per a bases de dades de l'Openoffice 3.1.0 no m'obre cap formulari,la tinc instal·lada en un Ubuntu 9.04. I em surten aquests 3 errors:

[COLOR="Red"]1r.-No s'ha pogut establir la connexió a la font de dades "Nova base de dades1".

2n.-Codi d'error: 1000

No s'ha pogut carregar la classe de controlador 'org.hsqldb.jdbcDriver'.El camí a les classes dels controladors addicionals és 'file:///usr/share/java/hsqldb.jar vnd.sun.star.expand:$OOO_BASE_DIR/program/classes/sdbc_hsqldb.jar'.

3r.-Codi d'error: -1

Bad version number in .class file
[/COLOR]

Ajudeu-me!! no vull rebaixar-me a demanar l'Office als de casa que van amb güind**ous**, però el curset l'haig de fer per temes de feina!!!!!!!!!!!!!!!!!!!
*_Abans amb un Spectrum que amb güind**ous**_*

Salut i moltes gràcies per endavant.

---

### Post by papapep on 2009-08-28
No dónes prou informació. No expliques quina mena de base de dades has creat, si ja hi tens taules creades, si la base de dades és local o remota...
Has verificat, si ja en tens de creades, que puguis accedir i editar el contingut de les taules?

I, si us plau, deixa els temes "emocionals" a banda. Com a molt poden afegir pressió a qui et pugui respondre, cosa que no et convé :)

---

### Post by RicardKp on 2009-08-29
> **papapep said:**
> No dónes prou informació. No expliques quina mena de base de dades has creat, si ja hi tens taules creades, si la base de dades és local o remota...
Has verificat, si ja en tens de creades, que puguis accedir i editar el contingut de les taules?

I, si us plau, deixa els temes "emocionals" a banda. Com a molt poden afegir pressió a qui et pugui respondre, cosa que no et convé :)

Hola papapep:

Quan dic "no puc obrir" vull dir que no puc encetar-ne cap de nou. Clico la icona de l'aplicació, se'm obre l'**Auxiliar de bases de dades**, tenint seleccionat **Crear una bases de dades nova** clico **Següent**, deixo seleccionat **Sí, registra la base de dades** i **Obrir la base de dades per editar-la**i clico **Finalitza**, em surt la finestreta de **Desa**, li dic on desar-la, clico **Desa** i se'm obre una base de dades en la qual no hi puc treballar perquè em surten els 3 errors que he descrit en la meva anterior entrada si ho tanco tot, vaig on l'he desada i provo de tornar-la a obrir em tornen a sortir els 3 errors.

Salut i gràcies

---

### Post by papapep on 2009-08-29
Jo provaria amb un parell de cosetes:

1. Verificar que tinc els paquets al dia i sense problemes de dependències

```

sudo aptitude update && sudo aptitude safe-upgrade
```

2. Verificar que tinc instal·lat algun jre de Sun i que el tinc correctament configurat a l'Openoffice.

```
sudo aptitude install sun-java6-jre
```

i anar a Eines > Opcions > Openoffice.org > Java i fer que surti, si no surt ja, la JVM que tenim instal·lada. Si et cal dir-li on és, sol ser a /usr/lib/jvm/java-6-sun-1.6.0.14/jre/bin.

Després reinicia l'openoffice per a que agafi correctament les variables d'entorn, a veure si hi trobes algun canvi.

Aquesta 3.1 que tens instal·lada és [la del launchpad]("https://launchpad.net/~openoffice-pkgs/+archive/ppa")?

---

### Post by RicardKp on 2009-08-30
Moltes gràcies papapep,

Sembla que funciona correctament, no sé si eren els paquets i les dependències o era el Java, perquè en tots dos casos m'ha fet actualitzacions, però sense instal·lar ni esborrar res.

Salut
Ricard

---

