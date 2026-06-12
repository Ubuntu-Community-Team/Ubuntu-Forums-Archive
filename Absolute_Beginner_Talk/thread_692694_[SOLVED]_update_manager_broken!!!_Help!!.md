---
title: "[SOLVED] update manager broken!!! Help!!"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by shadowber on 2008-02-10
Ok when I start the update manager (it shows there are updates ready by the orange button) it gives me this message "Software index is broken It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first." I have no idea what to do and would be very grateful for any help.
attached is a screen shot of the error message...

---

### Post by spiderbatdad on 2008-02-10
Applications>>Accessories>>Terminal. Enter:```
sudo apt-get install -f
```

---

### Post by Rocket2DMn on 2008-02-10
Try
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install *yourpackagehere*
```

---

### Post by shadowber on 2008-02-10
> **spiderbatdad said:**
> Applications>>Accessories>>Terminal. Enter:```
sudo apt-get install -f
```

I tried that before i posted, and I got this

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libfreebob0 libjack0 classpath-gtkpeer classpath-common cacao classpath
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firefox
Suggested packages:
  latex-xft-fonts
The following packages will be upgraded:
  firefox
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/9189kB of archives.
After unpacking, 28.7kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 110984 files and directories currently installed.)
Preparing to replace firefox 2.0.0.11+2nobinonly-0ubuntu0.7.10 (using .../firefox_2.0.0.12+2nobinonly+2-0ubuntu0.7.10_i386.deb) ...
Unpacking replacement firefox ...
dpkg: error processing /var/cache/apt/archives/firefox_2.0.0.12+2nobinonly+2-0ubuntu0.7.10_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Please restart any running Firefoxes, or you will experience problems.
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_2.0.0.12+2nobinonly+2-0ubuntu0.7.10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1"

and the same problem is still there...

---

### Post by shadowber on 2008-02-10
> **Rocket2DMn said:**
> Try
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install *yourpackagehere*
```

Not sure what you are telling me to do... I tried what you wrote (not sure what to write fot the last line...) but it is still broken.

again I don't care about this particular update, the whole update manager is broken...

---

### Post by PmDematagoda on 2008-02-10
Execute:-
```
sudo apt-get update
```
post the output you get.

---

### Post by shadowber on 2008-02-10
> **PmDematagoda said:**
> Execute:-
```
sudo apt-get update
```
post the output you get.

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main Translation-en_CA                  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/restricted Translation-en_CA            
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/universe Translation-en_CA              
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/multiverse Translation-en_CA            
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main Translation-en_CA          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/restricted Translation-en_CA    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/universe Translation-en_CA      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_CA    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy Release                                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates Release                         
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_CA                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main Sources                            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/restricted Sources                      
Get:4 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_CA               
Get:5 [http://buildbot.no-ip.org](http://buildbot.no-ip.org) gutsy Release.gpg [189B]                       
Ign [http://buildbot.no-ip.org](http://buildbot.no-ip.org) gutsy/main Translation-en_CA                     
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_CA           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/universe Packages                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/universe Sources                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/multiverse Packages                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/multiverse Sources                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main Packages                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/restricted Packages             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main Sources                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/restricted Sources              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/universe Packages               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_CA             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/universe Sources                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/multiverse Packages             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/multiverse Sources              
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_CA     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Hit [http://buildbot.no-ip.org](http://buildbot.no-ip.org) gutsy Release                                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages          
Ign [http://buildbot.no-ip.org](http://buildbot.no-ip.org) gutsy/main Packages                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources     
Hit [http://buildbot.no-ip.org](http://buildbot.no-ip.org) gutsy/main Sources                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://buildbot.no-ip.org](http://buildbot.no-ip.org) gutsy/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Fetched 6B in 0s (8B/s)  
Reading package lists... Done

---

### Post by Rocket2DMn on 2008-02-10
OK, so try and get back to doing whatever it is you were doing.  Does it work now?  Otherwise try
```
sudo apt-get upgrade
```

---

### Post by shadowber on 2008-02-10
> **Rocket2DMn said:**
> OK, so try and get back to doing whatever it is you were doing.  Does it work now?  Otherwise try
```
sudo apt-get upgrade
```

no the update manager still does not work, and is still giving me the same erroe message....

when I tried the above, I got

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  firefox-gnome-support: Depends: firefox (= 2.0.0.12+2nobinonly+2-0ubuntu0.7.10) but 2.0.0.11+2nobinonly-0ubuntu0.7.10 is installed
E: Unmet dependencies. Try using -f."

and still does not work.

---

### Post by PmDematagoda on 2008-02-10
Do:-
```
sudo apt-get install -f
```
and
```
sudo dpkg --configure -a
```
Post the outputs of both commands.

---

### Post by Rocket2DMn on 2008-02-10
Do
```
sudo apt-get autoremove
sudo rm /var/cache/apt/archives/firefox_2.0.0.12+2nobinonl y+2-0ubuntu0.7.10_i386.deb
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```
(this will delete the downloaded update since it seems to be corrupted, as well as clean out your cache)
Make sure firefox is closed when you do "upgrade" please.

---

### Post by shadowber on 2008-02-10
> **PmDematagoda said:**
> Do:-
```
sudo apt-get install -f
```
and
```
sudo dpkg --configure -a
```
Post the outputs of both commands.

from -f i got

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libfreebob0 libjack0 classpath-gtkpeer classpath-common cacao classpath
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firefox
Suggested packages:
  latex-xft-fonts
The following packages will be upgraded:
  firefox
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/9189kB of archives.
After unpacking, 28.7kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 110984 files and directories currently installed.)
Preparing to replace firefox 2.0.0.11+2nobinonly-0ubuntu0.7.10 (using .../firefox_2.0.0.12+2nobinonly+2-0ubuntu0.7.10_i386.deb) ...
Unpacking replacement firefox ...
dpkg: error processing /var/cache/apt/archives/firefox_2.0.0.12+2nobinonly+2-0ubuntu0.7.10_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Please restart any running Firefoxes, or you will experience problems.
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_2.0.0.12+2nobinonly+2-0ubuntu0.7.10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)"

from -a I got

"dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox (= 2.0.0.12+2nobinonly+2-0ubuntu0.7.10); however:
  Version of firefox on system is 2.0.0.11+2nobinonly-0ubuntu0.7.10.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 firefox-gnome-support"

---

### Post by shadowber on 2008-02-10
> **Rocket2DMn said:**
> Do
```
sudo apt-get autoremove
sudo rm /var/cache/apt/archives/firefox_2.0.0.12+2nobinonl y+2-0ubuntu0.7.10_i386.deb
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```
(this will delete the downloaded update since it seems to be corrupted, as well as clean out your cache)
Make sure firefox is closed when you do "upgrade" please.

did not work, and output was about the same as till now...

---

### Post by PmDematagoda on 2008-02-10
Do:-
```
sudo rm "/var/cache/apt/archives/firefox_2.0.0.12+2nobinonl y+2-0ubuntu0.7.10_i386.deb"
```
After that do:-
```
sudo apt-get install -f
```
and 
```
sudo dpkg --configure -a
```

---

### Post by shadowber on 2008-02-10
Thank you very much, that worked!!

---

### Post by Rocket2DMn on 2008-02-10
! I didn't see the space in the file path !  That's why my rm command didn't work.
Glad you got it worked out.

---

### Post by shadowber on 2008-02-11
Heh, thank you for trying though!!

---

