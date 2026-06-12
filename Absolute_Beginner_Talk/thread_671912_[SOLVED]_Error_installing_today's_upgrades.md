---
title: "[SOLVED] Error installing today's upgrades"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by arvevans on 2008-01-19
Error message when trying to install today's upgrades:

[INDENT]W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb)
  403 Forbidden[/INDENT]

Should I be worried about this?

Arv
_._

---

### Post by nkobel003 on 2008-01-19
Typically, it just means the server is down for that time.  403 forbidden can have a variety of reasons though.  Give it another day.

---

### Post by asmoore82 on 2008-01-19
I got this too ... fixed it by doing another package list update, then the upgrade...

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by RomeReactor on 2008-01-19
Hi. Today's xserver-xorg-core [update is buggy]("http://ubuntuforums.org/showthread.php?t=671065") (VLC, among others, and Java applications such as Azureus are unable to start); better wait until the package is fixed before updating it.

---

### Post by nikef on 2008-01-19
> **RomeReactor said:**
> Hi. Today's xserver-xorg-core [update is buggy]("http://ubuntuforums.org/showthread.php?t=671065") (VLC, among others, and Java applications such as Azureus are unable to start); better wait until the package is fixed before updating it.

Hi,thanks for letting us know 
i have 14 updates waiting to be installed,before i install anything i always check this site for errors.

i noticed a couple of errors yesterday,i did not update  :(
when/will we know if the package is fixed ?

---

### Post by fatality_uk on 2008-01-19
> **nikef said:**
> Hi,thanks for letting us know 
i have 14 updates waiting to be installed,before i install anything i always check this site for errors.

i noticed a couple of errors yesterday,i did not update  :(
when/will we know if the package is fixed ?

Just had an update run fine. Those issues have been addressed. I suggest you run update manager again and hopefully will be fixed for you. :)

---

### Post by RomeReactor on 2008-01-19
> **nikef said:**
> i noticed a couple of errors yesterday,i did not update  :(
when/will we know if the package is fixed ?

Hi. The fixed package is now available in the repositories; open Update Manager (System->Administration->Update Manager) and press the 'Check' button. Here's the [bug report]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969").

---

### Post by ronmarley1 on 2008-01-19
I just ran updates manually and restarted X and all is well.

---

### Post by nikef on 2008-01-19
Thank you all 
i have just run the updater like you said,now i am going to restart ,fingers crossed it works ok

---

### Post by nikef on 2008-01-19
Phew
i am back,just restarted everything seems fine

thanks,once again all :)

---

### Post by arvevans on 2008-01-19
STILL BROKEN (see below):

[INDENT]arv@arv-desktop:~$ sudo apt-get update
[sudo] password for arv:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Translation-en_US      
Get:4 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg [189B]                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Translation-en_US        
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_US            
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release [51.2kB]               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_US       
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release [58.5kB]                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages                     
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release                          
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages [66.1kB]        
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages [4263B]    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages                         
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages [96.9kB]         
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages [14B]     
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages [36.7kB]    
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages [2903B]   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Sources                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Sources                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Sources                      
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages [7569B]    
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Packages [27.1kB]     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages                
Fetched 352kB in 7s (47.8kB/s)                                                 
Reading package lists... Done
arv@arv-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  update-manager update-manager-core xserver-xorg-core xserver-xorg-dev
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 4914kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main xserver-xorg-core 2:1.3.0.0.dfsg-12ubuntu8.3 [3677kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main update-manager 1:0.81.2 [885kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main update-manager-core 1:0.81.2 [30.3kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main xserver-xorg-dev 2:1.3.0.0.dfsg-12ubuntu8.3 [322kB]
Fetched 4914kB in 53s (91.7kB/s)         
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.3_i386.deb)  rename failed, No such file or directory (/var/cache/apt/archives/partial/xserver-xorg-core_2%3a1.3.0.0.dfsg-12ubuntu8.3_i386.deb -> /var/cache/apt/archives/xserver-xorg-core_2%3a1.3.0.0.dfsg-12ubuntu8.3_i386.deb).
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
arv@arv-desktop:~$ 
[/INDENT]

Arv
_._

---

### Post by arvevans on 2008-01-19
OK.  I give up.

I manually downloaded 

[INDENT][http://security.ubuntu.com/ubuntu/po...tu8.3_i386.deb](http://security.ubuntu.com/ubuntu/po...tu8.3_i386.deb) [/INDENT]

from the archive and manually installed it myself.  It worked just fine (might be an installer problem?).

Problem solved, for me at least.

Arv
_._

---

### Post by thelatinist on 2008-01-19
This was actually a problem because the original package was broken and was replaced with a new one.  Update only checks for the list of available packages periodically, so it didn't know about the change.  Right-clicking on the update manager icon in the notification area and choosing check for updates would have fixed it.

---

### Post by arvevans on 2008-01-19
Thanks.  That is good to know for future situations like this one.

Arv
_._

---

