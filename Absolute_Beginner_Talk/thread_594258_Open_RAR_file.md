---
title: "Open RAR file?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-10-27
I have unrar, don't understand how to make it work; I need to install a driver that I downloaded to the desktop. When I try to install it, I get this. I know you guys have the answer!

 > tr@tr:~$ unrar e linux_audio.rar

UNRAR 3.70 beta 3 freeware      Copyright (c) 1993-2007 Alexander Roshal

Cannot open linux_audio.rar
No such file or directory
No files to extract
tr@tr:~$ 


:confused:  :confused:

---

### Post by kast on 2007-10-27
tr@tr:~$ ?? 

have you changed to your Desktop?
[B]
cd Desktop  [/B]  ??

[B]
user@nix:~/Desktop$ [/B]

---

### Post by taurus on 2007-10-27
Are you in the right directory where **linux_audio.rar** is located?

```
ls -la
unrar x linux_audio.rar <- This would unpack it.
```

---

### Post by discmaster on 2007-10-27
I guess what I am really asking is, what do I actually do with this file? It is an audio driver, I downloaded it to the desktop & that's as far as I got. I don't understand where/how I am supposed to install it or anything. Linux noob here :confused:

Please instruct in "dummy" language please! :lolflag:

---

### Post by taurus on 2007-10-27
Unpack it first and see if there is a README or INSTALL.  Otherwise, where did you download it?

---

