---
title: "how to install QT dev packages?"
date: 2005-08-03
forum: Absolute Beginner Talk
---

### Post by x1c0 on 2005-08-03
Hi, i'm trying to compile the kernel, but when i do this:

root@x1c0ubuntu:/usr/src/linux # make xconfig
* Unable to find the QT installation. Please make sure that the
* QT development package is correctly installed and the QTDIR
* environment variable is set to the correct location.
*

make[1]: *** [scripts/kconfig/.tmp_qtcheck] Error 1
make: *** [xconfig] Error 2

?? so what i can do now? i'm using Ubuntu, and i'm trying to fix my ethernet connection...

i also do this:

root@x1c0ubuntu:/usr/src/linux # apt-cache search qt
gstreamer0.8-misc - Collection of various GStreamer plugins
libqthreads-12 - QuickThreads library for Guile
libx11-6 - X Window System protocol client library

it means that i dont have the QT installation right?

please help..

x1c0. :(

---

### Post by Knome_fan on 2005-08-03
1. make menuconfig should give you a nice ncurses interface if all else fails.
2.apt-get install libqt3-mt-dev should give you the qt dev files.

---

### Post by x1c0 on 2005-08-03
:(:(:(:(:(:(

i tried, but:
couldn't find package libqt3-mt-dev

that's because i dont have a connection to the net i only have the ububtu CD

what should i do? i think i never going to make it...

---

### Post by Knome_fan on 2005-08-04
Hm, why don't you try make menuconfig?
You could also try make gconfig, which uses gtk I think.

But what problem are you trying to solve anyway?

---

### Post by x1c0 on 2005-08-04
My problem is: my ubuntu doesn't recongise my network interface card, and i have a toshiba tecra S2 laptop, from search in google i find this page: [http://www.linuxval.org/ubuntu/phpBB2/viewtopic.php?p=1776#1776](http://www.linuxval.org/ubuntu/phpBB2/viewtopic.php?p=1776#1776)

and i'm trying to do the same, but in the driver installation part, i'have to compile the kernel.. and my problem start there... :(  :?

if i try menuconfig, gives another error because the ncurses libryries.. and i dont't have connection to the internet so i can't make the better solution : apt-get install XXX , i only have de ubuntu CDROM.

what can i do??

x1c0.

---

### Post by Knome_fan on 2005-08-04
1. I'm pretty sure ncurses is on the CD, so you should at least be able to install it.
2. I'm not so sure about the linux sources being on the CD, so I don't really know if you'll be able to recompile the kernel anyway.
3. I don't really think you need to recompile it. If there's something you are missing that is installable via apt, as you seem to say, than you could simply download the .deb you need somehow, put it on your Ubuntu machine and then install it with sudo dpkg -i your.deb
4. Also, could you post what network card you have specifically? I think it would make helping you a lot easier. (As mentioned in the thread you linked to, lspci should give you some information)

---

### Post by x1c0 on 2005-08-04
1. all that i can find in the CD about ncurses i already have installed, and i dont know how, keep giving error

2. about the sources, i have made a download of the same version 2.6.10

3. in other PC i have made: apt-get -d install qt3-apps-dev , then this have downloaded to /var/cache/apt/archives folder.. but this command have downloaded 32 itens .deb

so what i do now? i copy those files to my  /var/cache/apt/archives folder and do what? i do: dpkg -i "what_file?".deb?

4.  lspci:

0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Port (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0148 (rev a2)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4362 (rev 15)
0000:06:02.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:06:04.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:06:04.1 CardBus bridge: Texas Instruments: Unknown device 8031
0000:06:04.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:06:04.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:06:04.4 0805: Texas Instruments: Unknown device 8034 

5. thanks for helping me. ;-)

---

### Post by Knome_fan on 2005-08-04
1.  ;-) About the errors you are getting when you try to recompile your kernel. Could you post the exact errors here? I really haven't tried running make menuconfig only with the stuff coming on the install CD, but I at least was pretty sure that it would work.
Btw., that just occurd to me, did you install build-essentials? You'll need them to compile anything and they are on the CD, so maybe that's the problem.

2. Downloading the sources form kernel.org isn't probably the best idea, as the Ubuntu sources are patched.

3. After some googleing I think there is a chance that your ethernet card works without recompiling.
Try the following:
sudo modprobe sk98lin
this should load the module, that is the driver you need.

However, google also revealed that apparently it doesn't work for all cards, but there is a newer driver here:
[http://www.syskonnect.com/syskonnect/support/driver/zip/linux/](http://www.syskonnect.com/syskonnect/support/driver/zip/linux/)

4. Finally, the following site may be of help:
[http://www.de-brauwer.be/wiki/wikka.php?wakka=LinuxTecraS2](http://www.de-brauwer.be/wiki/wikka.php?wakka=LinuxTecraS2)

---

### Post by x1c0 on 2005-08-09
sorry for replying so late...

1. here are the erros when try to compile the kernel:

x1c0@x1c0ubuntu:/usr/src/linux$ make menuconfig
/usr/bin/ld: cannot find -lncurses
collect2: ld returned 1 exit status

>> Unable to find the Ncurses libraries.
>>
>> You must install ncurses-devel in order
>> to use 'make menuconfig'

make[2]: *** [scripts/lxdialog/ncurses] Error 1
make[1]: *** [menuconfig] Error 2
make: *** [menuconfig] Error 2
------------------------------------------------
x1c0@x1c0ubuntu:/usr/src/linux$ make xconfig
*
* Unable to find the QT installation. Please make sure that the
* QT development package is correctly installed and the QTDIR
* environment variable is set to the correct location.
*
make[1]: *** [scripts/kconfig/.tmp_qtcheck] Error 1
make: *** [xconfig] Error 2
----------------------------------------------------------------
x1c0@x1c0ubuntu:/usr/src/linux$ make gconfig
*
* Unable to find the GTK+ installation. Please make sure that
* the GTK+ 2.0 development package is correctly installed...
* You need gtk+-2.0, glib-2.0 and libglade-2.0.
*
make[1]: *** [scripts/kconfig/.tmp_gtkcheck] Error 1
make: *** [gconfig] Error 2

and btw, what is the "build-essentials"? i only have istalled gcc  :?

2. what u mean by: "Ubuntu sources are patched" ?

3. i have try that command but... doesn't work :(
    and i already have that driver  ;-) 

4. that is the link that i have started to do something :grin:

---

### Post by Simon03 on 2005-11-09
Hey, I've got the same errors !!! 

Can someone help me ? I'm a linux's beginner and i'm trying to install the driver of my aDSL connection but to do this I need to compile the kernel ... so I need the comand "gconfig or menuconfig" ... I got the same errors as X1co !!! I really don't know how to install GTK+ and Ncurses libraries ....

I guess you can help me ...
thanx:)

---

