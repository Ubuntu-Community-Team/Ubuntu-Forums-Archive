---
title: "problema amb &quot;afegeix/elimina&quot;"
date: 2009-02-04
forum: Catalan Team
---

### Post by miquelet on 2009-02-04
Tinc instal·lat al portàtil l'ubuntu 8.10.  Des de fa un quants dies i no sé per quina raó, quan intento fer anar l'aplicació "afegeix/elimina", el missatge que em dóna és "No hi ha cap aplicació coincident disponible".  Tinc marcada l'opció "Totes les aplicacions disponibles".  L'única cosa "diferent" que he fet els darrers dies ha estat instal·lar-me l'escriptori KDE, per provar-lo (habitualment faig anar el gnome, que conservo instal·lat).  Pot tenir res a veure amb el meu problema.  Com el puc solucionar?  Gràcies.

---

### Post by papapep on 2009-02-07
No tinc idea del teu problema, però jo provaria a fer:

```
sudo aptitude update && aptitude safe-upgrade
```

a veure si es posa a to.

Si així tampoc funciona, també pots provar a verificar si tens dependències trencades a la base de paquets:

```
sudo apt-get -f install
```

això t'hauria d'arreglar el problema si fos aquest.

---

### Post by miquelet on 2009-02-09
He fet el que em recomanaves i no m'ha funcionat.

---

### Post by papapep on 2009-02-09
I cap de les ordres ha mostrat cap missatge indicatiu d'error que ens pugui donar alguna pista?

---

### Post by miquelet on 2009-02-09
Quan he fet: 

sudo aptitude update && aptitude safe-upgrade

Al final apareix això:

E: No es pot resoldre el fixter de blocat /var/lib/dpkg/lock - open (13 Permission denied)

E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


Llavors què hi he de posar?  Perquè quan li dic que sí (y) m'apareixen tot de “y” a cada línia.

---

### Post by papapep on 2009-02-09
prova a fer:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by oriolsbd on 2009-02-10
Quan has executat la comanda que t'ha dit el Papapep, tenies obert el Synaptic, o l'"Afegeix/Elimina"? També pot afectar el "Gestor d'actualitzacions" just en el moment que està cercant actualitzacions o realitzant-les. No hi pot haver dos programes alhora que accedeixin a la BDD de paquets instal·lats. Torna a executar les comandes que t'ha dit sense tenir-los oberts.

Salut!

---

### Post by miquelet on 2009-02-10
He provat tot el que em recomanaves Papapep i no he resolt res.  D'altra banda, quan he executat al terminal les ordres no tenia el synaptic ni l'afegeix/elimina oberts.  Alguna pista?  Salut i gràcies.

---

### Post by papapep on 2009-02-10
Només tens un usuari creat a l'ordinador (a banda de root, clar)?

Executa aquesta ordre, i enganxa aquí el que et mostri:

```
ls -la /var/lib/dpkg
```

---

### Post by miquelet on 2009-02-11
Només tinc un usuari.  He executat el que em deies Papapep i m'ha sortit això:

total 6288
drwxr-xr-x  7 root root    4096 2009-02-10 23:35 .
drwxr-xr-x 52 root root    4096 2008-12-29 23:09 ..
drwxr-xr-x  2 root root    4096 2009-01-30 18:10 alternatives
-rw-r--r--  1 root root 1504150 2009-02-10 23:35 available
-rw-r--r--  1 root root 1504150 2009-02-10 23:35 available-old
-rw-r--r--  1 root root       8 2008-04-22 19:49 cmethopt
-rw-r--r--  1 root root     258 2008-11-03 15:39 diversions
-rw-r--r--  1 root root     186 2008-11-03 15:30 diversions-old
drwxr-xr-x  2 root root  270336 2009-02-10 23:35 info
-rw-r-----  1 root root       0 2009-02-10 23:35 lock
drwxr-xr-x  2 root root    4096 2008-02-13 02:50 parts
-rw-r--r--  1 root root      65 2008-04-22 20:01 statoverride
-rw-r--r--  1 root root      30 2008-04-22 19:59 statoverride-old
-rw-r--r--  1 root root 1540935 2009-02-10 23:35 status
-rw-r--r--  1 root root 1540933 2009-02-10 23:35 status-old
drwxr-xr-x  2 root root    4096 2009-02-09 22:13 triggers
drwxr-xr-x  2 root root    4096 2009-02-10 23:35 updates


Salut i gràcies!

---

### Post by oriolsbd on 2009-02-11
Hola, en el teu post, dius que has fet:
```
sudo aptitude update && aptitude safe-upgrade
```

El Papapep t'havia dit el següent:
```
sudo aptitude update && sudo aptitude safe-upgrade
```

És a dir, el segon "aptitude" també amb "sudo". Ha estat només una errada a l'escriure el post, o realment no havies fet "sudo" en el "safe-upgrade"? Si no has fet el "safe-upgrade" amb "sudo", per això no et funcionava. Si no, caldrà seguir mirant...

---

### Post by miquelet on 2009-02-11
Sí que l'havia fet (l'he tornat a fer per si de cas) i no s'ha arreglat el problema.  Caldrà seguir buscant, doncs.  Salut!

---

### Post by papapep on 2009-02-11
Següent tentativa:

```
sudo dpkg --configure -a
```

---

### Post by miquelet on 2009-02-11
Temptativa fallida.

---

### Post by papapep on 2009-02-11
Estaria bé poder veure la sortida de les ordres (els missatges). A vegades hi ha cosetes que ens podrien donar pistes. Si enganxes el resultat aquí, t'ho agrairia.

---

### Post by miquelet on 2009-02-11
Sento no poder donar més pistes.  El que em demanaves:  ha anat així:

