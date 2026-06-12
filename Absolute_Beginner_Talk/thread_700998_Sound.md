---
title: "Sound"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by supertails on 2008-02-18
How do I get my sound to work?

tails@tails-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
tails@tails-laptop:~$

---

### Post by spiderbatdad on 2008-02-18
could you post the output of ```
asoundconf list
```
also run ```
alsamixer
``` and make sure master and PCM are up.
These are some simple steps...it can get much more complicated,  unfortunately.

---

### Post by supertails on 2008-02-18
Card: HDA ATI SB
Chip: Generic ffff ID ffff
View: [Playback] Capture All
Item: Caller ID [Off]

Card: HDA ATI SB
Chip: Generic ffff ID ffff
View: [Playback] Capture All
Item: Off-hook [Off]

---

### Post by spiderbatdad on 2008-02-18
This may be the best bet. [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

scroll down to method B...manually rebuild alsa.

or you may be able to just add ```
sudo apt-get install linux-backports-modules-generic & sudo reboot
```

See this post also: [http://ubuntuforums.org/archive/index.php/t-570442.html](http://ubuntuforums.org/archive/index.php/t-570442.html)

I would try the second option first....linux-backports...

Regards

---

### Post by Hobo Joe on 2008-02-18
This has worked for me, it may not for you, but it's worth a shot.

```

sudo asoundconf set-default-card HDA ATI SB

```

---

### Post by spiderbatdad on 2008-02-18
> **Hobo Joe said:**
> This has worked for me, it may not for you, but it's worth a shot.

```

sudo asoundconf set-default-card HDA ATI SB

```

+1

---

### Post by supertails on 2008-02-18
tails@tails-laptop:~$ sudo asoundconf set-default-card HDA ATI SB
[sudo] password for tails:
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

You have omitted a necessary parameter.  Please see the output from `asoundconf list`, and use one of those sound card(s) as the parameter.

tails@tails-laptop:~$

---

### Post by Hobo Joe on 2008-02-18
Was what you posted above the ouput of this command?:

```

sudo asoundconf list

```

If not, paste it again, then we can go from there. If so... There's a problem.

---

### Post by supertails on 2008-02-18
tails@tails-laptop:~$ sudo asoundconf set-default-card HDA ATI SB
[sudo] password for tails:
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

You have omitted a necessary parameter.  Please see the output from `asoundconf list`, and use one of those sound card(s) as the parameter.

tails@tails-laptop:~$ sudo asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
SB
tails@tails-laptop:~$ sudo asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
SB
tails@tails-laptop:~$

---

### Post by spiderbatdad on 2008-02-18
I dont think you are going to be able to set the module for the card using asoundconf set-default-card SB...I would try adding the backports I suggested in my second post. If that doesn't work, you may need to follow the tutorial to rebuild alsa.

---

### Post by Hobo Joe on 2008-02-18
Ahh, ok, I see now. The command would then be this:
```

sudo asoundconf set-default-card SB

```

That should work, as it's a similar model to my card, and it worked for me. But it's possible that it doesn't, in that case, I'd follow Spiderbatdad's advice.

---

### Post by supertails on 2008-02-18
linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.37.1_i386.deb How do I uninstall that?

```
tails@tails-laptop:~$ sudo asoundconf set-default-card HDA ATI SB
[sudo] password for tails:
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

You have omitted a necessary parameter.  Please see the output from `asoundconf list`, and use one of those sound card(s) as the parameter.

tails@tails-laptop:~$ sudo asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
SB
tails@tails-laptop:~$ sudo asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
SB
tails@tails-laptop:~$ sudo apt-get install update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package update
tails@tails-laptop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017) gutsy/restricted Translation-en_US
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:2 http://us.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release
Hit http://security.ubuntu.com gutsy-security/main Packages         
Hit http://us.archive.ubuntu.com gutsy-updates Release              
Hit http://security.ubuntu.com gutsy-security/restricted Packages   
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/main Packages
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Fetched 3B in 1s (2B/s)
Reading package lists... Done
tails@tails-laptop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017) gutsy/restricted Translation-en_US
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Get:2 http://us.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Hit http://security.ubuntu.com gutsy-security/main Packages
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release 
Hit http://us.archive.ubuntu.com gutsy-updates Release              
Hit http://security.ubuntu.com gutsy-security/restricted Packages   
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/main Packages
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Fetched 3B in 1s (2B/s)
Reading package lists... Done
tails@tails-laptop:~$ sudo asoundconf set-default-card SB
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

tails@tails-laptop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017) gutsy/restricted Translation-en_US
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:2 http://us.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release
Hit http://security.ubuntu.com gutsy-security/main Packages         
Hit http://us.archive.ubuntu.com gutsy-updates Release
Hit http://security.ubuntu.com gutsy-security/restricted Packages   
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/main Packages
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Fetched 3B in 1s (3B/s)
Reading package lists... Done
tails@tails-laptop:~$ sudo asoundconf set-default-card SB
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

tails@tails-laptop:~$ ^M
: command not found
tails@tails-laptop:~$ sudo asoundconf set-default-card SB
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

tails@tails-laptop:~$ sudo uninstall linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.37.1_i386.deb
sudo: uninstall: command not found
tails@tails-laptop:~$ 
tails@tails-laptop:~$ 

```

---

### Post by spiderbatdad on 2008-02-18
```
sudo dpkg -r linux-ubuntu-modules-2.6.22-14-generic
```

---

### Post by Hobo Joe on 2008-02-18
I might be wrong, but that looks like the Linux kernel, I don't know why you'd have that .deb sitting on your computer.

Unless you opened the .deb and installed though, there should be nothing to uninstall.

---

### Post by supertails on 2008-02-18
```
 tails@tails-laptop:~$ sudo dpkg -r linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.37.1_i386.deb
[sudo] password for tails:
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
tails@tails-laptop:~$ 



```

---

### Post by spiderbatdad on 2008-02-18
yeah sorry about that...not thinking well tonight. Changed the command for previous post. You should also be able to remove it from synaptic...but as HOBO JO says, if you haven't installed it, you can just trash it.

---

### Post by Hobo Joe on 2008-02-18
Out of curiosity, where did that come from and why are you trying to install/uninstall it?

---

### Post by supertails on 2008-02-18
I own a Toshiba and in the code section it says what do to and the install didn't work. 

```
Method E: Patch to add support for Realtek ALC268 Codec to Alsa 1.0.14

    *

      Does work: [WWW] Acer TravelMate 6292, Compal IFL90, MSI PR200, Extensa 5620, Toshiba A215-S7437
    *

      Does not work:

Support provided :

    *

      Internal speaker works
    *

      Headphones works (and internal speakers are automuted correctly)
    *

      External speaker works (and internal speakers are automuted correctly)
    *

      Internal mic doesn't seem to work...
    *

      External mic untested.

Procedure (See [WWW] #116326) :

    *

      Rebuild the linux-ubuntu-modules-2.6.22 packages after applying this [WWW] patch
      Or use this already pacthed,ready to install, [WWW] linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.37.1_i386.deb.
      Note: It only works with an up-to-date Gutsy.
    *

      Add the following line in /etc/modprobe.d/alsa-base:

      options snd-hda-intel model=acer

      Note: You can specify one of the following model : acer, toshiba, 3stack or auto Note 2: For MSI PR200, use model=targa-dig
    *

      Reboot

```

---

