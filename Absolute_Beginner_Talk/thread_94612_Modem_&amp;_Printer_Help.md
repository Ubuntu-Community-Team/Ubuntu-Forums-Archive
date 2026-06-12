---
title: "Modem &amp; Printer Help"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by arunmvishnu on 2005-11-24
Hi,
  I installed Linuxant modem driver for my D-Link internal modem. But iam getiing only 14.4kbps speed because iam using free version.I cannot spend 19$ for its licence. Yesterday i installed XMMS,Xine and Alien. Ops did u know it tk 1.4hrs  to download those 3packages(arnd 8MB):mad: :oops: :sad: . Only Synaptic Package manager  is used,no browsers or any other net tools. Now iam downloding w32codecs using $XP:rolleyes: .So can you suggest any other driver for my modem. Here is my modem details.
        Modem: D Link Internal Data/Voice/Fax modem.
        Config for modem unit 0: /dev/ttySHSF0
        Device instance: 0-PCI-127a:1025-127a:1025
        HW revision    : Basic2 2.15 Standard DAA
        HW profile name: hsfpcibasic2
        Registration ID: 3F1F-4011-1E2E
        License owner  : [email]arunmvishnu@gmail.com[/email]
        License key    : FREE
        License status : FREE (max 14.4kbps data only)
        Current region : INDIA (T.35 code: 0053)

My second problem is my printer(Canon pixma ip1000). I converted Fedora driver using alien and installed it. Now the printer is listed in the Printers list. But when i tried to print, the test page is send to the printer queue and after some time it is moved from the q. But the printer is not working. When i tried to print from G-edit the same probelm is occured. The full details is shown bellow. I also converted Realoneplayer10 rpm to deb and installed in my system but not working. No shortcuts are created in the desktop or Applications menu. When i tried realplay command from terminal i gt unknown command message. My xmms player is working. Sp iam not downloading deb package of Realone player, but downloading w32codecs for playing movies(.dat format) in xine.

arun@ubuntu:~$ sudo alien /home/arun/softwares/CanaonDriver/bjfilter-common-2.50 -2.i386.rpm
bjfilter-common_2.50-3_i386.deb generated
arun@ubuntu:~$ sudo alien /home/arun/softwares/CanaonDriver/bjfilter-pixmaip1000 -2.50-2.i386.rpm
bjfilter-pixmaip1000_2.50-3_i386.deb generated
arun@ubuntu:~$ sudo dpkg -i bjfilter-common_2.50-3_i386.deb
Selecting previously deselected package bjfilter-common.
(Reading database ... 59848 files and directories currently installed.)
Unpacking bjfilter-common (from bjfilter-common_2.50-3_i386.deb) ...
Setting up bjfilter-common (2.50-3) ...
arun@ubuntu:~$ sudo dpkg -i bjfilter-pixmaip1000_2.50-3_i386.deb
Selecting previously deselected package bjfilter-pixmaip1000.
(Reading database ... 59856 files and directories currently installed.)
Unpacking bjfilter-pixmaip1000 (from bjfilter-pixmaip1000_2.50-3_i386.deb) ...
Setting up bjfilter-pixmaip1000 (2.50-3) ...
arun@ubuntu:~$ gedit

(gedit:13624): Gdk-WARNING **: locale not supported by Xlib

(gedit:13624): Gdk-WARNING **: cannot set locale modifiers

(gedit:13624): GnomePrintCupsPlugin-WARNING **: iconv does not support ppd chara cter encoding: ISOLatin1, trying CSISOLatin1

(gedit:13624): GnomePrint-WARNING **: Problem while creating filter from 'frgba' : filter 'frgba' is unknown

(gedit:13624): GnomePrint-WARNING **: Problem while creating filter from 'frgba' : filter 'frgba' is unknown

(gedit:13624): GnomePrint-WARNING **: Problem while creating filter from 'frgba' : filter 'frgba' is unknown

(gedit:13624): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:13624): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:13624): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:13624): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:13624): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
arun@ubuntu:~$

---

### Post by towsonu2003 on 2005-11-24
[QUOTE=arunmvishnu]Hi,
  I installed Linuxant modem driver for my D-Link internal modem. But iam getiing only 14.4kbps speed because iam using free version.
[/QUOTE]

you may wanna go to linmodems.org , READ then download scanModem tool, READ the readme file inside, run that, READ the outputs it gives, then follow the instructions. If you don't understand the instructions, read the part where it says how you can email the people who maintain it. they are EXTREMELY helpful, as long as they see you read stuff but could not solve the problem (that's why I capitalized "READ" everywhere)... 

you may wanna allocate 2 days or so for that stuff... god luck (don't worry, it's usually easier than how it looks)

I wish ubuntu supported winmodems out of the box... people outside USA actually USE them to connect :p

They REALLY helped me with my sl modem... 

sorry, but dont know much about printers...

---

