---
title: "Cant install Certain packages"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by very_japi on 2008-01-18
I kinda fooled around on my sources.list file to get Desktop Effects to work on my laptop. Well ... Now i have all the effects one could ever wish for but when y tried to install the FLash player (non-free) i got struck by a surprise:

... PACKAGE IS NOT THERE!

Flash Package's name is somethign like flashplugin-nonfree or something like that, but when i search  for "flash" in synaptic there's nothing even remotely similar.

Also tried installing directly from firefox and i get this "You have held brocken packages" error. 

So my guess is that deleted some repository or something, so i tried to reset my sources.list file using that autamated page Ubuntu has ... and well... i still get the same errors.

Basically the problem is:flashplugin-nonfree is nowhere to be found.

This is my sources.list

```

## Uncomment the following two lines to fetch updated software from the network
deb http://tezcatl.fciencias.unam.mx/ubuntu/ gutsy main restricted
deb-src http://tezcatl.fciencias.unam.mx/ubuntu/ gutsy restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://tezcatl.fciencias.unam.mx/ubuntu/ gutsy-updates restricted main multiverse universe
deb-src http://tezcatl.fciencias.unam.mx/ubuntu/ gutsy-updates restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://tezcatl.fciencias.unam.mx/ubuntu/ gutsy universe

deb http://tezcatl.fciencias.unam.mx/ubuntu/ gutsy-security main restricted
deb-src http://tezcatl.fciencias.unam.mx/ubuntu/ gutsy-security restricted main universe #Added by software-properties

deb http://tezcatl.fciencias.unam.mx/ubuntu/ gutsy-security universe

deb http://tezcatl.fciencias.unam.mx/ubuntu/ gutsy multiverse


deb http://security.ubuntu.com/ubuntu/ gutsy-security restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security restricted main multiverse universe #Added by software-properties

deb http://tezcatl.fciencias.unam.mx/ubuntu/ gutsy-proposed restricted main multiverse universe
deb-src http://tezcatl.fciencias.unam.mx/ubuntu/ gutsy-proposed restricted main multiverse universe #Added by software-properties
deb http://tezcatl.fciencias.unam.mx/ubuntu/ gutsy-backports restricted main multiverse universe
deb-src http://tezcatl.fciencias.unam.mx/ubuntu/ gutsy-backports restricted main multiverse universe #Added by software-properties

```
This is the output of sudo apt-get update

