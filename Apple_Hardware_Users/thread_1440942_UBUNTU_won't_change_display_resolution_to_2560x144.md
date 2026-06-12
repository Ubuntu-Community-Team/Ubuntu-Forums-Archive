---
title: "UBUNTU won't change display resolution to 2560x1440 on an iMac 27&quot;"
date: 2010-03-28
forum: Apple Hardware Users
---

### Post by trujillr on 2010-03-28
I recently purchased an iMac 27" i7 with 8GB RAM, however after i installed UBUNTU i can't seen to find a way to set my display resolution to 2560 x 1440.
Any help will be greatly appreciated.

This is my second try on UBUNTU, the first time i was happy but disappointed on how difficult changing settings could be, this time seems not to be any different.

---

### Post by realzippy on 2010-03-28
...have you enabled the ATI fglrx driver?Have a look:

[http://ubuntuforums.org/showthread.php?t=1341331](http://ubuntuforums.org/showthread.php?t=1341331)

---

### Post by trujillr on 2010-03-28
I went to System -->  Administration -->  hardware drivers and nothing shows...

i downloaded the ati driver 10-3x86.x86_64 and nothing seems to happen.

what else do you suggest?

---

### Post by trujillr on 2010-03-28
i also tried this:

raultrujillo@ubuntu:~$ sudo aptitude install xorg-driver-fglrx
[sudo] password for raultrujillo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

but as you can see nothing happens.

---

### Post by realzippy on 2010-03-28
Have you updated your sources?

```
sudo apt-get update
```

then again

```
jockey-gtk
```

---

### Post by trujillr on 2010-03-28
this is what i got:

raultrujillo@ubuntu:~$ sudo apt-get update
[sudo] password for raultrujillo: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/universe Packages
Reading package lists... Done
raultrujillo@ubuntu:~$ jockey-gtk


and then i got the Hardware Drivers windows completely empty.

also, after installing the drivers for ATI i went to System -- Preferences -- Display and i got the folllowing message:

It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?  
giving me the choices of : NO     and      YES

when i click on YES i get the following messsage:

There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
No ATI graphics driver is installed, or ATI driver is not functioning properly.
Please install the ATI driver appropriate for your ATI hardware, or configure using aticonfig.


any more ideas? thanks by the way for your help

---

### Post by realzippy on 2010-03-28
run

```
sudo apt-get upgrade
```

then again

```
jockey-gtk
```

still no drivers there?

---

### Post by trujillr on 2010-03-28
this is what i got:

raultrujillo@ubuntu:~$ sudo apt-get upgrade
[sudo] password for raultrujillo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
raultrujillo@ubuntu:~$ jockey-gtk


nothing buddy...i get a blank list

---

### Post by realzippy on 2010-03-28
can you post your

/etc/X11/xorg.conf file ? (if exists)

```
gedit /etc/X11/xorg.conf
```

---

### Post by trujillr on 2010-03-28
this is what i get:

raultrujillo@ubuntu:~$ gedit /etc/X11/xorg.conf

it opens xorg.conf (/etc/X11) - gedit
but is blank... am i suppose to see something?
[IMG]file:///home/raultrujillo/Desktop/Screenshot-raultrujillo@ubuntu:%20%7E.png[/IMG][IMG]file:///home/raultrujillo/Desktop/Screenshot-raultrujillo@ubuntu:%20%7E.png[/IMG]

---

### Post by trujillr on 2010-03-28
i tried to past a picture... so disregard the IMG file

---

### Post by realzippy on 2010-03-28
...if it is blank,it does not exist,what means fglrx is not installed .
What happens if you try to install *xorg-driver-fglrx* from synaptic?

---

### Post by linuxopjemac on 2010-03-28
I would stick to open source, I am not sure whether the ATI driver supports dual head for the x1600 very well...

---

### Post by trujillr on 2010-03-28
i went to synaptic and i did a search on xorg and i noticed that xorg-driver-fglrx had a green square box so i installed the xorg-driver-fglrx-dev...
 after i installed i did the previous process : 
gedit /etc/X11/xorg.conf but nothing shows...
this is getting aggrevating...
no complains to you, i know you trying your best to help... but

---

### Post by realzippy on 2010-03-28
what does

```
fglrxinfo
```

say?

---

### Post by trujillr on 2010-03-28
this:

raultrujillo@ubuntu:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16

---

### Post by realzippy on 2010-03-28
..last attempt:

```
sudo aticonfig --initial
```

then reboot

---

### Post by trujillr on 2010-03-28
i didn't reboot yet but this is waht i get:
raultrujillo@ubuntu:~$ sudo aticonfig --initial
aticonfig: No supported adapters detected
raultrujillo@ubuntu:~$

---

### Post by trujillr on 2010-03-28
i just rebooted... but nothing has changed.

---

### Post by realzippy on 2010-03-28
Well,do you have an ATI card???

```
lspci |grep VGA
```

---

### Post by trujillr on 2010-03-28
lol... i do.

this is what i got:
raultrujillo@ubuntu:~$ lspci |grep VGA
01:00.0 VGA compatible controller: Device 1ab8:4005
raultrujillo@ubuntu:~$ 

from my about this mac this is the onformation i have:
ATI Radeon HD 4850:
Chipset Model:  ATI Radeon HD 4850
Type: GPU
Bus: PCIe
PCIe Lane width: x16
VRAM (total: 512 MB
Imac:
     Resolution: 2560 x 1440
     Pixel Depth:  32 Bit Color (ARGB8888)

hope this help.

---

### Post by realzippy on 2010-03-28
Hm,expected something like :

lspci
02:00.0 VGA compatible controller: ATI Technologies Inc RVXXX PRO [Radeon HD 4850]

...please try.

```
glxinfo | grep vendor
```

---

### Post by trujillr on 2010-03-28
sorry for the delay...
this is what i got:
raultrujillo@ubuntu:~$ glxinfo | grep vendor
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16
raultrujillo@ubuntu:~$

---

### Post by realzippy on 2010-03-28
Since AFAIK you have an ATI chipset and according to e.g. :

[http://www.technicaljar.com/?p=267](http://www.technicaljar.com/?p=267)

it should work out of the box,I have no idea.Maybe a
jockey (restricted-driver-manager) bug?The ATI driver should be available,but somehow your card is not recognized..
You seemed to have run a downloaded ATI.run installer,what might have caused troubles with kernel modules..yet an assumption.
Maybe fastest thing is to make a clean install,update and upgrade before installing anything and hope jockey will offer a driver.
If there is no way setting up the fglrx driver,you could
keep your running (free) driver and set the resolution with
*xrandr*.

---

### Post by trujillr on 2010-03-28
i will uninstall ubuntu and will install it again and will be back to this forum to get instruction on where do i start.
See you in a little bit.

---

### Post by realzippy on 2010-03-28
Sorry for the question,but we talk about a "real" ubuntu install,not about
install in "Parallels" ???

---

### Post by jbuhl on 2010-04-01
I am interested in this thread as well.  I have Ubuntu 9.1 running as a guest inside Sun/Oracle Virtual box on a 24" iMac and would also like to take advantage of full screen.

I successfully ran Suse 11.2 with a larger screen size with the KDE4 desktop.  But I bailed off that as I had problems with the network manager.  When I went to the Gnome desktop in Suse I have the same issue with Ubuntu with only 800 x 600 screen size available.  I will try some of the same methods suggested here tonight and report back.

jb

---

### Post by jbuhl on 2010-04-01
On the second page are instructions that may be relevant.

[http://5z8.info/racist-raps_s7u4s_amazon.com-phish](http://5z8.info/racist-raps_s7u4s_amazon.com-phish)

---

