---
title: "huawei k3520 i ubuntu 8.10"
date: 2009-01-12
forum: Catalan Team
---

### Post by joansfo on 2009-01-12
Hola,

Sóc nou al món Linux
M'acabo d'instalar ubuntu 8.10 i no aconsegueixo que el modem usb Huawei k3520 de vodafone funcioni.

He estat mirant i llegint forums. He provat d'instal·lar drivers i arxius que se suposa que havien d'arrreglar la cosa però no me'n surto.

Això és el que he provat:

usb-modeswitch_0.9.4-1_i386.deb
vodafone-mobile-connect_1.99.17-8_all.deb

vodafone-mobile-connect-card-driver-for-linux-2.0.beta3-ALL-i386-installer.run
python-vmc-2.5.2-3.deb

Vodafone diu que aquest modem no funciona amb linux (?)

Moltes gràcies per endavant

joan

---

### Post by RainCT on 2009-01-12
No conec el model aquest (jo tinc el Huawei E220), però si fas servir l'Ubuntu Intrepid (8.10) en principi t'hauria de funcionar bé. No et surt una notificació informant que s'ha trobat un dispositiu 3G i preguntant-te quin proveïdor fas servir?

**Actualització:** He trobat instruccions per a insta&#320;lar el mòdem aquest en l'Ubuntu Hardy (8.04) [aquí]("http://usrweblog.wordpress.com/2008/09/22/instalar-modem-3g-huawei-k3520-en-kubuntu/"). (Tot i això, si ho he entès bé -només ho he llegit per sobre- t'ho explica insta&#320;lant el programa de Vodafone, que trobo horrible; segur que si busques una mica més també trobes instruccions per a fer-lo funcionar sense el programa aquest). També pots mirar aquest altre programa (que és una versió millorada del de Vodafone): [wader](http://public.warp.es/wader).

**Actualització (2):** En un altre lloc comenten que amb l'Intrepid funciona sense problemes sempre i quan tinguis el mòdem connectat abans d'encendre l'ordinador. Prova-ho a veure... :)

---

### Post by joansfo on 2009-01-14
gràcies per la teva resposta,

Ubuntu si reconeix el modem. Inclús he configurat el proveidor (vodafone) amb el número que s'ha de marcar i tot plegat.

Quan inicio l'ordinador amb el modem conectat, l'aparell prova de'establir connexió però no se'n surt.

Entenc que els autoexecutables que porta el modem no em serveixen per a res oi?

El k3520 és com un llapis usb. Permet connexions 3G. El 220 també el tinc.
Primer provaré això de WADER i si no provaré de canviar al 220 a veure què passa.
gràcies altre cop

per cert: utilitzo ubuntu 8.10 i el meu ordinador és un VAIO
joan

---

### Post by joansfo on 2009-01-14
Perdona la meva ignorància... sóc totalment neòfit...:confused:

Un cop a la pàgina de Wader què és el que haig de descarregar i instalar?

---

### Post by RainCT on 2009-01-14
L'autor no proporciona paquets per a l'Intrepid (només per a Gutsy i Hardy), però te n'he preparat en un moment :). Per a insta&#320;lar-los, vés a Sistema -> Administració -> Fonts de programari, vés a la pestanya "Programari de tercers", prem a "Afegeix" i introdueix "deb [http://ppa.launchpad.net/rainct/ubuntu](http://ppa.launchpad.net/rainct/ubuntu) intrepid main", tanca la finestra i accepta d'actualitzar les llistes de paquets i finalment vés a Sistema -> Administració -> Gestor de paquets Synaptic i insta&#320;la el paquet "wader" (pot ser que encara tardi unes hores en aparèixer el paquet [**Actualització:** Sembla que no vol compilar-se a l'Intrepid.]).

Tot i això, t'ha demanat el PIN per al mòbil? Perquè ara que hi penso el problema deu ser aquest... Jo el vaig desactivar fa temps, cosa que pots fer posant la SIM dins d'un mòbil normal, desactivant-lo allà i tornant-la a posar dins de mòdem.

---

### Post by joansfo on 2009-01-15
Gràcies altre cop RainCT,

Però no me'n surto. Sóc massa talòs potser...

