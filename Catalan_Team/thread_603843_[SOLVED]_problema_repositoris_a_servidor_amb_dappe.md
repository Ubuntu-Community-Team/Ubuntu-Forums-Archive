---
title: "[SOLVED] problema repositoris a servidor amb dapper"
date: 2007-11-05
forum: Catalan Team
---

### Post by klonner on 2007-11-05
Hola, tinc un ordinador que faig servir de servidor i ara volia instalar el mysql, per posar una web amb PHP, i al instalar em demana el CD d'instalacio,i no el tinc (no se on collons està, fa mesos que el vaig instalar xDD).

He editat els repositoris i he posat un # davant on posa el CD, i he tornat a instalar xo ara diu que no s'instal·larà xq te dependències que no es poden instalar.

Quina solució tinc x aquest problema??

Salut i gracies!!

---

### Post by papapep on 2007-11-05
Enganxa'ns aquí el teu /etc/apt/sources.list i el missatge exacte de les dependències que no pot complir.

---

### Post by klonner on 2007-11-05
#deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted
#deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper-updates main estricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
#deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


desintalant el paquet i tornantlo a instalar s'ha arreglat però ara em diu que no troba el phpmyadmin....

---

### Post by papapep on 2007-11-05
Si vas a packages.ubuntu.com i busques el phpmyadmin, veuràs el següent:

```
Package Search Results

You have searched for packages that names contain phpmyadmin in distribution dapper, all sections, and all architectures.

Found 1 matching packages, displaying package 1.
Package phpmyadmin

    * dapper (web): set of PHP-scripts to administrate MySQL over the WWW **[COLOR="Red"][universe][/COLOR]**
      4:2.8.0.3-1: all



```

I com que tu tens comentades les línies del repositori "universe":

> **[COLOR="Red"]#[/COLOR]** deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper universe
[COLOR="Red"]**#**[/COLOR] deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper universe

fins que no les descomentis no podràs baixar-ne paquets.

---

### Post by klonner on 2007-11-05
Gràcies!! arreglat!! :lolflag:

---

