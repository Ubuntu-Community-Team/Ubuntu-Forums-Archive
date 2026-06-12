---
title: "Sound Issues - wats a ´tar xfvj alcsound.tar.bz2´ ?????"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Scarath on 2007-06-27
Hi
Trying to install some sound drivers cos my sound doesnt work.
I have the driver on CD (came with the mobo) but nowhere can i find the tar xfvj alcsound.tar.bz2 file. 
I have read a few posts on the subject of sound and this tar xfvj alcsound.tar.bz2 seems to pop up a few times but I cant find it. 

I have tried using the #aptitude thing but have had no luck. 

Its a bit frustrating as my drivers are sitting there on my CD and i cant .configure them without this file .... which doesnt exist on my CD.

I sure i missing something simple but dont know what as i new to this.

any advice would be great thanks :) 

btw

my README instructions read as follows: 

Step 1. unzip source code

        tar xfvj alcsound.tar.bz2



Step 2. Turn on sound support (soundcore module, default turn on)



Step 3. Complied source code

	a. ./configure

	b. make

	c. make install

	d. ./snddevices



Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution

 	(Please refer to the attached modules.conf)



Step 5. reboot your machine



Note: 	1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt 
		in the alcsound.tar.bz2.

	2. Kernel Version must be 2.2.14 or later.

	3. All mixer channels are muted by default. You must use a native

		or OSS mixer program to unmute appropriate channels.

	4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.

	5. The driver added to support the SPDIF functoin. 	

	6. Suggest use alsamixer to control mixer function. you can find it in the alsa-utils-0.9.4 ([www.alsa-project.org](www.alsa-project.org)).

---

### Post by meatpan on 2007-06-27
> **Scarath said:**
> 
I have read a few posts on the subject of sound and this tar xfvj alcsound.tar.bz2 seems to pop up a few times but I cant find it. 


There is only one file, alcsound.tar.bz2, referenced by the documentation.  the 'tar xfvj' portion is a command you need to run on the specified file.

> 
I have tried using the #aptitude thing but have had no luck. 


What did you try?  The reason I ask is because installing the proper sound drivers and controllers via aptitude is going to be *much* easier than managing a source installation.  This is particularly true when it comes time to uninstall files and flush the kernel of any additional modules.

Troubleshooting sound can be a bit tricky becuase there are several layers of software that might be causing the problem.  I think you are on the right track, but need to show the steps you took using aptitude.  Also, it will help to post the type of soundcard you have.  Try running 'lspci -vv' from a command line, and finding the sound card entry (This command will output a bunch of useful info about your motherboard and add-in cards).  Post the sound card info.  The reason I ask is because sometimes motherboard and peripheral manufactures change the chipset on their products without notification.  This causes problems because the existing how-to documentation for a linux driver might be obsoleted as a result.

---

### Post by dreadlord_chris on 2007-06-27
the file you are looking for is **alcsound.tar.bz2** - it's a compressed file (kinda like a .zip file) that you use the program **tar** to extract with.
So,
```

tar xfvj alcsound.tar.bz2

```
tells **tar** to extract **alcsound.tar.bz2** with the *options* **xfvj** - which break down too:
**x** = Extract
**f** = file mode (use the file listed on the command line)
**v** = verbose (print a bunch of stuff to the screen)
**j** = the file is comressed, pipe thru bzip2 first

---

### Post by Scarath on 2007-06-27
thanks for the reply.

alcsound.tar.bz2 - also doesnt seem to exist in the file or on the CD.

I found this forum on the subject, this guy couldnt find the file either:

