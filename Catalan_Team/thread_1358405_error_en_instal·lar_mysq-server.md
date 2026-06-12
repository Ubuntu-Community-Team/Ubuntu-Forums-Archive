---
title: "error en instal·lar mysq-server"
date: 2009-12-18
forum: Catalan Team
---

### Post by Mikyatope on 2009-12-18
bones a tothom,

Tinc una instal·lació neta d'un ubuntu server 9.10 i fa 2 dies que em barallo per instal·lar el mysql-server, pero al fer l'apt-get install rebo aquest error

Setting up mysql-server-5.1 (5.1.37-1ubuntu4) ...
 * Stopping MySQL database server mysqld                                 [ OK ]
 * Starting MySQL database server mysqld                                 [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured


algú es troba amb el mateix problema ? gràcies!

---

### Post by papapep on 2009-12-18
Fes un:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

i després un:

```
sudo apt-get -f install
```

Després repeteix la ordre que et peta, a veure si torna a fallar o no. Si torna a fallar, jo provaria a canviar de dipòsit de programari, que no sigui que el que fas servir té algun problema. No és gens habitual que aquest paquet falli així com així.

---

### Post by Mikyatope on 2009-12-19
res, no ha funcionat. Al ser una instal·lació neta, l'he feta de nou, sel·leccionant directament d'instalar l'ubuntu com a LAMP, ara funciona correctament. gràcies!

---

