---
title: "Llista fonts de programari bloquejada"
date: 2009-12-28
forum: Catalan Team
---

### Post by Pepe_Prats on 2009-12-28
Em surt aquest missatge:



> No es pot inicialitzar la informació dels paquets

S'ha produït un error irresoluble mentre s'inicialitzava la informació de paquets.

Informeu d'aquest error de l'update-manager i incloeu el missatge següent:

'E:S'està obrint /etc/apt/sources.list.d/medibuntu.list - ifstream::ifstream (13: Permission denied), E:No s'ha pogut llegir la llista de les fonts.'
:confused:

Puc actualitzar, pero només desde el synaptic...si qualcú hem diu per on començo li ho agraïria moltíssim

---

### Post by papapep on 2009-12-28
> Em surt aquest missatge:

Et surt això, però en fer què?? no ho expliques.

> Puc actualitzar, pero només desde el synaptic...si qualcú hem diu per on començo li ho agraïria moltíssim 

Pel que dius, entenc que fent un:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

et funciona tot correctament?

---

### Post by Pepe_Prats on 2009-12-29
Soory per la novatada:redface:. em surt quan miro de posar en marxa el gestor d'actualitzacions (update manager?) desde la icona.

Quan introdueixo aquesta ordre que em dius  desde un terminal em surt tota la llista de paquets i finalment..

> (...)
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Sources
S'han obtingut 24,5kB en 1s (17,4kB/s)
S'està llegint la llista de paquets... Fet

E: S'està obrint /etc/apt/sources.list.d/medibuntu.list - ifstream::ifstream (13: Permission denied)
Segmentation fault
pepe@pepe-laptop:~$ 
Gracies eh ;-)

---

### Post by sordoman on 2009-12-31
Hola Pepe

Em sembla que tens un problema de permisos del fitxer.

mira primer de fer
```

ls -l /etc/apt/sources.list.d/medibuntu.list

```

a veure que posa; teòricament aquest arxiu hauria de ser propietat de "root" amb perisos de lecura y escriptura vaja, el meu surt això

```

-rw-r--r-- 1 root root 273 2009-12-29 21:32 /etc/apt/sources.list.d/medibuntu.list

```

si no et surt aixís, canvia-ho

sort):P

---

