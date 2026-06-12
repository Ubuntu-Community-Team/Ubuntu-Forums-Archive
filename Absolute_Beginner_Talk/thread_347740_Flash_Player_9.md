---
title: "Flash Player 9"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by KriswithaK on 2007-01-27
Hello everyone, 
I am also a brand new user to Ubuntu, and am excited to get familar with all this OS has to offer.
I am having a very difficult time installing adobe flash player 9, as whenever I try to download it off of the adobe website, the download stops about 14% in every single time.  I have tried using the psyco cats tutorial, and the .tar.gz file still does not download.  Finally I got a windows user to download the .rpm file and send it to me. To open the file I used the command rpm -Uvh (flash installer>.  When I do this, the error I get is:
 Failed dependencies:
        /bin/bash is needed by flash-plugin-9.0.31.0-release.i386
        /bin/sh is needed by flash-plugin-9.0.31.0-release.i386
        libX11.so.6 is needed by flash-plugin-9.0.31.0-release.i386
        libXext.so.6 is needed by flash-plugin-9.0.31.0-release.i386
        libXt.so.6 is needed by flash-plugin-9.0.31.0-release.i386
        libc.so.6 is needed by flash-plugin-9.0.31.0-release.i386
        libc.so.6(GCC_3.0) is needed by flash-plugin-9.0.31.0-release.i386
        libc.so.6(GLIBC_2.0) is needed by flash-plugin-9.0.31.0-release.i386
        libc.so.6(GLIBC_2.1) is needed by flash-plugin-9.0.31.0-release.i386
        libc.so.6(GLIBC_2.1.2) is needed by flash-plugin-9.0.31.0-release.i386
        libc.so.6(GLIBC_2.1.3) is needed by flash-plugin-9.0.31.0-release.i386
        libc.so.6(GLIBC_2.2) is needed by flash-plugin-9.0.31.0-release.i386
        libc.so.6(GLIBC_2.3) is needed by flash-plugin-9.0.31.0-release.i386
        libdl.so.2 is needed by flash-plugin-9.0.31.0-release.i386
        libdl.so.2(GLIBC_2.0) is needed by flash-plugin-9.0.31.0-release.i386
        libdl.so.2(GLIBC_2.1) is needed by flash-plugin-9.0.31.0-release.i386
        libfontconfig.so.1 is needed by flash-plugin-9.0.31.0-release.i386
        libfreetype.so.6 is needed by flash-plugin-9.0.31.0-release.i386
        libglib-2.0.so.0 is needed by flash-plugin-9.0.31.0-release.i386
        libgobject-2.0.so.0 is needed by flash-plugin-9.0.31.0-release.i386
        libgtk-x11-2.0.so.0 is needed by flash-plugin-9.0.31.0-release.i386
        libm.so.6 is needed by flash-plugin-9.0.31.0-release.i386
        libm.so.6(GLIBC_2.0) is needed by flash-plugin-9.0.31.0-release.i386
        libpthread.so.0 is needed by flash-plugin-9.0.31.0-release.i386
        libpthread.so.0(GLIBC_2.0) is needed by flash-plugin-9.0.31.0-release.i386
        libpthread.so.0(GLIBC_2.1) is needed by flash-plugin-9.0.31.0-release.i386
        libpthread.so.0(GLIBC_2.2) is needed by flash-plugin-9.0.31.0-release.i386
        libpthread.so.0(GLIBC_2.2.3) is needed by flash-plugin-9.0.31.0-release.i386
        libpthread.so.0(GLIBC_2.3.2) is needed by flash-plugin-9.0.31.0-release.i386
and I have no idea what any of that means.  Any help would be GREATLY appreciated, as I need flash to do my physics assignments.

---

### Post by kosmic on 2007-01-27
Dont install an RPM file in a debian system. if you must use an rpm package use the alien program 'sudo apt-get install alien' and convert it to a deb package.

Also get the tgz package.

wget -c [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

What is the error you have when you execute the above command ?

---

### Post by KriswithaK on 2007-01-27
Now when I try to install alien, I get this message:
kris@kris-basement:~$ sudo aptitude update
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                   
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US  
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Fetched 4B in 1s (2B/s)  
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache
kris@kris-basement:~$ sudo aptitude install alien
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Let me thank everyone now for all the help that I can get, it's VERY appreciated

---

### Post by r4ik on 2007-01-27
It is in Synaptic reload first than search for flash. If it it is not try,

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

Good luck !

---

### Post by kosmic on 2007-01-27
> **KriswithaK said:**
> Now when I try to install alien, I get this message:
kris@kris-basement:~$ sudo aptitude update
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                   
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US  
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Fetched 4B in 1s (2B/s)  
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache
kris@kris-basement:~$ sudo aptitude install alien
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Let me thank everyone now for all the help that I can get, it's VERY appreciated

in a terminal type :

sudo dpkg --configure -a

---

### Post by xpod on 2007-01-27
You could always use automatx2 which should solve the problem for you..

[http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

It will also supply you with a load of other handy apps from your codecs and java to your p2p`s and  multimedia players...and a few other handy things  besides.

Of course you could also spend the next few days tracking down and installing everything  the "proper" ways but if you want things made easy then AX is the way to go:D 

Plenty time later to "learn" i say

Good luck

---

### Post by KriswithaK on 2007-01-27
alright, I tried open synaptic, but it told me I had to run dpkg --configure -a

I did that, and this is happening 
root@kris-basement:/home/kris# dpkg --configure -a 
Setting up flash-plugin (9.0.31.0-1) ...

Setting up flashplugin-nonfree (7.0.68~ubuntu3) ...
Downloading... 
 and it has been sitting like this for about 10 mins.  and I have cable, so I don't think it's going to fix itself

---

### Post by r4ik on 2007-01-27
Forget about it please try,

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

or if that fails xpod suggestion :)

---

### Post by stevedasilva on 2007-01-29
Hi, flashplugin-nonfree tries to download [http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz)

it md5sums the downloaded file and one unpacked component. I think that package has to be overworked, the URL changed and the MD5sums updated. 

So either you wait until that package was updated or you use the "manual method" [www.adobe.com](www.adobe.com)

(as of today, 29.1.07)
HTH
Steve

---