> [http://www.linuxquestions.org/questions/showthread.php?t=518391](http://www.linuxquestions.org/questions/showthread.php?t=518391)

aptitude - I went Virtual Packages, then found the #alsa thing and tried to install but it told me i already had them. How would I use #aptitude to install the drivers which I got with my mobo CD?

btw - the linux drivers came zipped-up on the CD (official Nvidia Nforce cd), i unzipped them to my home file. (I was shocked to find linux drivers on there)

I did the 'lspci -vv' and this was all that seemed to have any relation to my sound: 

 Audio Codec    Realtek ALC850 

> 
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ae
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (500ns min, 1250ns max)
        Interrupt: pin A routed to IRQ 17
        Region 0: I/O ports at dc00 [size=256]
        Region 1: I/O ports at e000 [size=256]
        Region 2: Memory at d3003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

thanks again

---

### Post by Scarath on 2007-06-27
bump

---

### Post by meatpan on 2007-06-27
Ok, here are some more ideas.

It seems like you might benifit from installing a few more alsa packages.  If you run 'dpkg -l alsa-base', what happens? (btw, dpkg is a handy tool to view installed packages)  If you don't have it, let us know and try to install via 'apt-get install alsa-base'.  While you are at it, check to see if you have 'alsa-tools-gui'.  This package is a handy gui interface for alsa configuration.  If you dont have the gui package, 'apt-get install alsa-tools-gui'.

Once these two packages are installed, try starting up the gui.  I'm not sure what the command name is for the gui, so you will have to search around.  'dpkg -L alsa-tools-gui' should list all the files related to the package, so you could probably see which are installed in /bin or /usr/bin.  Its probably obvious ;)

The gui will hopefully list your sound card (I bet it will, because lspci -vv seemed to identify it), and allow you to test it.

---

### Post by Scarath on 2007-06-27
Thanks

when i dpkg -l alsa base i get

> Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  alsa-base      1.0.13-3ubuntu ALSA driver configuration files
matt@matt-desktop:~$ 

wierd no? 

anyway I&#314;l try all those things you listed and see if they help

---

### Post by Scarath on 2007-06-27
Hi
thanks again
So i checked my synap package manager and it said all my alsa stuff was installed, i reinstalled them jst to make sure.

when i 'dpkg -L alsa-tools-gui' i got this ...

> /.
/usr
/usr/bin
/usr/bin/echomixer
/usr/bin/envy24control
/usr/bin/hdspconf
/usr/bin/hdspmixer
/usr/bin/rmedigicontrol
/usr/share
/usr/share/doc
/usr/share/doc/alsa-tools-gui
/usr/share/doc/alsa-tools-gui/echomixer
/usr/share/doc/alsa-tools-gui/echomixer/AUTHORS
/usr/share/doc/alsa-tools-gui/echomixer/README
/usr/share/doc/alsa-tools-gui/envy24control
/usr/share/doc/alsa-tools-gui/envy24control/AUTHORS
/usr/share/doc/alsa-tools-gui/envy24control/README
/usr/share/doc/alsa-tools-gui/envy24control/README.profiles.gz
/usr/share/doc/alsa-tools-gui/hdspconf
/usr/share/doc/alsa-tools-gui/hdspconf/AUTHORS
/usr/share/doc/alsa-tools-gui/hdspconf/README
/usr/share/doc/alsa-tools-gui/hdspmixer
/usr/share/doc/alsa-tools-gui/hdspmixer/AUTHORS
/usr/share/doc/alsa-tools-gui/hdspmixer/README
/usr/share/doc/alsa-tools-gui/hdspmixer/TODO
/usr/share/doc/alsa-tools-gui/hdspmixer/NEWS.gz
/usr/share/doc/alsa-tools-gui/rmedigicontrol
/usr/share/doc/alsa-tools-gui/rmedigicontrol/AUTHORS
/usr/share/doc/alsa-tools-gui/rmedigicontrol/README
/usr/share/doc/alsa-tools-gui/rmedigicontrol/NEWS.gz
/usr/share/doc/alsa-tools-gui/changelog.gz
/usr/share/doc/alsa-tools-gui/copyright
/usr/share/doc/alsa-tools-gui/changelog.Debian.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/envy24control.1.gz
/usr/share/pixmaps
/usr/share/pixmaps/hdspconf.png
/usr/share/pixmaps/hdspmixer.png
/usr/share/applications
/usr/share/applications/hdspconf.desktop
/usr/share/applications/hdspmixer.desktop
/usr/share/menu
/usr/share/menu/alsa-tools-gui

sorry to be dumb but i see no sign of my sound card ... am i looking in the right place? Probably not lol#-o

thanks for the help!

---

### Post by GFC2 on 2007-07-06
'dpkg -L alsa-tools-gui' refers to the GUI package for managing ALSA, not your hardware.  Next step is to get the GUI tool up and running.

---