### Post by falsospam on 2010-01-02
A mi hem pasa fent "sudo aptitude update && sudo aptitude safe-upgrade" que hem diu :
S'està escrivint la informació d'estat estesa... Fet
Ign [http://blognux.free.fr](http://blognux.free.fr) hardy Release.gpg                          
Obté:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                 
Prem [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-ca    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-ca
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic Release.gpg                  
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic/main Translation-ca          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-ca                   
Prem [http://repository.cairo-dock.org](http://repository.cairo-dock.org) karmic Release.gpg              
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) karmic/cairo-dock Translation-ca 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-ca
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-ca
Prem [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release               
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic/restricted Translation-ca    
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic/universe Translation-ca      
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic/multiverse Translation-ca    
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic-updates Release.gpg          
Ign [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic-updates/main Translation-ca   
Ign [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic-updates/restricted Translation-ca
Ign [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic-updates/universe Translation-ca
Ign [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic-updates/multiverse Translation-ca
Prem [http://repository.cairo-dock.org](http://repository.cairo-dock.org) karmic Release                  
Obté:2 [http://dl.google.com](http://dl.google.com) stable Release [2540B]                    
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic Release                      
Ign [http://blognux.free.fr](http://blognux.free.fr) hardy/main Translation-ca                  
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic-updates Release              
Prem [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages         
Prem [http://repository.cairo-dock.org](http://repository.cairo-dock.org) karmic/cairo-dock Packages      
Obté:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [873B]               
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic/main Packages                
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic/restricted Packages          
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic/main Sources                 
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic/restricted Sources           
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic/universe Packages            
Prem [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages   
Prem [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources          
Prem [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources    
Prem [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages     
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic/universe Sources             
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic/multiverse Packages          
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic/multiverse Sources           
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic-updates/main Packages        
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic-updates/restricted Packages  
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic-updates/main Sources         
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic-updates/restricted Sources   
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic-updates/universe Packages    
Prem [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources      
Prem [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages   
Prem [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources    
Ign [http://blognux.free.fr](http://blognux.free.fr) hardy Release                              
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic-updates/universe Sources     
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic-updates/multiverse Packages
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) karmic-updates/multiverse Sources
Ign [http://blognux.free.fr](http://blognux.free.fr) hardy/main Packages
Ign [http://blognux.free.fr](http://blognux.free.fr) hardy/main Packages
Err [http://blognux.free.fr](http://blognux.free.fr) hardy/main Packages
  404  Not Found
S'han obtingut 3602B en 6s (589B/s)                                   
S'està llegint la llista de paquets... Fet           

I fent "ls -l /etc/apt/sources.list.d/medibuntu.list" :

ls: no s&#8217;ha pogut accedir a /etc/apt/sources.list.d/medibuntu.list: No such file or directory

Pepe: que potser tens instalada una versio de 64 Bits?

---

### Post by kimet on 2010-01-02
Aixó et dona error:
Err [http://blognux.free.fr](http://blognux.free.fr) hardy/main Packages
Si vas a aquesta direcció veuras que ha camviar d'adressa.
Esborrala a veure que passa.
Hi cert risc en afegir font de programari que no sabem si son confiables, jo deixaria només els repositoris oficials...;)

---

### Post by falsospam on 2010-01-02
> **kimet said:**
> Aixó et dona error:
Err [http://blognux.free.fr](http://blognux.free.fr) hardy/main Packages
Si vas a aquesta direcció veuras que ha camviar d'adressa.
Esborrala a veure que passa.
Hi cert risc en afegir font de programari que no sabem si son confiables, jo deixaria només els repositoris oficials...;)

Si ho se pero es que no podia instalar la Webcam, el repositori de [http://blognux.free.fr](http://blognux.free.fr) ha cambiat pero tampoc esta disponible, hem fa por de esborra-lo i que en algun proces de neteja m'elimini la camara .. No se si el puc esborrar i quedar-me tranquil. De fet tinc altres problemes com aquest ... Tinc una impresora Dell 720 que de fet es una blanca de Lexmark i amb la versió anterior tenia els drivers de Z600, pero ara no hi es el repositori i no la puc fer funcionar amb la nova instalació del Kubuntu Karmic Koala 9.10..... 

De vegades tenim que fer el que no hauriem de fer i jugarnos-la...
Potser massa vegades :)

---

### Post by kimet on 2010-01-02
Amb: aptitude safe-upgrade veuras els paquets que es desinstal.len cada cop que vulguis actualitzar. De totes maneres només es desinstal.len els que han quedat "orfes, llibreries que eren dependencia d'un programa ja esborrat. No crec que t'esborri res relacionat amb la webcam.
En relació a la impressora hauries d'obrir un nou fil, a veure si algú en sap alguna cosa.
Salut.

---

### Post by Pepe_Prats on 2010-01-02
Sordoman: em surt

> pepe@pepe-laptop:~$ sudo ls -l /etc/apt/sources/list.d/medibuntu.list
[sudo] password for pepe: 
ls: no s’ha pogut accedir a /etc/apt/sources/list.d/medibuntu.list: No such file or directory
pepe@pepe-laptop:~$ 


I no, falsospam la versio es i386

Es possible que sia una cosa de permisos perque vaig tenir instal.lat un "bastille":confused:

---

### Post by papapep on 2010-01-02
> pepe@pepe-laptop:~$ sudo ls -l /etc/apt/**sources/list.d**/medibuntu.list
[sudo] password for pepe:
ls: no s&#8217;ha pogut accedir a /etc/apt/sources/list.d/medibuntu.list: No such file or directory

No has posat bé la ordre. La correcta és:

```
sudo ls -la /etc/apt/**sources.list.d**/medibuntu.list

```

Torna-ho a provar amb el camí correcte. :)

---

### Post by Pepe_Prats on 2010-01-04
:oops:> sudo ls -la /etc/apt/sources.list.d/medibuntu.list
-rw-r----- 1 root root 271 2009-12-15 16:16 /etc/apt/sources.list.d/medibuntu.list
Ara sí,!! per aquesta banda cap problema i..ara...[-o<

---

### Post by papapep on 2010-01-04
Fes un:

```
sudo chmod 644 /etc/apt/sources.list.d/medibuntu.list
```

i torna a provar a actualitzar la llista de paquets, a veure si funciona.

---

### Post by Pepe_Prats on 2010-01-04
=D>Siiiiiiiiiiii!!!!!!
Gracies company!!!!

---