### Post by discmaster on 2007-10-27
> Unpack it first and see if there is a README or INSTALL. Otherwise, where did you download it?I read the readme/install & it is all "greek" to me, lol. I downloaded it from my mainboards' website; they actually had a soundcard driver listed for linux, I was surprised.
[http://support.asus.com/download/download.aspx?SLanguage=en-us&model=A8V-VM%20SE](http://support.asus.com/download/download.aspx?SLanguage=en-us&model=A8V-VM%20SE)

But, since I don't really understand this OS or how to install things, esp. from the readme instructions included w/ this driver, I am totally lost. :(

---

### Post by taurus on 2007-10-27
Does your onboard soundcard work at all when you installed Gutsy?

You have to unpack it with unrar.  It will create a new directory called Audio.  You need to change to that directory, cd Audio, and you will see 6 more directories.  You need to change to the Linux one, cd Linux, and uncompress and unpack the realtek-linux one.

```
tar xvzf realtek-linux-audiopack-3.5-6b.tar.bz2
```
That will create a new directory so you need to change to that.  Then, there is a Readme.txt that you need to look at.

```
more Readme.txt
```

---

### Post by discmaster on 2007-10-27
> 
Does your onboard soundcard work at all when you installed Gutsy? Yes, except for capturing audio. I was hoping this would resolve that issue.I will work at what you have posted for me, but I will most likely be back! 
I am also confused as to "where" to install the driver? In the "filesystem" directory? I know windows, but I am lost here.

---

### Post by taurus on 2007-10-27
There is a fill called install.  You need to run that to install it on your machine.

```
sudo ./install
```

---

### Post by discmaster on 2007-10-27
> There is a fill called install. You need to run that to install it on your machine.After I have done that, how can I confirm that everything is installed correctly?

---

### Post by taurus on 2007-10-27
And that is why you need to read the manual, [http://support.asus.com/download/download.aspx?SLanguage=en-us&model=A8V-VM%20SE&type=map&mapindex=10](http://support.asus.com/download/download.aspx?SLanguage=en-us&model=A8V-VM%20SE&type=map&mapindex=10).

---

### Post by shankhs on 2007-10-28
There are many searches available for beginners to find where they have stored stuffs
**BEAGLE**

---

### Post by discmaster on 2007-10-28
> And that is why you need to read the manual, [http://support.asus.com/download/dow...ap&mapindex=10](http://support.asus.com/download/dow...ap&mapindex=10). I have read the manual. :) There isn't anything in there in regards to linux that I am aware of. I know how to check the dev. manager, etc. in windows, but I don't know how to properly check for these things under linux.

I am very anxious to learn, but there seems to be good tutorials/info. lacking for this OS, unless I am just looking in the wrong places. Unfortunately, this OS in not "self-intuitive" like Windoze... :lolflag:

---

### Post by aysiu on 2007-10-28
Copy and paste these commands into the terminal and then paste the output back here: ```
cd ~/Desktop
wget -c http://dlsvr03.asus.com/pub/ASUS/mb/socket939/A8V-VM_SE/linux_audio.rar
sudo apt-get update
sudo apt-get install unrar
unrar e linux_audio.rar
ls
cat Readme.txt
```

---

### Post by discmaster on 2007-10-28
Thank You 
> tr@tr:~$ cd ~/Desktop
tr@tr:~/Desktop$ wget -c [http://dlsvr03.asus.com/pub/ASUS/mb/socket939/A8V-VM_SE/linux_audio.rar](http://dlsvr03.asus.com/pub/ASUS/mb/socket939/A8V-VM_SE/linux_audio.rar)
--20:33:04--  [http://dlsvr03.asus.com/pub/ASUS/mb/socket939/A8V-VM_SE/linux_audio.rar](http://dlsvr03.asus.com/pub/ASUS/mb/socket939/A8V-VM_SE/linux_audio.rar)
           => `linux_audio.rar'
Resolving dlsvr03.asus.com... 205.158.107.131
Connecting to dlsvr03.asus.com|205.158.107.131|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

tr@tr:~/Desktop$ sudo apt-get update
[sudo] password for tr:
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015) gutsy/main Translation-en_US
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015) gutsy/multiverse Translation-en_US
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015) gutsy/restricted Translation-en_US
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015) gutsy/universe Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US         
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Fetched 3B in 0s (3B/s)  
Reading package lists... Done
tr@tr:~/Desktop$ 
tr@tr:~/Desktop$ 



---

### Post by aysiu on 2007-10-28
What about the rest of the commands? ```
sudo apt-get install unrar
unrar e linux_audio.rar
ls
cat Readme.txt
```

---

### Post by discmaster on 2007-10-28
See, told you I didn't know what I was doing! :lolflag:
> tr@tr:~$ cd ~/Desktop
tr@tr:~/Desktop$ wget -c [http://dlsvr03.asus.com/pub/ASUS/mb/socket939/A8V-VM_SE/linux_audio.rar](http://dlsvr03.asus.com/pub/ASUS/mb/socket939/A8V-VM_SE/linux_audio.rar)
--20:49:00--  [http://dlsvr03.asus.com/pub/ASUS/mb/socket939/A8V-VM_SE/linux_audio.rar](http://dlsvr03.asus.com/pub/ASUS/mb/socket939/A8V-VM_SE/linux_audio.rar)
           => `linux_audio.rar'
Resolving dlsvr03.asus.com... 202.94.157.171
Connecting to dlsvr03.asus.com|202.94.157.171|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

tr@tr:~/Desktop$ sudo apt-get update
[sudo] password for tr:
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015) gutsy/main Translation-en_US
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015) gutsy/multiverse Translation-en_US
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015) gutsy/restricted Translation-en_US
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015) gutsy/universe Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US         
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Fetched 3B in 0s (3B/s)  
Reading package lists... Done
tr@tr:~/Desktop$ sudo apt-get install unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unrar is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tr@tr:~/Desktop$ unrar e linux_audio.rar

UNRAR 3.70 beta 3 freeware      Copyright (c) 1993-2007 Alexander Roshal


Extracting from linux_audio.rar

Extracting  alsa-driver-1.0.11-FC4-4.04c.tar.bz2                      OK 
Extracting  alsa-lib-1.0.9.tar.bz2                                    OK 
Extracting  alsa-utils-1.0.9a.tar.bz2                                 OK 
Extracting  install                                                   OK 
Extracting  modules.conf                                              OK 
Extracting  Readme.txt                                                OK 
Extracting  test.wav.bz2                                              OK 
Extracting  turbolinux.txt                                            OK 
Extracting  version                                                   OK 
Extracting  realtek-linux-audiopack-FC5-4.05b.tar.bz2                 OK 
Extracting  realtek-linux-audiopack-3.5-6b.tar.bz2                    OK 
Extracting  realtek-linux-audiopack-4.05b.tar.bz2                     OK 
Extracting  realtek-linux-audiopack-RHEL4U4-4.05b.tar.bz2             OK 
Extracting  alsa-driver-1.0.11-SLES-4.04c.tar.bz2                     OK 

alsa-lib-1.0.9.tar.bz2 already exists. Overwrite it ?
[Y]es, [N]o, [A]ll, n[E]ver, [R]ename, [Q]uit y

Extracting  alsa-lib-1.0.9.tar.bz2                                    OK 

alsa-utils-1.0.9a.tar.bz2 already exists. Overwrite it ?
[Y]es, [N]o, [A]ll, n[E]ver, [R]ename, [Q]uit Y

Extracting  alsa-utils-1.0.9a.tar.bz2                                 OK 

install already exists. Overwrite it ?
[Y]es, [N]o, [A]ll, n[E]ver, [R]ename, [Q]uit Y

Extracting  install                                                   OK 

modules.conf already exists. Overwrite it ?
[Y]es, [N]o, [A]ll, n[E]ver, [R]ename, [Q]uit Y

Extracting  modules.conf                                              OK 

Readme.txt already exists. Overwrite it ?
[Y]es, [N]o, [A]ll, n[E]ver, [R]ename, [Q]uit Y

Extracting  Readme.txt                                                OK 

test.wav.bz2 already exists. Overwrite it ?
[Y]es, [N]o, [A]ll, n[E]ver, [R]ename, [Q]uit Y

Extracting  test.wav.bz2                                              OK 

turbolinux.txt already exists. Overwrite it ?
[Y]es, [N]o, [A]ll, n[E]ver, [R]ename, [Q]uit Y

Extracting  turbolinux.txt                                            OK 

version already exists. Overwrite it ?
[Y]es, [N]o, [A]ll, n[E]ver, [R]ename, [Q]uit Y

Extracting  version                                                   OK 
All OK
tr@tr:~/Desktop$ ls
alsa-driver-1.0.11-FC4-4.04c.tar.bz2
alsa-driver-1.0.11-SLES-4.04c.tar.bz2
alsa-lib-1.0.9.tar.bz2
alsa-utils-1.0.9a.tar.bz2
Audio
install
linux_audio.rar
modules.conf
Readme.txt
realtek-linux-audiopack-3.5-6b.tar.bz2
realtek-linux-audiopack-4.05b.tar.bz2
realtek-linux-audiopack-FC5-4.05b.tar.bz2
realtek-linux-audiopack-RHEL4U4-4.05b.tar.bz2
sound card info
soundtest.jpg
test.wav.bz2
The Family Link Directory 1.25.07.xls
turbolinux.txt
version
tr@tr:~/Desktop$ cat Readme.txt
The source code copy from [www.alsa-project.org](www.alsa-project.org).      ver:3.3-4
Linux Source Code for ALC audio codec
Support Codec list:
====AC97 Codec=====
ALC100,100P
ALC200,200P
ALC650D
ALC650E
ALC650F
ALC650
ALC655
ALC653
ALC658
ALC658D
ALC850
ALC101
ALC202
ALC250
ALC203

====HD Audio codec ====
ALC260
ALC262
ALC660
ALC861
ALC880
ALC882
ALC883
ALC885
ALC888

Installation:
This Source Code is from [www.alsa-project.org](www.alsa-project.org).
For driver installation, please follow below steps. 

Automatic install:
execute

  ./install

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support (soundcore module, default turn on)

Step 3. Complied source code
        a. cd alsa-driver-1.0.xx
        b. ./configure
        c. make
        d. make install
        e. ./snddevices

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
        (Please refer to the attached modules.conf)
         
        snd-xxxx is the card ID.

        -- Azalia controller --ALC880 ALC882 ALC260 ALC262 ALC883 ALC885 ALC888
           --- Intel ICH6 ICH7 ---------
               snd-hda-intel
           --- ATI chipset -----
               snd-atiixp

        -- AC97 controller --ALC655 ALC650 ALC250 ALC255
           --- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
               snd-intel8x0
           --- Via8233 Via686a  -------------------------------    
               snd-via82xx
           --- ATI Chipset  -------------------------------
               snd-atiixp

        Copy and paste this to the bottom of your /etc/modules.conf or /etc/modprobe.conf file.
        # ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx     
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss

Step 5. reboot your machine

Step 6. Use the alsamixer the disable mute (All audio line default is mute)
        *Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer

Note:   1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2.
        2. Kernel Version must be 2.2.14 or later.
        3. All mixer channels are muted by default. You must use a native
                or OSS mixer program to unmute appropriate channels.
        4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.
        5. The driver added to support the SPDIF functoin. 
        6. a. You can download the alsa-lib-1.0.9 and alsa-utils-1.0.9a form the [www.alsa-project.org](www.alsa-project.org), then unzip and install them. 
           b. Suggest use "alsamixer" to control mixer function.
           c. Used "alsaconf" can autodetect which drive you need to install (step 4). 
        7. SUSE Distribution must install the ncurses package. 
tr@tr:~/Desktop$ 

---

### Post by aysiu on 2007-10-28
Okay. That's about as far as I can lead you. I've never successfully compiled anything from source before.

Anyone willing to pick up at this point?

---

