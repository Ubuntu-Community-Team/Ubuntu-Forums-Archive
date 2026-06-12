---
title: "Amsn"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by BabyBoy on 2006-02-20
does anybody have any idea i can get AMSN on my ubuntu newest one, :S i downloaded the ubuntu.deb and powerpc one.... no luck with either of them any idea on what to do, thanks

BabyBoy.

---

### Post by heimo on 2006-02-20
There's 0.94 in [universe]("https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages") which can can installed using [Synaptic]("https://wiki.ubuntu.com/SynapticHowto").

[Automatix]("http://www.ubuntuforums.org/showthread.php?t=66563") can install 0.95



EDIT: Fixed link.

---

### Post by patrick295767 on 2006-02-21
Download this:
[http://prdownloads.sourceforge.net/amsn/amsn_0.95-3.ubuntu.deb](http://prdownloads.sourceforge.net/amsn/amsn_0.95-3.ubuntu.deb)
  
And :
```
sudo apt-get -f -y install amsn
```
```
sudo dpkg -i amsn_0.95-3.ubuntu.deb
```
  
That should make it normally.
(You'd need Ubuntu 5.10 Breezy )
Greetz

Patrick

---

### Post by BabyBoy on 2006-02-21
yup i have breezy 5.10 but it says E: cannot find package... :S

---

### Post by heimo on 2006-02-21
[quote=BabyBoy]yup i have breezy 5.10 but it says E: cannot find package... :S[/quote]

Then it's probably because it's in universe and you haven't enabled it?
[https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages](https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages)

---

### Post by BabyBoy on 2006-02-21
ah yes seems to have sorted it thank heimo :) and the rest of you.

---

### Post by patrick295767 on 2006-02-21
Enjoy the chat & the webcam !!
By the way which webcam are u using ? 
(cos I didnt get a lot of reply to this post [http://www.ubuntuforums.org/showthread.php?t=121889&highlight=plug](http://www.ubuntuforums.org/showthread.php?t=121889&highlight=plug))

Greetz

Pat'

---

### Post by BabyBoy on 2006-02-21
funny enough i also have webcam logitech quickcam thing lol............ :P

grey stand white cam grey around lense :P

---

### Post by patrick295767 on 2006-02-21
[QUOTE=BabyBoy]funny enough i also have webcam logitech quickcam thing lol............ :P

grey stand white cam grey around lense :P[/QUOTE]

Is it working ur webcam with amsn ? 
 
 
   
--
Camorama too ?
[http://camorama.fixedgear.org/](http://camorama.fixedgear.org/)
```
apt-get -f -y install camorama
```
--
(To install it, this webcam, ... a script is required... )
--
I tried thsi webcam with the macintosh, it's not automatically detected.

---

### Post by BabyBoy on 2006-02-21
no the package manager downloaded the amsn 0.94 :(! 
going to have to upgrade first, :)

---

### Post by patrick295767 on 2006-02-21
[QUOTE=BabyBoy]no the package manager downloaded the amsn 0.94 :(! 
going to have to upgrade first, :)[/QUOTE]
```
sudo dpkg -i amsn_0.95-3.ubuntu.deb
```

Ok, let me know when installed ...

---

### Post by BabyBoy on 2006-02-21
okie got msn 9.5 so i have to install Camorama to get my cam working
this is the one i have 

[IMG]http://www.logitech.com/lang/images/0/960.gif[/IMG]



thanks, :-D

---

### Post by BabyBoy on 2006-02-21
Deleted!

---

### Post by BabyBoy on 2006-02-21
i found driver for the quickcam messenger.... the link is 

[http://home.mag.cx/messenger/](http://home.mag.cx/messenger/)

anyone tell me how to install this under ubuntu?

i done what it said in readme file i go nowhere..


thanks.

---

### Post by patrick295767 on 2006-02-21
```
apt-get update
apt-get upgrade
apt-get -f -y install camorama
apt-get -f -y install amsn
dpkg -i amsn_0.95-3.ubuntu.deb
```

Then u have to get the script:[http://www.ubuntuforums.org/showthread.php?t=94588&highlight=quickcam.sh](http://www.ubuntuforums.org/showthread.php?t=94588&highlight=quickcam.sh)

Let me know ab. ur progress !

Greetz

Pat'

---

### Post by patrick295767 on 2006-02-27
Hi Hi, 
  
I followed this on a fresh installation to install the "logitech quickcam express".

I did that : 
> 
Le driver webcam qui marche pour kernel 2.4 et 2.6.X:
[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

- spca5xx-date_du_driver.tar.gz
- prenez aussi un peu plus bas le spcagui-date_de_release.tar.gz, ca permettra de tester facilement la cam

(from [http://forum.ubuntu-fr.org/viewtopic.php?id=8157](http://forum.ubuntu-fr.org/viewtopic.php?id=8157))
   
  
then, 
```
mknod /dev/video0 c 81 0
mknod /dev/video1 c 81 1
chmod a+rw /dev/video0
ln -s /dev/video0 /dev/video
```
  worked fine cos of 
```
6- a ce moment là, si tout c'est bien passé tapez dans la console : « lsmod | grep spca »
Vous devriez obtenir quelque chose comme :

spca5xx        301592    0
videodev        7168         spca5xx
usbcore        93176        5 spca5xx,usbhid,ehci_hcd,ohci_hcd
```
   
  
But I cannot do: 
```
 7- Compilation de spcagui (une intrerface graphique minime pour afficher et controler la video de la webcam)
lisez ce qui est ecrit dans le readme et dans le rep de doc...
make
make install
```
to compile teh sapgui
I get some errors 
  
when I try camorama, my linux freeeeze and I have to do a cold reset of th  pc !
What to do ? 

Someone knows the problem ?

Thank you, 

Patrick

---

### Post by patrick295767 on 2006-02-27
That 's my error messasge, when I do make in the spcagui20050918 folder :

```
/spcagui20050918# make
make: sdl-config: Command not found
cc -DUSE_SDL -O2 -DLINUX  -DHAVE_LIBJPEG=1   -c -o spcagui.o spcagui.c
In file included from spcagui.c:23:
gui.h:11:21: error: SDL/SDL.h: No such file or directory
gui.h:12:23: error: SDL_image.h: No such file or directory
In file included from spcagui.c:23:
gui.h:41: error: syntax error before ‘SDL_Surface’
gui.h:41: warning: no semicolon at end of struct or union
gui.h:42: warning: data definition has no type or storage class
gui.h:43: error: syntax error before ‘}’ token
gui.h:51: error: syntax error before ‘SDL_Surface’
gui.h:51: warning: no semicolon at end of struct or union
gui.h:52: warning: data definition has no type or storage class
gui.h:53: error: syntax error before ‘}’ token
gui.h:63: error: syntax error before ‘SDL_Surface’
gui.h:63: warning: no semicolon at end of struct or union
gui.h:64: warning: data definition has no type or storage class
gui.h:65: error: syntax error before ‘*’ token
gui.h:65: warning: data definition has no type or storage class
gui.h:66: error: syntax error before ‘*’ token
gui.h:66: warning: data definition has no type or storage class
gui.h:67: error: syntax error before ‘}’ token
gui.h:76: error: syntax error before ‘SDL_Surface’
gui.h:79: error: syntax error before ‘SDL_Surface’
gui.h:87: error: syntax error before ‘SDL_Surface’
gui.h:90: error: syntax error before ‘SDL_Surface’
gui.h:99: error: syntax error before ‘SDL_Surface’
gui.h:102: error: syntax error before ‘SDL_Surface’
gui.h:105: error: syntax error before ‘SDL_Surface’
spcagui.c:54: error: array type has incomplete element type
spcagui.c:224: error: syntax error before ‘SDL_Surface’
spcagui.c: In function ‘refresh_screen’:
spcagui.c:227: error: ‘myframe’ undeclared (first use in this function)
spcagui.c:227: error: (Each undeclared identifier is reported only once
spcagui.c:227: error: for each function it appears in.)
spcagui.c:227: error: ‘vd’ undeclared (first use in this function)
spcagui.c:238: error: ‘Screen’ undeclared (first use in this function)
spcagui.c: In function ‘telecom’:
spcagui.c:289: error: ‘SDL_Surface’ undeclared (first use in this function)
spcagui.c:289: error: ‘screen’ undeclared (first use in this function)
spcagui.c:291: error: ‘Uint32’ undeclared (first use in this function)
spcagui.c:291: error: syntax error before ‘video_flags’
spcagui.c:292: error: ‘SDL_Event’ undeclared (first use in this function)
spcagui.c:295: error: ‘lib_flags’ undeclared (first use in this function)
spcagui.c:295: error: ‘SDL_INIT_VIDEO’ undeclared (first use in this function)
spcagui.c:297: error: ‘video_flags’ undeclared (first use in this function)
spcagui.c:297: error: ‘SDL_HWPALETTE’ undeclared (first use in this function)
spcagui.c:297: error: ‘SDL_DOUBLEBUF’ undeclared (first use in this function)
spcagui.c:329: error: ‘event’ undeclared (first use in this function)
spcagui.c:332: error: ‘SDL_MOUSEMOTION’ undeclared (first use in this function)
spcagui.c:368: error: ‘SDL_MOUSEBUTTONUP’ undeclared (first use in this function)
spcagui.c:376: error: ‘SDL_MOUSEBUTTONDOWN’ undeclared (first use in this function)
spcagui.c:403: error: invalid use of undefined type ‘struct control’
spcagui.c:408: error: invalid use of undefined type ‘struct control’
spcagui.c:409: error: invalid use of undefined type ‘struct control’
spcagui.c: In function ‘processvideo’:
spcagui.c:504: error: ‘SDL_Surface’ undeclared (first use in this function)
spcagui.c:504: error: ‘screen’ undeclared (first use in this function)
spcagui.c:505: error: ‘Uint32’ undeclared (first use in this function)
spcagui.c:505: error: syntax error before ‘video_flags’
spcagui.c:506: error: ‘SDL_Event’ undeclared (first use in this function)
spcagui.c:508: error: ‘lib_flags’ undeclared (first use in this function)
spcagui.c:508: error: ‘SDL_INIT_VIDEO’ undeclared (first use in this function)
spcagui.c:509: error: ‘video_flags’ undeclared (first use in this function)
spcagui.c:509: error: ‘SDL_HWPALETTE’ undeclared (first use in this function)
spcagui.c:509: error: ‘SDL_DOUBLEBUF’ undeclared (first use in this function)
make: *** [spcagui.o] Error 1

```

---

### Post by patrick295767 on 2006-02-27
I installed : 
   
```
apt-get -f -y install libsdl1.2-dev
``` 
   to correct my previous error message...
it's better, but 
  
  
I get now such error:
```
make
cc -DUSE_SDL -O2 -DLINUX -I/usr/include/SDL -D_REENTRANT -DHAVE_LIBJPEG=1   -c -o spcagui.o spcagui.c
In file included from spcagui.c:23:
gui.h:12:23: error: SDL_image.h: No such file or directory
make: *** [spcagui.o] Error 1

```

... some idea for the webcam ... 
?

THank you

---

### Post by dvarsam on 2006-02-27
Dear "BabyBoy":

If you get your camera fixed, please inform us, cause I want to buy a camera too, that can work with my Ubuntu...

So, it is very important to tell us, if you finally manage to make it work...

I have a "Trust 380 USB 2.0 Spacec@m" & I do not think I will be able to make it work.

---

### Post by arnieboy on 2006-02-27
follow this howto to make ur cam work:
[http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284)

---

### Post by patrick295767 on 2006-02-27
[QUOTE=arnieboy]follow this howto to make ur cam work:
[http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284)[/QUOTE]
  
Thank you for your help arnie !!
  
It's now since 2-3 months that  I started to try installing this webcam ... 
Maybe one day ... :-)
  
Thx, I'll try tomorrow. We'll see the resutls...
Everyday is progressing under linux, ... everyday one step further ... 

Patrick

---

### Post by patrick295767 on 2006-02-27
[QUOTE=dvarsam]Dear "BabyBoy":

If you get your camera fixed, please inform us, cause I want to buy a camera too, that can work with my Ubuntu...

So, it is very important to tell us, if you finally manage to make it work...

I have a "Trust 380 USB 2.0 Spacec@m" & I do not think I will be able to make it work.[/QUOTE]
  
I started a post concerning webcam plug&see wihtout compiling ... Not much interest by users in forum ... 
  
I got several replies:
two webcams are available (repos. and  spacecam etrust)...  as mentioned here :[http://www.ubuntuforums.org/showthread.php?t=64557&page=9](http://www.ubuntuforums.org/showthread.php?t=64557&page=9)

Greetings,

Patrick

---

### Post by patrick295767 on 2006-02-27
I runned your script : 
(thank you arnie)
```
#!/bin/bash
apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r`
apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20060202.tar.gz
tar xvfz spca5xx-20060202.tar.gz
cd spca5xx-20060202
make CC=gcc-3.4
modprobe -r spca5xx
rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
make install
modprobe spca5xx

```
  
Then, got the following, no error:
```

root@Laptop06:~# ./arnie.sh
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.12-9-386 is already the newest version.
linux-restricted-modules-2.6.12-9-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.12-9-386 is already the newest version.
linux-restricted-modules-2.6.12-9-386 is already the newest version.
build-essential is already the newest version.
gcc-3.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
--01:09:17--  http://mxhaard.free.fr/spca50x/Download/spca5xx-20060202.tar.gz
           => `spca5xx-20060202.tar.gz.2'
Resolving mxhaard.free.fr... 212.27.63.122
Connecting to mxhaard.free.fr|212.27.63.122|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 193,391 (189K) [application/x-gzip]

100%[====================================>] 193,391      221.40K/s

01:09:18 (220.92 KB/s) - `spca5xx-20060202.tar.gz.2' saved [193391/193391]

spca5xx-20060202/
spca5xx-20060202/Makefile
spca5xx-20060202/LICENSE
spca5xx-20060202/RGB-YUV%2fmodule-setting
spca5xx-20060202/README
spca5xx-20060202/drivers/
spca5xx-20060202/drivers/usb/
spca5xx-20060202/drivers/usb/spcagamma.h
spca5xx-20060202/drivers/usb/cx11646.h
spca5xx-20060202/drivers/usb/sn9cxxx.h
spca5xx-20060202/drivers/usb/pac207.h
spca5xx-20060202/drivers/usb/cxlib.h
spca5xx-20060202/drivers/usb/zc3xx.h
spca5xx-20060202/drivers/usb/cs2102.h
spca5xx-20060202/drivers/usb/jpeg_qtables.h
spca5xx-20060202/drivers/usb/pas106b.h
spca5xx-20060202/drivers/usb/spca506.h
spca5xx-20060202/drivers/usb/spca561.h
spca5xx-20060202/drivers/usb/mr97311.h
spca5xx-20060202/drivers/usb/sonix.h
spca5xx-20060202/drivers/usb/spca5xx.c
spca5xx-20060202/drivers/usb/spca5xx.h
spca5xx-20060202/drivers/usb/spcausb.h
spca5xx-20060202/drivers/usb/icm105a.h
spca5xx-20060202/drivers/usb/hv7131b.h
spca5xx-20060202/drivers/usb/hv7131c.h
spca5xx-20060202/drivers/usb/spca501_init.h
spca5xx-20060202/drivers/usb/pb0330.h
spca5xx-20060202/drivers/usb/ov7630c.h
spca5xx-20060202/drivers/usb/et61xx51.h
spca5xx-20060202/drivers/usb/sp5xxfw2.h
spca5xx-20060202/drivers/usb/jpeg_header.h
spca5xx-20060202/drivers/usb/spca508_init.h
spca5xx-20060202/drivers/usb/spcaCompat.h
spca5xx-20060202/drivers/usb/dummy_cam.h
spca5xx-20060202/drivers/usb/spcadecoder.c
spca5xx-20060202/drivers/usb/spcadecoder.h
spca5xx-20060202/drivers/usb/tas5130c.h
spca5xx-20060202/drivers/usb/sp5xxfw2.dat
spca5xx-20060202/drivers/usb/hdcs2020.h
spca5xx-20060202/drivers/usb/spca505_init.h
spca5xx-20060202/drivers/usb/spca500_init.h
spca5xx-20060202/drivers/usb/tv8532.h
spca5xx-20060202/CHANGELOG
tar: spca5xx-20060202/drivers: implausibly old time stamp 1970-01-01 01:00:00
spca5xx-20060202/README-SONIX
spca5xx-20060202/README-TV8532
spca5xx-20060202/INSTALL
spca5xx-20060202/cutlog.py
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/root/spca5xx-20060202 CC=gcc-3.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca50x.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/et61x.ko
install -c -m 0644 spca5xx.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
/sbin/depmod -ae

```
  
```
apt-get -f -y install gqcam
```

gqcam 
```
root@Laptop06:~# gqcam
/dev/video: No such file or directory
root@Laptop06:~#     
```
  
```
root@Laptop06:~# ls /dev/video*
/dev/video0
root@Laptop06:~#  
```

---

### Post by patrick295767 on 2006-02-27
I unplug and replug the webcam ... 
  
and get this:
```
[4294670.962000] ICH4: chipset revision 3
[4294670.962000] ICH4: not 100% native mode: will probe irqs later
[4294670.962000]     ide0: BM-DMA at 0x1840-0x1847, BIOS settings: hda:DMA, hdb:
pio
[4294670.962000]     ide1: BM-DMA at 0x1848-0x184f, BIOS settings: hdc:DMA, hdd:
pio
[4294670.962000] Probing IDE interface ide0...
[4294671.226000] hda: IC25N060ATMR04-0, ATA DISK drive
[4294671.838000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.838000] Probing IDE interface ide1...
[4294672.561000] hdc: TOSHIBA DVD-ROM SD-R6112, ATAPI CD/DVD-ROM drive
[4294673.173000] ide1 at 0x170-0x177,0x376 on irq 15
[4294673.173000] Probing IDE interface ide2...
[4294673.686000] Probing IDE interface ide3...
[4294674.198000] Probing IDE interface ide4...
[4294674.716000] Probing IDE interface ide5...
[4294675.231000] hda: max request size: 1024KiB
[4294675.253000] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/25
5/63, UDMA(100)
[4294675.254000] hda: cache flushes supported
[4294675.254000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 > p3 p4
[4294675.318000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294675.318000] Uniform CD-ROM driver Revision: 3.20
[4294675.525000] Attempting manual resume
[4294675.547000] swsusp: Suspend partition has wrong signature?
[4294675.583000] usbcore: registered new driver usbfs
[4294675.583000] usbcore: registered new driver hub
[4294675.584000] USB Universal Host Controller Interface driver v2.2
[4294675.585000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 3
[4294675.585000] PCI: setting IRQ 3 as level-triggered
[4294675.585000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 3 (le
vel, low) -> IRQ 3
[4294675.585000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294675.585000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801DB/DBL/DBM (ICH4/
ICH4-L/ICH4-M) USB UHCI Controller #1
[4294675.647000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus num
ber 1
[4294675.647000] uhci_hcd 0000:00:1d.0: irq 3, io base 0x00001800
[4294675.647000] hub 1-0:1.0: USB hub found
[4294675.647000] hub 1-0:1.0: 2 ports detected
[4294675.650000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294675.650000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (l
evel, low) -> IRQ 11
[4294675.650000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294675.650000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801DB/DBL/DBM (ICH4/
ICH4-L/ICH4-M) USB UHCI Controller #2
[4294675.712000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus num
ber 2
[4294675.712000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[4294675.712000] hub 2-0:1.0: USB hub found
[4294675.712000] hub 2-0:1.0: 2 ports detected
[4294675.733000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 7
[4294675.733000] PCI: setting IRQ 7 as level-triggered
[4294675.733000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 7 (le
vel, low) -> IRQ 7
[4294675.733000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294675.733000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801DB/DBM (ICH4/ICH4
-M) USB2 EHCI Controller
[4294675.733000] ehci_hcd 0000:00:1d.7: debug port 1
[4294675.733000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus num
ber 3
[4294675.733000] ehci_hcd 0000:00:1d.7: irq 7, io mem 0xc0000000
[4294675.737000] PCI: cache line size of 32 is not supported by device 0000:00:1
d.7
[4294675.737000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 1
0 Dec 2004
[4294675.737000] hub 3-0:1.0: USB hub found
[4294675.737000] hub 3-0:1.0: 4 ports detected
[4294675.817000] e100: Intel(R) PRO/100 Network Driver, 3.4.8-k2-NAPI
[4294675.817000] e100: Copyright(c) 1999-2005 Intel Corporation
[4294675.817000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[4294675.817000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 11 (l
evel, low) -> IRQ 11
[4294675.840000] e100: eth0: e100_probe: addr 0xc2004000, irq 11, MAC addr 00:08
:0D:F3:C5:D3
[4294676.446000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[4294676.701000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[4294677.892000] usbcore: registered new driver hiddev
[4294677.912000] input: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse Op
tical] on usb-0000:00:1d.1-1
[4294677.912000] usbcore: registered new driver usbhid
[4294677.912000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294678.130000] ACPI: Fan [FAN] (off)
[4294678.134000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294678.135000] ACPI: Thermal Zone [THRM] (41 C)
[4294678.351000] Attempting manual resume
[4294678.367000] swsusp: Suspend partition has wrong signature?
[4294678.406000] EXT3-fs: INFO: recovery required on readonly filesystem.
[4294678.406000] EXT3-fs: write access will be enabled during recovery.
[4294680.619000] kjournald starting.  Commit interval 5 seconds
[4294680.620000] EXT3-fs: hda4: orphan cleanup on readonly fs
[4294680.620000] ext3_orphan_cleanup: deleting unreferenced inode 294118
[4294680.620000] ext3_orphan_cleanup: deleting unreferenced inode 293011
[4294680.620000] EXT3-fs: hda4: 2 orphan inodes deleted
[4294680.620000] EXT3-fs: recovery complete.
[4294680.647000] EXT3-fs: mounted filesystem with ordered data mode.
[4294682.111000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294684.493000] Adding 208772k swap on /dev/hda6.  Priority:-1 extents:1
[4294684.631000] EXT3 FS on hda4, internal journal
[4294691.223000] pnp: Device 00:08 activated.
[4294691.223000] parport: PnPBIOS parport detected.
[4294691.223000] parport0: PC-style at 0x378 (0x778), irq 5, dma 3 [PCSPP,TRISTA
TE,COMPAT,ECP,DMA]
[4294691.310000] lp0: using parport0 (interrupt-driven).
[4294691.340000] mice: PS/2 mouse device common for all mice
[4294691.380000] ieee1394: Initialized config rom entry `ip1394'
[4294691.389000] SCSI subsystem initialized
[4294691.394000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294692.144000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xf6eb1, caps: 0x804
713/0x0
[4294692.144000] synaptics: Toshiba Satellite M30 detected, limiting rate to 40p
ps.
[4294692.147000] input: SynPS/2 Synaptics TouchPad on isa0060/serio1
[4294692.380000] ts: Compaq touchscreen protocol output
[4294694.929000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@r
edhat.com
[4294697.310000] Linux agpgart interface v0.101 (c) Dave Jones
[4294697.318000] agpgart: Detected an Intel 855PM Chipset.
[4294697.345000] agpgart: AGP aperture is 256M @ 0xd0000000
[4294697.419000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294697.424000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294697.424000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294697.631000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294697.631000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294697.689000] hw_random: RNG not detected
[4294698.064000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 4 (le
vel, low) -> IRQ 4
[4294698.064000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294699.325000] AC'97 1 does not respond - RESET
[4294699.325000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[4294699.325000] Unable to initialize codec #1
[4294699.375000] intel8x0_measure_ac97_clock: measured 49526 usecs
[4294699.375000] intel8x0: clocking to 48000
[4294699.699000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294699.699000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 3
[4294699.699000] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [LNKF] -> GSI 3 (le
vel, low) -> IRQ 3
[4294699.764000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[3]  MMIO=[c200600
0-c20067ff]  Max Packet=[2048]
[4294699.918000] ieee80211_crypt: registered algorithm 'NULL'
[4294699.922000] ieee80211: 802.11 data/management/control stack, 1.0.3
[4294699.922000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@
linux.intel.com>
[4294699.932000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.1.2
[4294699.932000] ipw2100: Copyright(c) 2003-2005 Intel Corporation
[4294699.935000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [LNKD] -> GSI 11 (l
evel, low) -> IRQ 11
[4294699.936000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[4294700.142000] eth1: Radio is disabled by RF switch.
[4294700.334000] Linux Kernel Card Services
[4294700.334000]   options:  [pci] [cardbus] [pm]
[4294700.338000] PCI: Enabling device 0000:02:0b.0 (0000 -> 0002)
[4294700.338000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKA] -> GSI 3 (le
vel, low) -> IRQ 3
[4294700.338000] Yenta: CardBus bridge found at 0000:02:0b.0 [1179:0001]
[4294700.458000] Yenta: ISA IRQ mask 0x0000, PCI irq 3
[4294700.458000] Socket status: 30000007
[4294701.021000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000039000046f558]
[4294701.778000] Linux video capture interface: v1.00
[4294701.783000] drivers/usb/media/spca5xx/spca5xx-core.c: USB SPCA5XX camera fo
und.Logitech QuickCam Express II(SPCA561A)
[4294701.789000] usbcore: registered new driver spca5xx
[4294701.789000] drivers/usb/media/spca5xx/spca5xx-core.c: spca5xx driver 00.57.
02 registered
[4294702.010000] input: PC Speaker
[4294702.109000] Real Time Clock Driver v1.12
[4294702.819000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[4294702.829000] NET: Registered protocol family 17
[4294714.641000] nfs warning: mount version older than kernel
[4294716.143000] NET: Registered protocol family 10
[4294716.143000] Disabled Privacy Extensions on device c02eb280(lo)
[4294716.143000] IPv6 over IPv4 tunneling driver
[4294716.896000] ACPI: AC Adapter [ADP1] (on-line)
[4294716.938000] ACPI: Battery Slot [BAT1] (battery present)
[4294716.958000] ACPI: Power Button (FF) [PWRF]
[4294716.958000] ACPI: Lid Switch [LID]
[4294716.958000] ACPI: Power Button (CM) [PWRB]
[4294717.063000] ibm_acpi: ec object not found
[4294717.152000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[4294717.152000] toshiba_acpi:     HCI method: \_SB_.VALZ.GHCI
[4294717.168000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[4294717.168000] toshiba_acpi: ktoshkeyd will check 2 times per second
[4294717.169000] toshiba_acpi: Dropped 0 keys from the queue on startup
[4294717.189000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[4294718.463000] cdrom: This disc doesn't have any tracks I recognize!
[4294722.418000] cs: IO port probe 0x100-0x4ff: excluding 0x1e0-0x1e7 0x4d0-0x4d
7
[4294722.419000] cs: IO port probe 0xc00-0xcf7: clean.
[4294722.420000] cs: IO port probe 0xa00-0xaff: clean.
[4294726.906000] eth0: no IPv6 routers present
[4294727.992000] nfs warning: mount version older than kernel
[4295313.716000] usbcore: deregistering driver spca5xx
[4295313.731000] drivers/usb/media/spca5xx/spca5xx-core.c: driver spca5xx deregi
stered
[4295314.011000] Linux video capture interface: v1.00
[4295314.025000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: USB SPCA5XX camer
a found.Logitech QuickCam Express II(SPCA561A)
[4295314.025000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_probe:81
88] Camera type S561
[4295314.030000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_getcapab
ility:2176] maxw 352 maxh 288 minw 160 minh 120
[4295314.046000] usbcore: registered new driver spca5xx
[4295314.046000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: spca5xx driver 00
.57.09 registered
[4295462.637000] usbcore: deregistering driver spca5xx
[4295462.657000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: driver spca5xx de
registered
[4295462.919000] Linux video capture interface: v1.00
[4295462.933000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: USB SPCA5XX camer
a found.Logitech QuickCam Express II(SPCA561A)
[4295462.933000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_probe:81
88] Camera type S561
[4295462.938000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_getcapab
ility:2176] maxw 352 maxh 288 minw 160 minh 120
[4295462.954000] usbcore: registered new driver spca5xx
[4295462.954000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: spca5xx driver 00
.57.09 registered
[4295547.900000] usb 1-1: USB disconnect, address 2
[4295551.066000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[4295551.158000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: USB SPCA5XX camer
a found.Logitech QuickCam Express II(SPCA561A)
[4295551.158000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_probe:81
88] Camera type S561
[4295551.164000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_getcapab     ility:2176] maxw 352 maxh 288 minw 160 minh 120
[4295735.572000] usbcore: deregistering driver spca5xx
[4295735.599000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: driver spca5xx de     registered
[4295735.921000] Linux video capture interface: v1.00
[4295735.939000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: USB SPCA5XX camer     a found.Logitech QuickCam Express II(SPCA561A)
[4295735.939000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_probe:81     88] Camera type S561
[4295735.946000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_getcapab     ility:2176] maxw 352 maxh 288 minw 160 minh 120
[4295735.947000] usbcore: registered new driver spca5xx
[4295735.947000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: spca5xx driver 00     .57.09 registered
[4295873.900000] usb 1-1: USB disconnect, address 3
[4295876.816000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[4295876.909000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: USB SPCA5XX camer     a found.Logitech QuickCam Express II(SPCA561A)
[4295876.909000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_probe:81     88] Camera type S561
[4295876.914000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_getcapab     ility:2176] maxw 352 maxh 288 minw 160 minh 120
root@Laptop06:~#

```
  
....

---

### Post by patrick295767 on 2006-02-27
big progress !!

Camorama gives a window

not frozen linux !!!
:-)

investigating still !!!

---

### Post by patrick295767 on 2006-02-27
Thankkkkkkkkkkkkkkkkkkkkkkkkkkkkk
Thankkkkkkkkkkkkkkkkkkkkkkkkkkkkkthankkkkkkkkkkkkkkkkkkkkkkkkkkkkkthankkkkkkkkkkkkkkkkkkkkkkkkkkkkkthankkkkkkkkkkkkkkkkkkkkkkkkkkkkk
You You !! Arnie !

---

### Post by patrick295767 on 2006-02-27
To make scripts solves everthg !!!
Just like u said, use it wihtout modifying and it'll work !!
  
Thank you very much Arnie, after 3 months of reading posts and posts and posts !!
And any posts had the solution !!




===  
I like  scripts: ...
We should provide more scripts for installing things & hardwares ...
with wget directly from the net ... 

 Very good day !

Like installing video & mozilla ... 
I use this:
nothing to think, and it works all time ... every installation of server linux ... 
```
#!/bin/bash
date
echo "I hope u didnt forget to start enter the name of the main user"
echo " If right, press space otherwise, quit with ctrl Z or ctrl c"
echo "wait functino ?"
echo " Processing ..."
##mkdir "/home/$1/.fvwm"
cp "/etc/apt/sources.list" "/etc/apt/sources.list-backup"
cp "/root/sources.list" /etc/apt/sources.list
##cp "/root/.fvwm2rc" "/home/$1/.fvwm/.fvwm2rc"
apt-get -f -y install mc
apt-get update
apt-get -y upgrade
apt-get -f -y install mc proftpd
apt-get -f -y install nfs
apt-get -f -y install 
apt-get -f -y install ssh
apt-get -f -y install ftp
apt-get -f -y install openssh-server
apt-get -f -y install x-window-system-core
apt-get -f -y install xserver-xorg
apt-get -f -y install 
apt-get -f -y install 
apt-get -f -y install fvwm 
apt-get -f -y install rxvt
apt-get -f -y install wterm aterm
apt-get -f -y install eterm
apt-get -f -y install xlock 
apt-get -f -y install xlockmore
apt-get -f -y install rox-filer
apt-get -f -y install leafpad
apt-get -f -y install xterm
apt-get -f -y install
apt-get -f -y install

apt-get -f -y install nfs-common
apt-get -f -y install nfs-kernel-server
apt-get -f -y install portmap
apt-get -f -y install nfs
apt-get -f -y install 
apt-get -f -y install autofs
apt-get -f -y install idesk
apt-get -f -y install xloadimage
apt-get -f -y install samba
apt-get -f -y install unzip
apt-get -f -y install bzip2
apt-get -f -y install gzip
apt-get -f -y install openssh-server

apt-get -f -y install growisofs
apt-get -f -y install 
apt-get -f -y install 
apt-get -f -y install smbclient xloadimage

apt-get -f -y install dhcp3-server
apt-get -f -y install 
echo " You can go now for a cup of coffee !"
echo " Enjoy & see you later !"
apt-get -f -y install numlockx
apt-get -f -y install xterm
apt-get -f -y install mc
apt-get -f -y install nedit
apt-get -f -y install gedit
apt-get -f -y install gnome-chess
apt-get -f -y install menu
apt-get -f -y install debian-menu
apt-get -f -y install abiword gnome-gv
apt-get -f -y install xmms xlock
apt-get -f -y install fvwm
apt-get -f -y install xpdf xzgv 
apt-get -f -y install xpdf-reader
apt-get -f -y install rar
apt-get -f -y install tar
apt-get -f -y install zip
apt-get -f -y install scrot
apt-get -f -y install gdesklets
apt-get -f -y install idesk
apt-get -f -y install krusader
apt-get -f -y install bootcd
apt-get -f -y install aterm rxvt 
apt-get -f -y install mrxvt
apt-get -f -y install eterm
apt-get -f -y install 


apt-get -f -y install mozilla-firefox dillo
apt-get -f -y install sylpheed lynx gedit
apt-get -f -y install gnumeric
apt-get -f -y install digikam
apt-get -f -y install audacity kaudiocreator
apt-get -f -y install gparted
apt-get -f -y install qtparted
apt-get -f -y install k3b mplayer-386
apt-get -f -y install k3bsetup
apt-get -f -y install kate
apt-get -f -y install
apt-get -f -y install cdrdao
apt-get -f -y install kadu gftp xpdf
apt-get -f -y install sylpheed
apt-get -f -y install imagemagick
apt-get -f -y install idesk 
apt-get -f -y install gimp
apt-get -f -y install kadu
apt-get -f -y install gnome-panel
apt-get -f -y install xloadimage
apt-get -f -y install dvd+rw-tools
apt-get -f -y install growisofs mozilla
apt-get -f -y install mozilla-firefox
apt-get -f -y install sun-j2re1.5 flashplayer-mozilla

## this 3  lines for amsn 0.95 & also for vmware workstation
apt-get -f -y install tcl8.4 
apt-get -f -y install tk8.4
apt-get -f -y install tk8.4-dev
apt-get -f -y install zenity

apt-get -f -y install gcc 
apt-get -f -y install gcc-3.4
apt-get -f -y install build-essential tcl8.4-dev tk8.4-dev imlib11-dev esound-clients
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
apt-get -f -y install linux-headers-$(uname -r)
apt-get -f -y install build-essential 
#apt-get -f -y install amsn 


apt-get -f -y install
apt-get -f -y install


apt-get -f -y install 
apt-get -f -y install 
apt-get -f -y install dvd+rw-format
apt-get -f -y install 
apt-get -f -y install imagemagick mozilla-browser
apt-get -f -y install gaim
apt-get -f -y install 

apt-get -f -y install opera
apt-get -f -y install nfs
apt-get -f -y install mozplugger
apt-get -f -y install kopete

apt-get -f -y install xlockmore
apt-get -f -y install kfmclient
apt-get -f -y install xfce
apt-get -f -y install samba
apt-get -f -y install kaffeine
apt-get -f -y install kadu
apt-get -f -y install xine
apt-get -f -y install

apt-get -f -y install gnome-volume-manager
apt-get -f -y install amule alien
apt-get -f -y install rcconf
apt-get -f -y install vpnc
apt-get -f -y install kcron
apt-get -f -y install cron 
apt-get -f -y install libqt3c102-mt
apt-get -f -y install crond gpdf kpdf gs kghostview
apt-get -f -y install xzgv mplayerplug-in

apt-get -f -y install xmltv
apt-get -f -y install audacity gcc
apt-get -f -y install digikam kmail kaddressbook mtools annoyance-filter khelpcenter kleopatra
apt-get -f -y install nfs nfs-common
apt-get -f -y install libpt-plugins-v4l kmail
apt-get -f -y install kontact kmail
apt-get -f -y install kicker
apt-get -f -y install konsole gxine
apt-get -f -y install kmines 
apt-get -f -y install galeon
apt-get -f -y install minimo
apt-get -f -y install camorama kbear gftp
apt-get -f -y install klondike kdict
apt-get -f -y install kmahjongg
apt-get -f -y install kate grip
apt-get -f -y install synaptic alsamixergui
apt-get -f -y install synaptics
apt-get -f -y install wine gimp hatari 
apt-get -f -y install audacity
apt-get -f -y install ardour rezound ksim

apt-get -f -y install gweather
apt-get -f -y install gdesklets
apt-get -f -y install 

# hb
apt-get -f -y install libwxgtk2.4-dev
apt-get -f -y install tcltls planner kweather knewsticker korn wine





apt-get -f -y install xawtv
apt-get -f -y install gqcam qcam qc-usb-source qc-usb-utils
apt-get -f -y install 


echo "*** LINUX$(uname -r) startup file to be modified !"

cd ~
apt-get -f -y install rox-filer dgen xscreensaver xlockmore gnome-screensaver
apt-get -f -y install sun-j2re1.5
apt-get -f -y --force-yes sun-j2re1.5
apt-get -f -y install azureus
apt-get -f -y install
apt-get -f -y install sun-j2sdk1.5
apt-get -f -y install
apt-get -f -y install
apt-get -f -y install azureus
apt-get -f -y install

echo "***"
echo "*** please go and get opera, skype and gaim, install them rox-filer***"
echo "** crossover is nice prg for windows apps**"
echo "fvwm" > "/home/$1/.Xsession"
echo "/home/$1/.Xsession"
echo "set up the fvwm as default"
apt-get -f -y install 



cd /usr/lib/mozilla-firefox/plugins
mv libtotem_mozilla.a libtotem_mozilla.la libtotem_mozilla.so libtotem_mozilla.xpt /home

apt-get -f -y install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg w32codecs
apt-get -f -y install lame sox ffmpeg mjpegtools vorbis-tools libdvdcss2 
apt-get -f -y install gstreamer0.8-plugins-multiverse avifile-divx-plugin avifile-mad-plugin 
apt-get -f -y install avifile-mjpeg-plugin avifile-vorbis-plugin avifile-win32-plugin 
apt-get -f -y install avifile-xvid-plugin libdvdnav4 libdvdplay0 libdvdread3
apt-get -f -y install gst-register-0.8

apt-get -f -y install mplayer-386
apt-get -f -y install mozilla-mplayer
apt-get -f -y install mplayer-fonts flashplayer-mozilla
sudo apt-get -f -y install gstreamer0.8-plugins
sudo apt-get -f -y install gstreamer0.8-lame
sudo apt-get -f -y install gstreamer0.8-ffmpeg
sudo apt-get -f -y install w32codecs
sudo apt-get -f -y install libdivx4linux
sudo apt-get -f -y install lame
sudo apt-get -f -y install sox
sudo apt-get -f -y install ffmpeg
sudo apt-get -f -y install mjpegtools
sudo apt-get -f -y install vorbis-tools
apt-get -f -y install acroread 
apt-get -f -y install flashplayer-mozilla
apt-get -f -y install mozilla-acroread
apt-get -f -y install mplayerplug-in
apt-get -f -y install totem-xine
apt-get -f -y install mozplugger
apt-get -f -y install libflash-mozplugin
apt-get -f -y install libstdc++5
apt-get -f -y install w32codecs 
apt-get -f -y install libdvdcss2 
apt-get -f -y install gstreamer-mad xmms vlc wxvlc gvlc vlc-esd
apt-get -f -y install beep-media-player mozilla-mplayer

##apt-get -f -y install totem-xine-firefox-plugin


wget http://www2.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2
mkdir /usr/lib/win32
tar -xjf essential-20050412.tar.bz2
mv essential-20050412/* /usr/lib/win32
  
##never forget this for all the users
echo "zoom=yes" >> ~/.mplayer/config



apt-get -f -y install xorg-driver-fglrx
## gatos also possible

######################## INSTALLATION OF PACKAGE FOLDER ##################"


# now installing realplayer from the file placed in /root/RealPlayer10GOLD.bin
chmod 777 /root/RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin       #You could install it in /opt/Realplayer
##And if you have mplayer associated to the rpm-files (check with: about: plugins), do also:
cd /usr/lib/mozilla-firefox/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla-firefox/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup

cd /usr/lib/mozilla/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup

## now the cedega
mkdir /root/patrickpackages
cd /root/patrickpackages

gzip -d cedega_4.4.3-1.i386.tgz
# un-tgz
tar -xvf cedega_4.4.3-1.i386.tar
## once done
##/usr created 
##you'll have to place it in /usr

tar -jxvf cdemu-0.7.tar.bz2.tar


############ antivirus
apt-get -f -y install build-essential
apt-get -f -y  install libwww-perl
apt-get -f -y  install libgtk2.0-dev
apt-get -f -y  install checkinstall

cd /root
dpkg -i xfprot*.deb

cd /root
tar zxvf xfprot-1.15.tar.gz
tar zxvf xfprot-1.15.tar.gz.tar

cd xfprot-1.15
./configure --with-gtk2 --with-sudo --autodetect --without-debug --with-install-dir=/usr/local
make
checkinstall
dpkg -i xfprot*.deb

smeg

###################### Installing xvidcap ############""

echo "  " >> /etc/apt/sources.list
echo "## libavcodec1 " >> /etc/apt/sources.list
echo "deb ftp://ftp.nerim.net/debian-marillat/ sarge main" >> /etc/apt/sources.list
apt-get update
##apt-get upgrade   # I consider you upgraded ur linux
apt-get -f -y install imagemagick
apt-get -f -y install libpng2
cd /root
dpkg -i xvidcap_1.1.3-1_i386.deb
echo "#!/bin/bash" > "/root/xvid.sh"
chmod +x /root/xvid.sh
chmod 777 /root/xvid.sh
echo "xvidcap --gui no --compress 9 --file ~/myvideo.mpeg --frames 0 --fps 10 --cap_geometry 1024x768+0+0" >> "/root/xvid.sh"
echo "if you wanna make a avi file of ur screen, run sh /root/xvid.sh" 
echo "u can move this little script, where you want & need"
echo "** Greetz' **"


########################### end of patrick packages
apt-get -y remove numlockx
apt-get -f -y install openoffice.org
apt-get -f -y install inkscape
apt-get -f -y install openoffice.org-bin
apt-get -f -y install
apt-get -f -y install

############# End of Installing (long packages)
############# fr - nothg -nothg
echo "Please choose gdm "
apt-get -f -y install 
apt-get -y install gdm
apt-get -y install x-window-system-core
apt-get -f -y install xserver-xorg

apt-get -f -y install 
dpkg-reconfigure xserver-xorg
apt-get -f -y install 
apt-get clean
/etc/init.d/gdm restart


apt-cache pkgnames gnome 
date


echo "*** dont forget to enable the XDMCP as true ":
echo "please do: gedit /etc/X11/gdm/gdm.conf &"
echo "gdmsetup should be done too !"
echo "Installation Done !!"




```

---

### Post by patrick295767 on 2006-02-27
Another problem now...'cos trying now on  my tower PC ...
  
I have an ATI all in wonder Tuner Tv video card ... 
(not yet installed)
  
I plugged the usb webcam ... runned ur script 
and try camorama and it says no device ... 
  
i can post my dmesg :
```
294671.940000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:DMA
[4294671.940000] Probing IDE interface ide0...
[4294672.324000] hda: SAMSUNG SP1604N, ATA DISK drive
[4294672.579000] hdb: MAXTOR 4K080H4, ATA DISK drive
[4294672.630000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.630000] Probing IDE interface ide1...
[4294673.677000] hdd: LITE-ON DVDRW SHW-1635S, ATAPI CD/DVD-ROM drive
[4294673.728000] ide1 at 0x170-0x177,0x376 on irq 15
[4294673.728000] Probing IDE interface ide2...
[4294674.241000] Probing IDE interface ide3...
[4294674.753000] Probing IDE interface ide4...
[4294675.265000] Probing IDE interface ide5...
[4294675.782000] hda: max request size: 1024KiB
[4294675.787000] hda: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/255/63, UDMA(33)
[4294675.787000] hda: cache flushes supported
[4294675.787000]  /dev/ide/host0/bus0/target0/lun0: p1 < p5 p6 > p2
[4294675.802000] hdb: max request size: 128KiB
[4294675.803000] hdb: 156301488 sectors (80026 MB) w/2000KiB Cache, CHS=65535/16/63, UDMA(33)
[4294675.803000] hdb: cache flushes supported
[4294675.803000]  /dev/ide/host0/bus0/target1/lun0: p1 p2 < p5 p6 p7 p8 p9 p10 p11 p12 p13 p14 p15 >
[4294675.954000] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294675.954000] Uniform CD-ROM driver Revision: 3.20
[4294676.357000] Attempting manual resume
[4294676.357000] swsusp: Suspend partition has wrong signature?
[4294676.393000] ne2k-pci.c:v1.03 9/22/2003 D. Becker/P. Gortmaker
[4294676.393000]   http://www.scyld.com/network/ne2k-pci.html
[4294676.393000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294676.394000] eth0: RealTek RTL-8029 found at 0xe800, IRQ 16, 00:00:B4:98:CE:F7.
[4294676.429000] usbcore: registered new driver usbfs
[4294676.429000] usbcore: registered new driver hub
[4294676.431000] USB Universal Host Controller Interface driver v2.2
[4294676.431000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294676.431000] PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 5
[4294676.431000] uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
[4294676.493000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[4294676.493000] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d800
[4294676.493000] hub 1-0:1.0: USB hub found
[4294676.493000] hub 1-0:1.0: 2 ports detected
[4294676.496000] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 21
[4294676.496000] PCI: Via IRQ fixup for 0000:00:10.1, from 10 to 5
[4294676.496000] uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
[4294676.558000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[4294676.558000] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000dc00
[4294676.558000] hub 2-0:1.0: USB hub found
[4294676.558000] hub 2-0:1.0: 2 ports detected
[4294676.561000] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 21
[4294676.561000] PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 5
[4294676.561000] uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
[4294676.623000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[4294676.623000] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000e000
[4294676.623000] hub 3-0:1.0: USB hub found
[4294676.623000] hub 3-0:1.0: 2 ports detected
[4294676.660000] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 21
[4294676.660000] ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
[4294676.660000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[4294676.660000] ehci_hcd 0000:00:10.3: irq 21, io mem 0xdfffff00
[4294676.660000] ehci_hcd 0000:00:10.3: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294676.661000] hub 4-0:1.0: USB hub found
[4294676.661000] hub 4-0:1.0: 6 ports detected
[4294676.671000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[4294677.419000] usb 4-1: new high speed USB device using ehci_hcd and address 2
[4294677.493000] hub 4-1:1.0: USB hub found
[4294677.493000] hub 4-1:1.0: 4 ports detected
[4294677.876000] usb 4-1.2: new low speed USB device using ehci_hcd and address 4
[4294678.045000] usb 4-1.4: new low speed USB device using ehci_hcd and address 5
[4294678.265000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[4294678.785000] usbcore: registered new driver hiddev
[4294678.789000] input: USB HID v1.10 Mouse [Acrox USB & PS/2 Mouse] on usb-0000:00:10.3-1.2
[4294678.797000] input: USB HID v1.10 Joystick [Logitech Logitech Dual Action] on usb-0000:00:10.3-1.4
[4294678.797000] usbcore: registered new driver usbhid
[4294678.797000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294679.253000] ACPI: CPU0 (power states: C1[C1])
[4294679.253000] ACPI: Processor [CPU1] (supports 16 throttling states)
[4294679.586000] Attempting manual resume
[4294679.587000] swsusp: Suspend partition has wrong signature?
[4294679.605000] kjournald starting.  Commit interval 5 seconds
[4294679.605000] EXT3-fs: mounted filesystem with ordered data mode.
[4295431.297000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4295435.681000] Adding 746948k swap on /dev/hda6.  Priority:-1 extents:1
[4295435.785000] EXT3 FS on hda2, internal journal
[4295441.924000] parport: PnPBIOS parport detected.
[4295441.924000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[4295442.016000] lp0: using parport0 (interrupt-driven).
[4295442.072000] mice: PS/2 mouse device common for all mice
[4295445.879000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4295446.844000] cdrom: open failed.
[4295525.285000] Linux agpgart interface v0.101 (c) Dave Jones
[4295525.330000] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[4295525.348000] agpgart: AGP aperture is 128M @ 0xe0000000
[4295525.551000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4295525.575000] shpchp: shpc_init : shpc_cap_offset == 0
[4295525.575000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4295526.013000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 17 (level, low) -> IRQ 17
[4295527.104000] gameport: EMU10K1 is pci0000:00:06.1/gameport0, io 0xec00, speed 1169kHz
[4295527.610000] irda_init()
[4295527.610000] NET: Registered protocol family 23
[4295529.551000] Linux video capture interface: v1.00
[4295529.588000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: USB SPCA5XX camera found.Logitech QuickCam Express II(SPCA561A)
[4295529.588000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_probe:8188] Camera type S561
[4295529.593000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_getcapability:2176] maxw 352 maxh 288 minw 160 minh 120
[4295529.620000] usbcore: registered new driver spca5xx
[4295529.620000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: spca5xx driver 00.57.09 registered
[4295530.043000] Floppy drive(s): fd0 is 1.44M
[4295530.058000] FDC 0 is a post-1991 82077
[4295530.489000] Real Time Clock Driver v1.12
[4295530.596000] input: PC Speaker
[4295531.067000] ts: Compaq touchscreen protocol output
[4295533.040000] NET: Registered protocol family 17
[4295542.126000] NET: Registered protocol family 10
[4295542.126000] Disabled Privacy Extensions on device c02eb280(lo)
[4295542.126000] IPv6 over IPv4 tunneling driver
[4295543.363000] ACPI: Power Button (FF) [PWRF]
[4295543.363000] ACPI: Power Button (CM) [PWRB]
[4295543.363000] ACPI: Sleep Button (CM) [SLPB]
[4295543.531000] ibm_acpi: ec object not found
[4295549.728000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[4295553.082000] eth0: no IPv6 routers present
[4295554.689000] kjournald starting.  Commit interval 5 seconds
[4295554.690000] EXT3-fs warning: mounting unchecked fs, running e2fsck is recommended
[4295554.691000] EXT3 FS on hda5, internal journal
[4295554.691000] EXT3-fs: mounted filesystem with ordered data mode.
[4295567.271000] nfs warning: mount version older than kernel
[4295567.330000] nfs warning: mount version older than kernel
[4295567.378000] nfs warning: mount version older than kernel
[4295753.708000] usbcore: deregistering driver spca5xx
[4295753.743000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: driver spca5xx deregistered
[4295760.585000] Linux video capture interface: v1.00
[4295760.609000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: USB SPCA5XX camera found.Logitech QuickCam Express II(SPCA561A)
[4295760.609000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_probe:8188] Camera type S561
[4295760.619000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_getcapability:2176] maxw 352 maxh 288 minw 160 minh 120
[4295760.622000] usbcore: registered new driver spca5xx
[4295760.622000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: spca5xx driver 00.57.09 registered
[4295825.246000] usb 1-2: USB disconnect, address 3
[4295831.912000] usb 1-2: new full speed USB device using uhci_hcd and address 4
[4295832.007000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: USB SPCA5XX camera found.Logitech QuickCam Express II(SPCA561A)
[4295832.007000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_probe:8188] Camera type S561
[4295832.013000] /root/spca5xx-20060202/drivers/usb/spca5xx.c: [spca5xx_getcapability:2176] maxw 352 maxh 288 minw 160 minh 120
root@tower05:/# ls /dev/video*
/dev/video0
root@tower05:/#       
```
  
You would know the problem ??

Thank you very much, 

Patrick

---

### Post by l @ l o on 2006-09-26
> **patrick295767 said:**
> Download this:
[http://prdownloads.sourceforge.net/amsn/amsn_0.95-3.ubuntu.deb](http://prdownloads.sourceforge.net/amsn/amsn_0.95-3.ubuntu.deb)
  
And :
```
sudo apt-get -f -y install amsn
```
```
sudo dpkg -i amsn_0.95-3.ubuntu.deb
```
  
That should make it normally.
(You'd need Ubuntu 5.10 Breezy )
Greetz

Patrick

hi, i've tried to install amsn but it didnt works,

i used your commands, than i got this error

Application initialization failed: couldn't connect to display ":0.0"

than, i did this

export DISPLAY:myip:0.0

than i tried again, and i got an different error

Application initialization failed: couldn't connect to display "myip:0.0"

help?

seems, i have some problem with the display

thanks in advance!](*,)

---

### Post by l @ l o on 2006-09-26
done, it's ok

i find what i needed

xhost +LOCAL:

indeed now works :mrgreen:

---

