---
title: "help installing wine"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2007-03-22
I tried to install wine like it says to on thier site.
But i have no clue what went wrong.

```
ben@ben-ubuntu:~$ sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list -O /etc/apt/sources.list.d/winehq.list
--11:13:53--  http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list
           => `/etc/apt/sources.list.d/winehq.list'
Resolving wine.budgetdedicated.com... 
81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 139 [text/plain]

100%[====================================>] 139           --.--K/s             

11:13:56 (11.05 MB/s) - `/etc/apt/sources.list.d/winehq.list' saved [139/139]

ben@ben-ubuntu:~$ 
ben@ben-ubuntu:~$ 
ben@ben-ubuntu:~$ sudo apt-get update
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US      
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US      
Get:2 http://wine.budgetdedicated.com edgy Release.gpg [191B]                  
Ign http://wine.budgetdedicated.com edgy/main Translation-en_US                
Hit http://security.ubuntu.com edgy-security Release                           
Ign http://people.debian.org php5.0 Release.gpg                                
Ign http://people.debian.org php5.0/hoary Translation-en_US                    
Get:3 http://wine.budgetdedicated.com edgy Release [739B]                      
Ign http://people.debian.org php5.0 Release                                    
Ign http://people.debian.org php5.0/hoary Packages                             
Get:4 http://archive.ubuntu.com edgy Release.gpg [191B]                        
Ign http://people.debian.org php5.0/hoary Sources                              
Hit http://people.debian.org php5.0/hoary Packages                             
Hit http://archive.ubuntu.com edgy Release                                     
Hit http://people.debian.org php5.0/hoary Sources                              
Get:5 http://us.archive.ubuntu.com edgy Release.gpg [191B]                     
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US
Get:6 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com edgy Release 
Hit http://us.archive.ubuntu.com edgy-updates Release
Ign http://wine.budgetdedicated.com edgy Release
Hit http://security.ubuntu.com edgy-security/main Packages                     
Ign http://wine.budgetdedicated.com edgy/main Packages                         
Hit http://archive.ubuntu.com edgy/main Sources                      
Hit http://us.archive.ubuntu.com edgy/main Packages                  
Hit http://security.ubuntu.com edgy-security/restricted Packages     
Hit http://security.ubuntu.com edgy-security/restricted Sources                
Hit http://security.ubuntu.com edgy-security/main Sources                      
Ign http://wine.budgetdedicated.com edgy/main Sources                          
Hit http://archive.ubuntu.com edgy/restricted Sources                          
Hit http://us.archive.ubuntu.com edgy/restricted Packages            
Hit http://us.archive.ubuntu.com edgy/restricted Sources             
Hit http://us.archive.ubuntu.com edgy/main Sources                   
Hit http://security.ubuntu.com edgy-security/multiverse Sources      
Hit http://security.ubuntu.com edgy-security/multiverse Packages     
Get:7 http://wine.budgetdedicated.com edgy/main Packages [1319B]     
Hit http://us.archive.ubuntu.com edgy/multiverse Sources           
Hit http://us.archive.ubuntu.com edgy/universe Sources
Hit http://us.archive.ubuntu.com edgy/multiverse Packages
Hit http://us.archive.ubuntu.com edgy/universe Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://us.archive.ubuntu.com edgy-updates/main Sources
Hit http://us.archive.ubuntu.com edgy-updates/multiverse Sources
Get:8 http://wine.budgetdedicated.com edgy/main Sources [641B]
Hit http://us.archive.ubuntu.com edgy-updates/multiverse Packages
Fetched 2894B in 2s (1057B/s)
Reading package lists... Done
W: GPG error: http://wine.budgetdedicated.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems
ben@ben-ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnucrypto-java xserver-xorg-video-rendition xserver-xorg-input-evdev
  xserver-xorg-video-newport xserver-xorg-video-s3virge xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-tdfx
  xserver-xorg-video-trident xserver-xorg-video-glint xserver-xorg-video-fbdev
  xserver-xorg-input-wacom xserver-xorg-video-v4l xserver-xorg-video-mga
  xserver-xorg-input-mouse xserver-xorg-video-nsc liblog4j1.2-java
  xserver-xorg-video-vesa xserver-xorg-video-siliconmotion
  xserver-xorg-video-tga xserver-xorg-video-sis libswt3.2-gtk-java
  xserver-xorg-video-vga xserver-xorg-video-via xserver-xorg-video-s3
  libseda-java xserver-xorg-video-nv libcommons-cli-java xserver-xorg-core
  libgtk-jni xserver-xorg-video-tseng xserver-xorg-video-savage libcairo-java
  xserver-xorg-input-all libbcprov-java xserver-xorg-input-elographics
  xserver-xorg-input-kbd localechooser-data libglib-java
  xserver-xorg-video-i128 xserver-xorg-video-neomagic xserver-xorg-video-chips
  xserver-xorg-video-voodoo xserver-xorg-video-i740 xserver-xorg-video-i810
  libgtk-java xserver-xorg-video-cyrix xserver-xorg-video-dummy
  libswt3.2-gtk-jni xserver-xorg-input-synaptics xserver-xorg-video-sisusb
  xserver-xorg-video-imstt xserver-xorg-video-cirrus
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 9747kB of archives.
After unpacking 44.3MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? y
Get:1 http://wine.budgetdedicated.com edgy/main wine 0.9.33~winehq0~ubuntu~6.10-2 [9747kB]
Fetched 9747kB in 22s (426kB/s)                                                
Selecting previously deselected package wine.
(Reading database ... 125037 files and directories currently installed.)
Unpacking wine (from .../wine_0.9.33~winehq0~ubuntu~6.10-2_i386.deb) ...
Setting up apache (1.3.34-4ubuntu1) ...
 * Configuration syntax error detected, not starting/reloading...               
Syntax error on line 1 of /etc/apache/conf.d/vhost.conf.gz:
Invalid command '&zCvhost.conf', perhaps mis-spelled or defined by a module not included in the server configuration
                                                                         [fail]
invoke-rc.d: initscript apache, action "start" failed.
dpkg: error processing apache (--configure):
 subprocess post-installation script returned error exit status 1
Setting up wine (0.9.33~winehq0~ubuntu~6.10-2) ...

Errors were encountered while processing:
 apache
E: Sub-process /usr/bin/dpkg returned an error code (1)
ben@ben-ubuntu:~$ 
```

---

### Post by familyjules74123 on 2007-03-22
wine is located in the synaptic package manager if you would like a easier way to install it.  You might have to enable the multiverse and universe repositories though

---

### Post by RDUBBALO on 2007-03-22
Do it how they reccomend on wineHQ [http://www.winehq.org/]("http://www.winehq.org/") Just follow all their steps.

---

### Post by RDUBBALO on 2007-03-22
Yeah he is right you need to allow all your repositories go into the synaptic package manager and hit settings-->preferences-->repositories tab and make sure they are all checked.

---

### Post by warmotor on 2007-03-22
I installed Wine from the add/remove programs menu without a problem, definately try that first. Although I had already gone into my software sources .conf file and un-commented the unsupported repositories ahead of time - I didn't have to do anything special to get it installed and running. 

Answers to questions no one asked:

If you plan on running windows programs from existing NTFS drives on your box, you may want to enable writes to NTFS (some programs will crash if they can't write to the directory where they live) and I found enabling login as root helped bypass the permission headaches associated with working with NTFS drives too, just be sure to log back OUT when you're done.

Ah, I feel as if I've almost justified my existence.

---

