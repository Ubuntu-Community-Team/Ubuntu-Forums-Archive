---
title: "UNity desaparegut després d'actulitzar"
date: 2013-05-19
forum: Catalan Team
---

### Post by tanreb20 on 2013-05-19
Bones!

Fa temps que no entro per aqui pero estic desesperat perque ho he provat tot :(

Ahir estava amb una actualització rutinaria i em saltava el error de parcial update, aixi que entro al synaptinc, marco totes les coses que estaven en "broke" i sembla que tot bé.

AL fina lno se que va passar que aquest matí m'he trobat sense escriptoi, el Ubuntu funciona pero el unity ha desaparegut, i al intentar instalar em dona:

[FONT=Century Gothic]alorma@Hogwarts ~ $ sudo apt-get install unity
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
 unity : Depende: libunity-core-6.0-5 (= 7.0.0daily13.05.15ubuntu.unity.experimental.certified-0ubuntu1) pero no va a instalarse
         Depende: unity-common (= 7.0.0daily13.05.15ubuntu.unity.experimental.certified-0ubuntu1) pero 7.0.0daily13.05.16ubuntu.unity.experimental.certified-0ubuntu1 va a ser instalado
E: No se pudieron corregir los problemas, usted ha retenido paquetes rotos[/FONT]

També em sortien un munt de paquets de l'estil unity-lens* o unity-scope que si he pogut istalar.

Algú s'hi ha trobat? Sabeu com solucioanro?

He provat el reinstalant el compiz, y el ccsm funciona, pero apart d'aixó res...

Des de synaptic em marca tan sols dos paquets de unity, el **= 7.0.0daily13.05.15ubuntu.unity.experimental.certified-0ubuntu1**, y el estable

---

### Post by wgarcia on 2013-05-20
Forçar les actualitzacions parcials pot ser problemàtic i sols s'ha de fer amb coneixement de causa, perquè pot trencar dependències i forçar la desinstal·lació de paquets essencials. Però tot es pot arreglar, és clar. 

Segons el que dius al teu missatge estàs tenint accés almenys a una terminal, tot i que no tinguis accés a l'entorn gràfic, oi? Així que ja tens molt guanyat per resoldre el problema. 

Per començar, tens dipòsits no estàndard habilitats? Si hi ha dipòsits no estàndard relacionats amb unity convindria deshabilitar-los. Seria útil que enganxessis aquí el següent fitxer per comprovar-ho: "/etc/apt/sources.list". 

Segon: prova les següents comandes a la terminal, a veure si aconsegueixen els problemes de dependències no resoltes que es mostren en les sortides que has enganxat:

```
sudo apt-get dist-upgrade
sudo apt-get install -f
sudo dpkg --configure -a
```

A veure si hi ha sort.

---

### Post by tanreb20 on 2013-05-20
Bones wgarcia.

SI, al final he instalat un cinammon per anar tirant mentres no resolc el problema.

El meu sources.list és el seguent:

# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Alpha amd64 (20130412)]/ raring main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring-updates universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring-updates multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main


No tinc cap repositori no oficial habilitat.

JA vaig provar a fer el que dius, i a la conola em surt que tot está correcte, no hi ha paquets er actualitzar.

El cas es que des de synaptic, quanmarco el libunity-core-6.0-5 el marca com a trencat, i no hi ha manera de trobar quins paquets son els que están malament.

---

### Post by wgarcia on 2013-05-21
No es veu res estrany al fitxer que has enganxat. 

Prova a veure 

```
sudo apt-get install -f unity
```

---

### Post by tanreb20 on 2013-05-21
Ja ho javia provat i res:

alorma@Hogwarts ~ $ sudo apt-get install unity -f
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
 unity : Depende: libunity-core-6.0-5 (= 7.0.0daily13.04.18~13.04-0ubuntu1) pero no va a instalarse
         Depende: unity-common (= 7.0.0daily13.04.18~13.04-0ubuntu1) pero 7.0.0daily13.05.16ubuntu.unity.experimental.certified-0ubuntu1 va a ser instalado
E: No se pudieron corregir los problemas, usted ha retenido paquetes rotos.

---

### Post by tanreb20 on 2013-05-21
Bé al final he reinstalat el sistema que ja en tinc experiencia...

Tanco el tema.

Merci!

---

