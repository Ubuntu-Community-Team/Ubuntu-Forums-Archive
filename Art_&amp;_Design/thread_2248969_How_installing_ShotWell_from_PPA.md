---
title: "How installing ShotWell from PPA"
date: 2014-10-18
forum: Art &amp; Design
---

### Post by ybecognee on 2014-10-18
hello 

I'm using Ubuntu 14.04 
To have the last version of Shotwell, I try the procedure proposed here: 
[http://doc.ubuntu-fr.org/shotwell](http://doc.ubuntu-fr.org/shotwell) 
 
sudo add-apt-repository ppa:yorba/ppa
sudo apt-get update
sudo apt-get install shotwell 

However, I get an error message during instalation: 

Des erreurs ont été rencontrées pendant l'exécution :
/var/cache/apt/archives/shotwell_0.20.1-1~trusty1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1) 

and I remain in version 0.18.0 :mad:

How do I install 0.20.1 from a ppa? 

Thank you :p

---

### Post by ibjsb4 on 2014-10-18
I just tried it and it installed without any problems.

Maybe you have a bad download.  Try removing the cache package and reinstall.
```
sudo rm /var/cache/apt/archives/shotwell_0.20.1-1~trusty1_amd64.deb
sudo apt-get install --reinstall shotwell
```

---

### Post by ybecognee on 2014-10-18
I did it, but the problem still here and I have the same message :

[FONT=courier new]yonnel@yo-McBkPro:~$ sudo rm /var/cache/apt/archives/shotwell_0.20.1-1~trusty1_amd64.deb
[sudo] password for yonnel: 
yonnel@yo-McBkPro:~$ sudo apt-get install --reinstall shotwell
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets suivants seront mis à jour :
  shotwell
1 mis à jour, 0 nouvellement installés, 0 à enlever et 1 non mis à jour.
Il est nécessaire de prendre 8,194 ko dans les archives.
Après cette opération, 35.0 Mo d'espace disque supplémentaires seront utilisés.
Réception de : 1 [http://ppa.launchpad.net/yorba/ppa/ubuntu/](http://ppa.launchpad.net/yorba/ppa/ubuntu/) trusty/main shotwell amd64 0.20.1-1~trusty1 [8,194 kB]
8,194 ko réceptionnés en 19s (420 ko/s)                                        
(Lecture de la base de données... 355054 fichiers et répertoires déjà installés.)
Préparation du décompactage de .../shotwell_0.20.1-1~trusty1_amd64.deb ...
Décompactage de shotwell (0.20.1-1~trusty1) sur (0.18.0-0ubuntu4.2) ...
dpkg: error processing archive /var/cache/apt/archives/shotwell_0.20.1-1~trusty1_amd64.deb (--unpack):
 tentative de remplacement de « /usr/share/applications/shotwell.desktop », qui appartient aussi au paquet shotwell-common 0.18.0-0ubuntu4.2
dpkg-deb : erreur : le sous-processus coller a été tué par le signal (Relais brisé (pipe))
Traitement déclenché pour  gnome-menus (3.10.1-0ubuntu2) ...
Traitement déclenché pour  desktop-file-utils (0.22-1ubuntu1) ...
Traitement déclenché pour  bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Traitement déclenché pour  mime-support (3.54ubuntu1) ...
Des erreurs ont été rencontrées pendant l'exécution :
 /var/cache/apt/archives/shotwell_0.20.1-1~trusty1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
yonnel@yo-McBkPro:~$ 


[/FONT]:(:(

---

### Post by ibjsb4 on 2014-10-18
Try this
```
sudo apt-get remove --purge shotwell-common
sudo apt-get install --reinstall shotwell
```

---

### Post by ybecognee on 2014-10-19
Wonderfull !

It is working now ! :eek:
Thank you very much ! =d>

What's was wrong ? :confused:

---

### Post by ian-weisser on 2014-10-19
> **ybecognee said:**
> [FONT=courier new]tentative de remplacement de « /usr/share/applications/shotwell.desktop », qui appartient aussi au paquet shotwell-common 0.18.0-0ubuntu4.2[/FONT]

That was the problem.
Each file in your system can be provided by a maximum of one package.
If two packages provide the same file, they *conflict*. Only one of the packages can be installed on your system.
You, the human, much choose between the packages.

This occurs most often with PPAs and other non-Ubuntu software.
Different packagers include different files in their package.

---

### Post by ibjsb4 on 2014-10-19
As ian-weisser said, a package conflict.

Et ne pas oublier de remercier google translate :D

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Sasha_Aderolop on 2014-11-05
I use the next wat to install:
Open the terminal and run the following commands

 sudo add-apt-repository ppa:yorba/ppa
 sudo apt-get update
 sudo apt-get install shotwell
All OK.

---