```

Get:1 http://tezcatl.fciencias.unam.mx gutsy Release.gpg [191B]
Ign http://tezcatl.fciencias.unam.mx gutsy/main Translation-en_US              
Ign http://tezcatl.fciencias.unam.mx gutsy/restricted Translation-en_US        
Ign http://tezcatl.fciencias.unam.mx gutsy/universe Translation-en_US          
Ign http://tezcatl.fciencias.unam.mx gutsy/multiverse Translation-en_US
Get:2 http://tezcatl.fciencias.unam.mx gutsy-updates Release.gpg [191B]
Ign http://tezcatl.fciencias.unam.mx gutsy-updates/restricted Translation-en_US
Ign http://tezcatl.fciencias.unam.mx gutsy-updates/main Translation-en_US
Ign http://tezcatl.fciencias.unam.mx gutsy-updates/multiverse Translation-en_US
Ign http://tezcatl.fciencias.unam.mx gutsy-updates/universe Translation-en_US
Get:3 http://tezcatl.fciencias.unam.mx gutsy-security Release.gpg [191B]
Ign http://tezcatl.fciencias.unam.mx gutsy-security/main Translation-en_US  
Get:4 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US  
Ign http://tezcatl.fciencias.unam.mx gutsy-security/restricted Translation-en_US
Ign http://tezcatl.fciencias.unam.mx gutsy-security/universe Translation-en_US
Get:5 http://tezcatl.fciencias.unam.mx gutsy-proposed Release.gpg [191B]
Get:6 http://packages.medibuntu.org gutsy Release.gpg [189B]                
Ign http://tezcatl.fciencias.unam.mx gutsy-proposed/restricted Translation-en_US
Ign http://tezcatl.fciencias.unam.mx gutsy-proposed/main Translation-en_US
Ign http://tezcatl.fciencias.unam.mx gutsy-proposed/multiverse Translation-en_US
Ign http://tezcatl.fciencias.unam.mx gutsy-proposed/universe Translation-en_US
Get:7 http://tezcatl.fciencias.unam.mx gutsy-backports Release.gpg [191B]
Ign http://tezcatl.fciencias.unam.mx gutsy-backports/restricted Translation-en_US
Ign http://tezcatl.fciencias.unam.mx gutsy-backports/main Translation-en_US
Ign http://tezcatl.fciencias.unam.mx gutsy-backports/multiverse Translation-en_US
Ign http://tezcatl.fciencias.unam.mx gutsy-backports/universe Translation-en_US
Hit http://tezcatl.fciencias.unam.mx gutsy Release
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release                          
Hit http://tezcatl.fciencias.unam.mx gutsy-updates Release                     
Hit http://tezcatl.fciencias.unam.mx gutsy-security Release                    
Hit http://tezcatl.fciencias.unam.mx gutsy-proposed Release                    
Hit http://tezcatl.fciencias.unam.mx gutsy-backports Release                   
Hit http://tezcatl.fciencias.unam.mx gutsy/main Packages                       
Hit http://tezcatl.fciencias.unam.mx gutsy/restricted Packages       
Hit http://tezcatl.fciencias.unam.mx gutsy/restricted Sources        
Hit http://tezcatl.fciencias.unam.mx gutsy/main Sources              
Hit http://tezcatl.fciencias.unam.mx gutsy/multiverse Sources        
Hit http://tezcatl.fciencias.unam.mx gutsy/universe Sources          
Hit http://security.ubuntu.com gutsy-security/restricted Packages    
Hit http://tezcatl.fciencias.unam.mx gutsy/universe Packages         
Hit http://tezcatl.fciencias.unam.mx gutsy/multiverse Packages
Hit http://tezcatl.fciencias.unam.mx gutsy-updates/restricted Packages
Hit http://tezcatl.fciencias.unam.mx gutsy-updates/main Packages     
Hit http://tezcatl.fciencias.unam.mx gutsy-updates/multiverse Packages
Hit http://tezcatl.fciencias.unam.mx gutsy-updates/universe Packages 
Hit http://tezcatl.fciencias.unam.mx gutsy-updates/restricted Sources
Hit http://tezcatl.fciencias.unam.mx gutsy-updates/main Sources      
Ign http://packages.medibuntu.org gutsy/free Translation-en_US       
Hit http://tezcatl.fciencias.unam.mx gutsy-updates/multiverse Sources
Hit http://tezcatl.fciencias.unam.mx gutsy-updates/universe Sources
Hit http://security.ubuntu.com gutsy-security/main Packages          
Hit http://security.ubuntu.com gutsy-security/multiverse Packages    
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://tezcatl.fciencias.unam.mx gutsy-security/main Packages    
Hit http://tezcatl.fciencias.unam.mx gutsy-security/restricted Packages
Hit http://tezcatl.fciencias.unam.mx gutsy-security/restricted Sources
Hit http://tezcatl.fciencias.unam.mx gutsy-security/main Sources     
Hit http://tezcatl.fciencias.unam.mx gutsy-security/universe Sources 
Hit http://tezcatl.fciencias.unam.mx gutsy-security/universe Packages
Hit http://tezcatl.fciencias.unam.mx gutsy-proposed/restricted Packages
Hit http://tezcatl.fciencias.unam.mx gutsy-proposed/main Packages    
Hit http://tezcatl.fciencias.unam.mx gutsy-proposed/multiverse Packages
Hit http://tezcatl.fciencias.unam.mx gutsy-proposed/universe Packages
Hit http://tezcatl.fciencias.unam.mx gutsy-proposed/restricted Sources
Hit http://tezcatl.fciencias.unam.mx gutsy-proposed/main Sources
Hit http://tezcatl.fciencias.unam.mx gutsy-proposed/multiverse Sources
Hit http://tezcatl.fciencias.unam.mx gutsy-proposed/universe Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Sources     
Hit http://security.ubuntu.com gutsy-security/universe Sources       
Hit http://tezcatl.fciencias.unam.mx gutsy-backports/restricted Packages
Hit http://tezcatl.fciencias.unam.mx gutsy-backports/main Packages
Hit http://tezcatl.fciencias.unam.mx gutsy-backports/multiverse Packages
Hit http://tezcatl.fciencias.unam.mx gutsy-backports/universe Packages
Hit http://tezcatl.fciencias.unam.mx gutsy-backports/restricted Sources
Hit http://tezcatl.fciencias.unam.mx gutsy-backports/main Sources
Hit http://tezcatl.fciencias.unam.mx gutsy-backports/multiverse Sources
Hit http://tezcatl.fciencias.unam.mx gutsy-backports/universe Sources
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_US
Hit http://packages.medibuntu.org gutsy Release
Ign http://packages.medibuntu.org gutsy/free Packages
Ign http://packages.medibuntu.org gutsy/non-free Packages
Ign http://packages.medibuntu.org gutsy/free Sources
Ign http://packages.medibuntu.org gutsy/non-free Sources
Hit http://packages.medibuntu.org gutsy/free Packages                          
Hit http://packages.medibuntu.org gutsy/non-free Packages                      
Hit http://packages.medibuntu.org gutsy/free Sources                           
Hit http://packages.medibuntu.org gutsy/non-free Sources                       
Fetched 7B in 8s (1B/s)                                                        
Reading package lists... Done

```

Ths are my enabled repositories:
[LIST]
[*]main
[*]universe
[*]restricted
[*]multiverse
[*]medibuntu free non-free
[*]gutsy-security
[*]gutsy-updates
[/LIST]

Any ideas?

---

### Post by eolson on 2008-01-18
Do you have a directory

  /home/yourusername/.mozilla/plugins

we can install it by hand.

If you don't,  make it and copy the file

   libflashplayer.so

into it.  That should do it.

---

### Post by very_japi on 2008-01-18
Ok, yeah... tere's a work around...  bet there's a ton of them, but the real problem here is that many libraries, and packages are missing...  and i would like to have them back

---

### Post by eolson on 2008-01-18
search for
  adobe

in synaptic and see what happens

---

### Post by very_japi on 2008-01-18
That got me a bit closer, i found the package (although it doesn't appear on the full list when i look for it manually)

but i get:

flashplugin-nonfree:
 Depends: nspluginwrapper but it is not going to be installed

when i look for nspluginwrapper manually i do FIND IT. But f i try to install it i get 

nspluginwrapper:
 Depends: ia32-libs but it is not going to be installed
 Depends: lib32gcc1 but it is not going to be installed
 Depends: libc6-i386 but it is not going to be installed

The problem seems to be that Synpactic s not automatically resolving dependencies now, cuz when i llok for ia32-libs the package s there, but synaptic does not resolve dependencies.

---

