---
title: "emerge??"
date: 2007-05-31
forum: Catalan Team
---

### Post by kukat on 2007-05-31
Quan utilitzaba el Sabayon, estava el comandament "emerge", que instalaves les coses en un moment. posaves emerge amarok i te l'instalava automáticament. Hi ha algun comandament similar a ubuntu? aquest no funciona. 
He provat a instalar nous programes amb "Afegeix/elimina" però hem demana un CD que no tinc (???) Jo tinc l'Ubuntu Studio, i hem demana el Ubuntu Studio 7.04 _Feisty Fawn_ - Release i386 (20070415)...No es el mateix que tinc? Tinc que baixar-me algun altre disc? 

Gràcies!!

---

### Post by Seti on 2007-05-31
```

sudo emerge foo

```

with ubuntu (debian based)

```

sudo apt-get install foo

```

---

### Post by kukat on 2007-05-31
Però instala paquets sense tindre'ls a un CDroom??? Es que hem torna a ixir el mateix missatje d'error a la consola instalant l'amarok

---

### Post by kukat on 2007-05-31
Ahhhhh!!! Crec que ja se el que passa: L'Amarok no està pal Gnome??? Però no deuría de donar-me l'error del CD-ROOM....no se que hi passa. 

Gràcies per el sudo emerge!! Al Sabayon es veu que no feia falta posar el Sudo per que pots funcionar com a root sense problemes...no? Jjejejej, es que tinc que anar ensenyant-me per a poder algún dia ajudar!!:D

---

### Post by RainCT on 2007-05-31
Sí que hi és.

Vés a «Sistema -> Administració -> Software Sources» i allà, sota «Descarregable d'Internet» marca totes les opcions excepte «Codi Font» (si vols desmarca el CD-ROM, a baix). Llavors executa «sudo apt-get update» a la terminal, i ja podràs insta&#320;lar el que vulguis.

---

### Post by papapep on 2007-05-31
Emerge és una comanda pròpia de les distros "Gentoo like" i, evidentment, Ubuntu no n'és pas una d'elles.
Si vols saber com funciona la gestió de paquets a les distros "Debian like" com Ubuntu, pots fer un cop d'ull [aqui]("http://recepteslinux.homelinux.org/wordpress/?p=14")  i  una segona part [aquí]("http://recepteslinux.homelinux.org/wordpress/?p=15"). 
I, per cert, Amarok, evidentment que és als repositoris de l'Ubuntu, el que has de saber trobar-lo i instal·lar-lo. ;)

---

### Post by lluis.dalmau on 2007-05-31
La clau de l'èxit és saber quin/s repositori/s de paquets són els que t'interessen.

Si busques a google trobaràs els repositoris adequats per la versió de l'Ubuntu que tens instal·lada. Afegeix-los o amb programes de l'estil del Synaptic o a pèl, directament editant /etc/apt/sources.list, llavors actualitzes la llista de paquets disponibles en base als nous repositoris definits sudo apt-get update i instal·la el què necessitis sudo apt-get install nomdelpaquet.

---