Això que comentes del PIN ho vaig pensar i el vaig desactivar des del Vodafone Mobile Connect a windows... i res. També he fet el que m'has dit i tampoc no ha funcionat.

He mirat d'instalar el paquet que has preparat però em quedo en el primer pas (ja et dic que sóc una mica burro) perquè no trobo 'fonts de programari' dins de sistema->administració.

És possible?
Total: m'he instalat ubuntu 8.04 i he provat de seguir les passes proposades al link que em vas donar i que ja havia provat anteriorment. Però resulta que allò és per a Kubuntu i hi ha un pas en el que necessito Konqueror i no el tinc instalat. No sé si Ubuntu 8.04 té un explorador que em serveixi o m'haig de descarregar el konqueror (cosa que dubto)

Bé, miraré d'nar provant coses i ja et diré

Gràcies 

Joan

---

### Post by RainCT on 2009-01-15
> **joansfo said:**
> He mirat d'instalar el paquet que has preparat però em quedo en el primer pas perquè no trobo 'fonts de programari' dins de sistema->administració.

També pots obrir la finestra fent el següent a la terminal:

```
gksu software-properties-gtk
```

Alternativament, tot el que dic al primer paràgraf es pot fer des de la terminal amb:

```
echo "deb http://ppa.launchpad.net/rainct/ubuntu intrepid main" | sudo tee -a /etc/apt/sources.list; sudo aptitude update; sudo aptitude install wader
```

---

### Post by joansfo on 2009-01-15
RainCT,

m'he instalat el 8.04
això que em dius em servirà o em torno a instalar el 8.10?

Per cert, que haig d efer quan entro a WADER. Què m'haig de descarregar?

Ets molt amable. No sé com us ho feu 

Moltes gràcies

Joan

ps: ei que també busco al google i a tot arreu però enlloc no trobo la solució
You are my only hope;)

---

### Post by lluisanunez on 2009-01-15
Si el sistema et reconeix el mòdem, llença això del Vodafone-mobile-connect... a la paperera  i insta&#322;la't el gnomeppp. Una mica de paciència amb la configuració i funcionarà.

---

### Post by joansfo on 2009-01-16
nois i noies,

no sé què són les dependències, no sé què és un script,...

tot i que ho continuaré provant em sembla que em buscaré algun curset o alguna cosa semblant, és el millor que puc fer no?

salut i gràcies

joan

---

### Post by papapep on 2009-01-17
No és tan complicat això que comentes, Joan:

Les dependències, en el cas que ens ocupa ara, són paquets (programes, per a que ens entenguem) que són necessaris per a que un altre funcioni correctament. P. ex, per a que el programa A funcioni, necessita que B, C i D siguin instal·lats prèviament.

De la wikipedia: 

> Script: En informàtica, un script és un guió o conjunt d'instruccions. Permeten l'automatització de tasques creant petites utilitats. És molt utilitzat per l'administració de sistemes UNIX. Són executats per un intèrpret d'ordres i normalment són fitxers de text. També un script pot considerar una alteració o acció a una determinada plataforma, Molt semblant als trucs que s'usen per alterar jocs i aconseguir coses extres ...

L'únic que et cal és llegir, i t'asseguro que trobaràs tones d'informació sobre aquestes coses a internet :-)
Tots hem passat per aquí, o sigui que no et pensis que saps poc ni res semblant ;-)

PD I sempre tens el fòrum per preguntar el que no acabis de tenir clar...

---

### Post by RainCT on 2009-01-17
> **joansfo said:**
> 
m'he instalat el 8.04
això que em dius em servirà o em torno a instalar el 8.10?


Per a la 8.04 has d'agafar els paquets de [https://launchpad.net/~wader/+archive/ppa](https://launchpad.net/~wader/+archive/ppa), de manera que la «ordre per a fer-ho tot» queda així:

```
echo "deb http://ppa.launchpad.net/wader/ubuntu hardy main" | sudo tee -a /etc/apt/sources.list; sudo aptitude update; sudo aptitude install wader
```

---

### Post by joansfo on 2009-01-20
Gràcies a tots altra vegada,

Seguiré els vostres consells i indicacions.
A veure si aviat em converteixo en un ubuntaire de ple dret.

Salut i fins aviat

Joan

---

