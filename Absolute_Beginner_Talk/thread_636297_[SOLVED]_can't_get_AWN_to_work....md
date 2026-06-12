---
title: "[SOLVED] can't get AWN to work..."
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2007-12-09
ok so i'm trying to install it. and i'm following the instructions of this site [http://www.simplehelp.net/2007/05/31/how-to-install-setup-and-use-avant-window-navigator-awn-in-ubuntu-feisty/](http://www.simplehelp.net/2007/05/31/how-to-install-setup-and-use-avant-window-navigator-awn-in-ubuntu-feisty/)

but it's not working when i put in the codes it tells me too this is what i get...
```
jordan@jordan-laptop:~$ sudo gedit /etc/apt/sources.list
jordan@jordan-laptop:~$ wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O- | sudo apt-key add -
--15:45:02--  http://download.tuxfamily.org/syzygy42/8434D43A.gpg
           => `-'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
15:45:02 ERROR 404: Not Found.

gpg: no valid OpenPGP data found.
jordan@jordan-laptop:~$ rm 8434D43A.gpg
rm: cannot remove `8434D43A.gpg': No such file or directory
jordan@jordan-laptop:~$ sudo apt-get update
Get:1 http://mx.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://mx.archive.ubuntu.com gutsy/main Translation-en_US                  
Ign http://mx.archive.ubuntu.com gutsy/restricted Translation-en_US           
Ign http://mx.archive.ubuntu.com gutsy/universe Translation-en_US             
Ign http://mx.archive.ubuntu.com gutsy/multiverse Translation-en_US           
Get:2 http://mx.archive.ubuntu.com gutsy-updates Release.gpg [191B]            
Ign http://mx.archive.ubuntu.com gutsy-updates/main Translation-en_US          
Ign http://mx.archive.ubuntu.com gutsy-updates/restricted Translation-en_US    
Ign http://mx.archive.ubuntu.com gutsy-updates/universe Translation-en_US      
Ign http://mx.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US    
Hit http://mx.archive.ubuntu.com gutsy Release                                 
Hit http://mx.archive.ubuntu.com gutsy-updates Release                         
Hit http://mx.archive.ubuntu.com gutsy/main Packages                           
Hit http://mx.archive.ubuntu.com gutsy/restricted Packages                     
Hit http://mx.archive.ubuntu.com gutsy/main Sources                           
Hit http://mx.archive.ubuntu.com gutsy/restricted Sources                     
Hit http://mx.archive.ubuntu.com gutsy/universe Packages                      
Hit http://mx.archive.ubuntu.com gutsy/universe Sources                       
Hit http://mx.archive.ubuntu.com gutsy/multiverse Packages                    
Hit http://mx.archive.ubuntu.com gutsy/multiverse Sources                     
Hit http://mx.archive.ubuntu.com gutsy-updates/main Packages                   
Hit http://mx.archive.ubuntu.com gutsy-updates/restricted Packages             
Hit http://mx.archive.ubuntu.com gutsy-updates/main Sources                    
Hit http://mx.archive.ubuntu.com gutsy-updates/restricted Sources             
Hit http://mx.archive.ubuntu.com gutsy-updates/universe Packages              
Hit http://mx.archive.ubuntu.com gutsy-updates/universe Sources               
Hit http://mx.archive.ubuntu.com gutsy-updates/multiverse Packages             
Hit http://mx.archive.ubuntu.com gutsy-updates/multiverse Sources              
Get:3 http://download.tuxfamily.org gutsy Release.gpg [189B]                   
Ign http://download.tuxfamily.org gutsy/avant-window-navigator Translation-en_US
Get:4 http://download.tuxfamily.org feisty Release.gpg [189B]
Get:5 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US
Ign http://download.tuxfamily.org feisty/avant-window-navigator Translation-en_US
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://download.tuxfamily.org gutsy Release
Hit http://security.ubuntu.com gutsy-security Release               
Get:6 http://download.tuxfamily.org feisty Release [26.9kB]         
Hit http://security.ubuntu.com gutsy-security/main Packages
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages                
Hit http://security.ubuntu.com gutsy-security/universe Sources                 
Hit http://security.ubuntu.com gutsy-security/multiverse Packages              
Hit http://security.ubuntu.com gutsy-security/multiverse Sources               
Hit http://download.tuxfamily.org gutsy/avant-window-navigator Packages        
Hit http://download.tuxfamily.org gutsy/avant-window-navigator Sources         
Get:7 http://download.tuxfamily.org feisty/avant-window-navigator Packages [1488B]
Get:8 http://download.tuxfamily.org feisty/avant-window-navigator Sources [879B]
Fetched 29.5kB in 6s (4545B/s)                                                 
Reading package lists... Done
jordan@jordan-laptop:~$ sudo apt-get install avant-window-navigator-svn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package avant-window-navigator-svn is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  avant-window-navigator-bzr
E: Package avant-window-navigator-svn has no installation candidate
jordan@jordan-laptop:~$ 

```

so what should i do? =\

---

### Post by tnseditor on 2007-12-09
I just tried to do that last night.  While it is good to be cautious of such files, [www.getdeb.net](www.getdeb.net) has a nice deb file to use.

---

### Post by RadiationHazard on 2007-12-09
could you give me a direct download link to what i need to download??

---

### Post by tnseditor on 2007-12-09
[http://www.getdeb.net/search.php?keywords=avant](http://www.getdeb.net/search.php?keywords=avant).  Just select the version of Ubuntu you are using.

---

