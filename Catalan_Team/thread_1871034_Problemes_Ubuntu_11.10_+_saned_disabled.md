---
title: "Problemes Ubuntu 11.10 + saned disabled"
date: 2011-10-28
forum: Catalan Team
---

### Post by diablessamariken on 2011-10-28
Hola ubuntaires

ja fa dies que arrossego el problema i no he sabut trobar-hi una solució cercant a internet casos similars.

Fa un parell de setmanes vaig actualitzar a ubuntu 11.10 però a mitja actualització l'ordinador es va penjar. És un ACER Aspire 5104WLMI - AMD Turion 64 x2. Vaig obligar-lo a reiniciar pensant que podria tornar a començar l'actualització però no va ser així.

Un company m'ha ajudat a actualitzar tot el que quedava pendent a través de la consola, però malgrat que totes les actualitzacions estan al dia segueixo tenint un problema.

Quan arrenca l'ordinador no es carrega l'entorn gràfic i queda penjat en un punt on em dóna la següent informació:

[B]PulseAudio configured for per-user sessions
      saned disabled;    edit /etc/default/saned      [OK][/B]

I aquí s'atura.
Aleshores faig un Crtl+Alt+F1 i aconsegueixo accedir a la consola des d'on puc entrar a l'entorn gràfic a través de la comanda: 

sudo /etc/init.d/gdm restart

Però el problema és que he de fer tots aquests passo per poder entrar a Ubuntu. Algú té alguna idea de què puc fer per solucionar-ho?

Per acabar-ho d'adobar hi ha un tema que no em quadra gaire, i és que si se suposa que he actualitzat la versió d'ubuntu a 11.10 perquè en arrencar l'ordinador em surten els kernels de la versió 11.04 i no els de la nova?


Gràcies!
Astrid

---

### Post by vila-seca on 2011-10-31
Astrid,

Es possible que hi hagi un problema amb el controladors del vídeo. Tal com has fet abans des de consola inicia el GDM i prova d'instal·lar el controladors (privatius o lliures) a veure que passa.

ja ens indicaràs

---

### Post by ernestux on 2011-11-04
Hola,

Anava a obrir un problema igual:
En iniciar-se a mi se'm queda penjat en una fase posterior: "starting timidity alsa midi emulation" , i sempre aquesta.
He de fer Alt+F2  per entrar a mode consola, i he de fer "starx" perquè iniciï l'entorn gràfic.
He actualitzat paquets, també he re-instal.lat gdm , però segueix el problema.  No tinc cap controlador privatiu.
Ernest

---

### Post by diablessamariken on 2011-12-02
Hola

ja m'imagino que hi ha un problema amb els control·ladors però no sé com solucionar-ho. El meu grau de domini de l'Ubuntu és d'usuari bàsic de manera que fer segons quines coses amb la consola no puc. 

Tinc una targeta gràfica ATI MOBILITY RADEON X1300.

Amb aquesta informació em podeu ajudar una mica més? 

Moltes gràcies
Astrid

---

### Post by wgarcia on 2011-12-02
Si es tracta d'una actualització abortada, jo primer miraria que no hi hagin quedat coses per actualitzar o paquets trencats o mal configurats. 

Per això, des d'una terminal, les comandes següents poden ser d'utilitat per acabar de veure si queden coses per instal·lar/configurar:

```

sudo apt-get clean 
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

```

Un cop hagis fets aquestes comandes, també podria mirar-se el fitxer /etc/apt/sources.list a veure si tot apunta a la nova versió. Si vols adjunta'l al missatge.

---

### Post by kimet on 2011-12-05
Pots provar a deshabilitar ACPI desde el grub.
Editant (com a root) /etc/default/grub i canviant la línia: GRUB_CMDLINE_LINUX=""
per: GRUB_CMDLINE_LINUX=" acpi=off noapic nolapic" i actualitzant el grub:
```
sudo update grub
```

Salut

---

### Post by diablessamariken on 2011-12-13
Hola

gràcies per les noves aportacions. 

KIMET: Tinc una pregunta, de què em serveix deshabilitar ACPI?

WGARCIA: He fet totes les comandes que has llistat. I quan he entrar a mirar l'arxiu /etc/apt/sources.list m'ha donat el següent error:
```
astrid@astrid:~$  /etc/apt/sources.list
bash: /etc/apt/sources.list: S’ha denegat el permís
astrid@astrid:~$ sudo /etc/apt/sources.list
sudo: /etc/apt/sources.list: command not found

```

---

### Post by wgarcia on 2011-12-13
Per mirar "/etc/apt/sources.list" has de fer per exemple ALT-F2 i entrar 

```
gedit /etc/apt/sources.list
```

o simplement adjuntar aquest fitxer a una resposta i el podem mirar tots plegats.

De la forma que ho has entrat el sistema pensa que vols "executar" aquest fitxer, és a dir qué es un programa o llista d'instruccions, i et diu que no ho pot fer perquè no té permisos d'execució (i tot que li donessis permissos tampoc faria res perquè és un fitxer de text).

---

### Post by diablessamariken on 2011-12-15
Ja ho tinc! gràcies per explicar-me com fer-ho.

Aquí us copio el contingut de l'arxiu sources.list
______________________________________--

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security restricted main universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric universe main restricted multiverse
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main #Third party developers repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-updates universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by wgarcia on 2011-12-15
Aquest fitxer sembla correcte. Sisplau entra al sistema amb el procediment que descrius, obre una terminal, i entra el següent:

```
lspci -vnn | grep VGA
```

Engantxa en un missatge el que surt. Això mostrarà quina targeta gràfica tens.

---

### Post by diablessamariken on 2011-12-19
Aquesta és la targeta gràfica que tinc.

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M52 [Mobility Radeon X1300] [1002:7149] (prog-if 00 [VGA controller])

---

### Post by wgarcia on 2011-12-19
D'acord, mira si tens els controladors addicionals instal·lats. Per això clica a la icona de més a la dreta del plafó superior (la que és com una estrelleta) i aquí Paràmetres de sistema -> Maquinari -> Controladors addicionals. 

Mira si aquí t'ofereix un controlador per a la targeta gràfica i si el tens habilitat.

---

### Post by diablessamariken on 2011-12-20
Hola

he fet el que deies i em diu que:

AQUEST SISTEMA NO UTILITZA CONTROLADORS DE PROPIETAT

mal asuntu... oi?

---

### Post by wgarcia on 2011-12-20
No necessàriament, però hauries de provar d'instal·lar els controladors propietaris per veure si es resolen els problemes que menciones.

El pots instal·lar a través del Centre de Programari Ubuntu, obre'l i entra "Broadcom" a la finestra de búsqueda. Has d'instal·lar el que posa "Fitxers comuns".

---

### Post by wgarcia on 2011-12-21
Perdona pel missatge anterior, se m'han creuat els cables amb un altre fil. 

El que volia dir sí que es pot provar d'instal·lar controladors per a la teva targeta. No he tingut mai ordinadors amb targeta ATI, però hauria d'haver-hi algun controlador propietari que es pugui provar. 

Potser hi ha algú llegint que tingui alguna targeta semblant i pugui indicar quin és el controlador adequat.

---

