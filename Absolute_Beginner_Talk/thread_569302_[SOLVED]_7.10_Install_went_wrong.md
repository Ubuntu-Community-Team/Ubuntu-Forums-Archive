---
title: "[SOLVED] 7.10 Install went wrong"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by michiel.patrick on 2007-10-06
Well last night was updating to 7.10 and i thought my laptop was plugged in when i left but someone must have unplugged it and the battery died in mid install. Does anyone think this caused some problems because i believe it probably did. Im in ubuntu now and it is ok but when i try to update it always says missing dependencies.

---

### Post by taurus on 2007-10-06
Why don't you post the complete error message here so we all know what's wrong with it?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
-or-
sudo apt-get dist-upgrade
```

---

### Post by michiel.patrick on 2007-10-06
Ok I did sudo apt-get dist-upgrade and got this message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-restricted-modules-2.6.22-13-generic
The following packages will be upgraded:
  apport apport-gtk evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-plugins gdebi gdebi-core
  gnome-keyring gnome-user-guide guidance-backends libcamel1.2-10
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6
  libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13
  libexchange-storage1.2-3 libgnome-keyring0 libgnome2-0 libgnome2-common
  libpam-gnome-keyring libpoppler-glib2 libpoppler2 linux-generic
  linux-headers-generic linux-image-generic linux-restricted-modules-common
  linux-restricted-modules-generic poppler-utils python-apport
  python-problem-report ubuntu-desktop ubuntu-minimal ubuntu-standard
38 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0B/40.5MB of archives.
After unpacking 1348kB disk space will be freed.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 util-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by taurus on 2007-10-06
Try running the update first.

```
sudo apt-get update
```

---

### Post by michiel.patrick on 2007-10-06
Also when i try to run update manager I get this error


E: tzdata: subprocess post-installation script returned error exit status 10
E: util-linux: dependency problems - leaving unconfigured

---

### Post by michiel.patrick on 2007-10-06
ok here is the first two commands:

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release [65.9kB]                      
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US     
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources           
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages [1078kB]      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages [7649B]           
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources [2107B]            
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources [307kB]                  
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources [57.0kB]          
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources [1225kB]            
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages [4048kB]           
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages [159kB]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources              
Fetched 6949kB in 39s (175kB/s)                                                
Reading package lists... Done
mpatrick@mpatrick-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-restricted-modules-generic
The following packages will be upgraded:
  apport apport-gtk evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-plugins gdebi gdebi-core
  gnome-keyring gnome-user-guide guidance-backends libcamel1.2-10
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6
  libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13
  libexchange-storage1.2-3 libgnome-keyring0 libgnome2-0 libgnome2-common
  libpam-gnome-keyring libpoppler-glib2 libpoppler2 linux-generic
  linux-headers-generic linux-image-generic linux-restricted-modules-common
  poppler-utils python-apport python-problem-report ubuntu-desktop
  ubuntu-minimal ubuntu-standard
37 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
9 not fully installed or removed.
Need to get 0B/23.9MB of archives.
After unpacking 44.5MB disk space will be freed.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 util-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by zerobinary on 2007-10-06
try reinstalling 7.10 if this doesn't work install the stable release
and wait for 7.10
lol
I can't wait either lol

---

### Post by michiel.patrick on 2007-10-06
Ya I have tried to reinstall 7.10 and it says depency problems. I cannot wait myself. I thought opensuse was the greatest for so long.... o my was i ever wrong. More stuff works on my laptop in ubuntu than works on xp pro. Battery life is much better and all the accessory buttons on the front work. It is easy to tell that a lot of time has been put into unbuntu and its quality shows

---

### Post by zerobinary on 2007-10-06
then try using the live cd to backup the the work then use qparted in knoppix live cd
To remove ubuntu and format it to fat32
CAN'T WAIT

---

### Post by michiel.patrick on 2007-10-06
Since I have gotten everything working (wireless, resolution,etc) Is there any way I can save my settings and driver configurations? The reason I ask is that if I can then I will just  format and reinstall and upgrade again after that

---

### Post by zerobinary on 2007-10-06
lol no
But u can write it down in a piece of paper and reset it using the paper 
sorry i can't help u

---

### Post by michiel.patrick on 2007-10-06
damnit haha I hate setting everything up. I will probably just wait till 7.10 since the system is not overly unstable. Thanks for the help

---

### Post by Pumalite on 2007-10-06
You might want to try:
sudo dpkg --remove --force-remove-reinstreq tzdata

---

### Post by michiel.patrick on 2007-10-06
tried it and it didnt work haha. O well i guess i will learn to double check next time

---

### Post by ravenwere on 2007-10-07
If an update process is interrupted (like when my dog accidentally hits the reset button when I'm installing updates) usually you ```
sudo dpkg --configure -a
``` which should then pick up where you left off.

---

### Post by michiel.patrick on 2007-10-07
Thanks, that is good to know for the future.

---

