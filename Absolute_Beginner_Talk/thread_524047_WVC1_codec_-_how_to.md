---
title: "WVC1 codec - how to?"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Harry789 on 2007-08-12
I have been all over the internet, and I cannot find a good solution to playing wvc1 .wmv files in ubuntu.

Who has advice/solution?

---

### Post by Kobalt on 2007-08-12
Have you tried [this]("http://ubuntuforums.org/showthread.php?t=413624") ?

---

### Post by Harry789 on 2007-08-12
I tried but I am not allowed to make any changes to the .sources file ?

---

### Post by Harry789 on 2007-08-12
see:

laan97ac@laan97ac-laptop:~$ wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
Password:
OK
laan97ac@laan97ac-laptop:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release          
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg [189B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Fetched 192B in 3s (63B/s)
Reading package lists... Done
laan97ac@laan97ac-laptop:~$ sudo apt-get install libdvdcss2 w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
libdvdcss2 set to manual installed.
w32codecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
laan97ac@laan97ac-laptop:~$ 

and still not working

---

### Post by Kobalt on 2007-08-12
Are you trying to read a file that has [DRM]("http://en.wikipedia.org/wiki/Drm") ? If so, (to my knowledge) it can't be done in Ubuntu.

---

### Post by Harry789 on 2007-08-12
that may be the case, I actually do not know.

---

