---
title: "Problem in installed ati graphics card"
date: 2011-04-22
forum: Any Other OS
---

### Post by vicke4 on 2011-04-22
i have installed ati driver by the
instructions of the following url
note:i read and followed every instructions correctly


[https://help.ubuntu.com/](https://help.ubuntu.com/)
community/BinaryDriverHowto/
ATI
[]()

no problem the driver is
instlled.but my problem is when i
open ati control center i get
following error report


There was a problem initializing
Catalyst Control Center Linux
edition. It could be caused by the
following.
No ATI graphics driver is installed,
or the ATI driver is not
functioning properly.
Please install the ATI driver
appropriate for you ATI hardware,
or configure using aticonfig.

please help me how to fix this
problem?

---

### Post by dino99 on 2011-04-22
which card is it ?

into a terminal, run:

sudo rm /etc/X11/xorg.conf
sudo apt-get update
sudo apt-get install -f
sudo apt-get install xserver-xorg-video-radeon

then reboot

---

### Post by vicke4 on 2011-04-22
my graphics card is ati mobility radeon hd 4350.i entered your commands i get the following output my output is






vicky@Ganapathy-HP-ProBook-4520s ~ $ sudo rm /etc/X11/xorg.conf
[sudo] password for vicky: 
rm: cannot remove `/etc/X11/xorg.conf': No such file or directory
vicky@Ganapathy-HP-ProBook-4520s ~ $ sudo apt-get update
Ign file: binary/ Release.gpg
Ign file:/usr/share/local-repository/ binary/ Translation-en                   
Ign file:/usr/share/local-repository/ binary/ Translation-en_IN                
Ign file: binary/ Release                                                      
Ign file: binary/ Packages                                                     
Ign file: binary/ Packages                                                     
Get:1 [http://packages.linuxmint.com](http://packages.linuxmint.com) julia Release.gpg [198B]                   
Ign [http://packages.linuxmint.com/](http://packages.linuxmint.com/) julia/import Translation-en                 
Ign [http://packages.linuxmint.com/](http://packages.linuxmint.com/) julia/import Translation-en_IN              
Ign [http://packages.linuxmint.com/](http://packages.linuxmint.com/) julia/main Translation-en                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_IN          
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release.gpg [197B]                
Ign [http://packages.linuxmint.com/](http://packages.linuxmint.com/) julia/main Translation-en_IN                
Ign [http://packages.linuxmint.com/](http://packages.linuxmint.com/) julia/upstream Translation-en               
Ign [http://packages.linuxmint.com/](http://packages.linuxmint.com/) julia/upstream Translation-en_IN            
Get:3 [http://packages.linuxmint.com](http://packages.linuxmint.com) julia Release [7,253B]                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_IN    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_IN    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_IN      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en     
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_IN    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_IN  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_IN
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en      
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages      
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) julia/main i386 Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release                         
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) julia/upstream i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages                      
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) julia/import i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages                
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) julia/main i386 Packages                     
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) julia/upstream i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages        
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) julia/import i386 Packages                   
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) julia/main i386 Packages                     
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) julia/upstream i386 Packages                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages            
Hit [http://packages.linuxmint.com](http://packages.linuxmint.com) julia/import i386 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages      
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en_IN             
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en_IN
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages
Fetched 7,648B in 24s (309B/s)
Reading package lists... Done
vicky@Ganapathy-HP-ProBook-4520s ~ $ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 303 not upgraded.
vicky@Ganapathy-HP-ProBook-4520s ~ $ sudo apt-get install xserver-xorg-video-radeon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-radeon is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 303 not upgraded.

---

### Post by vicke4 on 2011-04-22
Sorry i am using mint 10.i know mint is based on ubuntu.in mint forums i got no answers so only i get it to ubuntu forums.

---

### Post by vicke4 on 2011-04-22
when i put the command sudo aticonfig --initial in terminal i got the following output. 



aticonfig: No supported adapters detected





when i put the command fglrxinfo in terminal i got the following output


Segmentation fault

---

### Post by Perfect Storm on 2011-04-22
Moved to Other OS/Distro Talk.

---

### Post by Jechem on 2011-04-22
> **vicke4 said:**
> when i put the command sudo aticonfig --initial in terminal i got the following output. 



aticonfig: No supported adapters detected





when i put the command fglrxinfo in terminal i got the following output


Segmentation fault

This may help:
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Aticonfig_not_found_after_installation_.26_.22module_does_not_exist.22_after_boot](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Aticonfig_not_found_after_installation_.26_.22module_does_not_exist.22_after_boot)

---

### Post by Mosabama on 2011-04-22
is there "additional drivers" in administration menu in mint?
if there is I guess it will do everything alone from there.

---

### Post by Zero Prime on 2011-04-22
Yes, there is an additional drivers in Linux Mint 10.  All you have to do is open additional drivers and it will find the driver for your card.  Activate then restart X or reboot.  If your using Gnome, it will be under Administration, under KDE it is under System.  Also, if your using KDE, then you might have to disable Kwallet.

BTW, most of this post was copied from what I already posted on the Mint forums, sometimes you have to wait a little longer than a few hours for an answer, patience is a virtue :)

---

### Post by vicke4 on 2011-04-22
There is no driver for me in additional drivers.please help me.

---

### Post by Shadowfire on 2011-05-21
Did you ever get this fixed?  If not then please do the following.

Go to Terminal:

Type in: lspci

and copy and paste it into the reply.

Thanks,

-SF-

---