miquel@miquel-laptop:~$ sudo dpkg --configure -a
[sudo] password for miquel: 
miquel@miquel-laptop:~$ 

I això és tot!  No puc donar més informació.

---

### Post by papapep on 2009-02-11
No pots donar més del que hi ha :-)

Però, has provat a fer després un:

```
sudo aptitude update
```

i, si aquesta no dóna cap missatge d'error (enganxa el que faci), un:

```
sudo aptitude safe-upgrade
```

?

---

### Post by miquelet on 2009-02-11
He executat les dues ordres que em deies i en cap cas no m'ha donat cap missatge d'error.  I segueix sense funcionar.  Buf!

---

### Post by papapep on 2009-02-11
_Enganxa la sortida que generen_, si us plau.

---

### Post by miquelet on 2009-02-12
Quan executo la primera ordre, genera això:

miquel@miquel-laptop:~$ sudo aptitude update

[sudo] password for miquel: 

Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release.gpg

Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-ca

Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-ca

Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy Release   

Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Packages

Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Packages

Err cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Packages

  Si us plau, useu apt-cdrom per a que aquest CD sigui reconegut per APT. No pot emprar-se apt-get update per afegir-ne de nous

Err cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Packages

  Si us plau, useu apt-cdrom per a que aquest CD sigui reconegut per APT. No pot emprar-se apt-get update per afegir-ne de nous

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid Release.gpg                          

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/main Translation-ca                  

Prem [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             

Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-ca                   

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/restricted Translation-ca            

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/universe Translation-ca       

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/multiverse Translation-ca     

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates Release.gpg           

Prem [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   

Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-ca            

Prem [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 

Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-ca      

Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-ca 

Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-ca

Prem [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/main Translation-ca   

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/restricted Translation-ca

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/universe Translation-ca

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/multiverse Translation-ca

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports Release.gpg

Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports/main Translation-ca

Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports/restricted Translation-ca

Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports/universe Translation-ca     

Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports/multiverse Translation-ca   

Prem [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        

Prem [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                  

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-backports Release.gpg            

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed Release.gpg          

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed/restricted Translation-ca

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed/main Translation-ca  

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed/multiverse Translation-ca

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed/universe Translation-ca

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid Release                       

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates Release               

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports Release             

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-backports Release                       

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed Release                     

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/main Packages                        

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/restricted Packages                  

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/main Sources    

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/restricted Sources                   

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/universe Packages                    

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/universe Sources

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/multiverse Packages

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/multiverse Sources

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/main Packages                

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/restricted Packages   

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/main Sources

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/restricted Sources    

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/universe Packages     

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/universe Sources

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/multiverse Packages

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/multiverse Sources

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports/main Packages

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports/restricted Packages

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports/universe Packages

Prem [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-backports/multiverse Packages

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-backports/main Sources           

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-backports/restricted Sources     

Prem [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages    

Prem [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources           

Prem [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources     

Prem [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages      

Prem [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-backports/universe Sources

Prem [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages

Prem [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) hardy-backports/multiverse Sources

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed/restricted Packages

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed/main Packages

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed/multiverse Packages

Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-proposed/universe Packages

S'està llegint la llista de paquets... Fet 



miquel@miquel-laptop:~$ 


I quan executo la segona, això:

miquel@miquel-laptop:~$ sudo aptitude safe-upgrade

S'està llegint la llista de paquets... Fet 

S'està construint l'arbre de dependències       

S'està llegint la informació d'estat... Fet

S'està llegint la informació d'estat estesa      

S'estan inicialitzant els estats dels paquets... Fet

No s'instal·larà, actualitzarà o suprimirà cap paquet.

0 paquets a actualitzar, 0 a instal·lar, 0 a suprimir i 0 a no actualitzar.

Es necessita obtenir 0B d'arxius. Després del desempaquetat s'utilitzaran 0B.

S'està llegint la llista de paquets... Fet 

S'està construint l'arbre de dependències       

S'està llegint la informació d'estat... Fet

S'està llegint la informació d'estat estesa       

S'estan inicialitzant els estats dels paquets... Fet



miquel@miquel-laptop:~$ 



Ara me n'adono que SÍ que donava un error.  Ho sento.  Salut i gràcies.

---

### Post by papapep on 2009-02-12
Cap problema. Enganxa el contingut del fitxer /etc/apt/sources.list:

```
cat /etc/apt/sources.list
```

---

### Post by miquelet on 2009-02-12
Aquí va:

miquel@miquel-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse


Fins la pròxima.

---

### Post by CarlesOriol on 2009-02-14
Elimina totes les linies on hi ha escrit Hardy.

---

### Post by miquelet on 2009-02-15
Suposo que l'última resposta l'he d'entendre com que he d'eliminar totes les línies de l'arxiu sources.list on apareix la paraula "hardy".  El cas és que quan ho intento fer (obrint l'arxiu i eliminant-les) em diu que no tinc tots els permisos i no em permet desar els canvis.  O bé és que no sé fer-ho, o bé és que no es tracta d'això. Em podeu dir on cometo l'error?  Gràcies.

---

### Post by oriolsbd on 2009-02-16
El fitxer sources.list és un fitxer d'administració, amb permisos només per a root. Per tant, per editar-lo ho has de fer amb "sudo". Per exemple:
```
sudo gedit /etc/apt/sources.list
```
Salut!

---

### Post by miquelet on 2009-02-16
He eliminat totes les línies on apareix "hardy", i el problema continua sense solucionar-se.  (Però he après a fer una cosa nova!).  Seguiré investigant.  Salut i gràcies!

---

