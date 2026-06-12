---
title: "sound in ubuntu..."
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by kokophone on 2007-11-16
hello all of my friend
I unable to open my sound in my ubuntu!!
I don't know why>>
I use so many website
but it can't be
please help me

---

### Post by DutyDuty on 2007-11-17
If, and only if, you are using a Toshiba, use the link in my Signature to get your sound working.

---

### Post by saj0577 on 2007-11-17
What computer are you using?

Are you trying to use on board sound or external speakers?


Saj

---

### Post by kokophone on 2007-11-17
I used compaq laptop...
hda-intel...
But I can't find no sound...
pls.....

---

### Post by DutyDuty on 2007-11-17
```
lspci
``` output please

---

### Post by kokophone on 2007-11-17
kokophone@kokophone-laptop:~$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree... Done
apache2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kokophone@kokophone-laptop:~$ sudo apt-get install php4
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libapache2-mod-php4 libzzip-0-12 php4-common
Suggested packages:
  php-pear
The following packages will be REMOVED
  libapache2-mod-php5 php5-mysql php5-mysqli
The following NEW packages will be installed
  libapache2-mod-php4 libzzip-0-12 php4 php4-common
0 upgraded, 4 newly installed, 3 to remove and 0 not upgraded.
Need to get 1766kB of archives.
After unpacking 1794kB disk space will be freed.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe libzzip-0-12 0.12.83-5 [33.9kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe php4-common 4:4.4.2-1build1 [174kB]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe libapache2-mod-php4 4:4.4.2-1build1 [1557kB]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe php4 4:4.4.2-1build1 [1162B]Fetched 1766kB in 7s (241kB/s)
(Reading database ... 85916 files and directories currently installed.)
Removing php5-mysql ...
Removing php5-mysqli ...
Removing libapache2-mod-php5 ...
Module php5 disabled; run /etc/init.d/apache2 force-reload to fully disable.
Selecting previously deselected package libzzip-0-12.
(Reading database ... 85910 files and directories currently installed.)
Unpacking libzzip-0-12 (from .../libzzip-0-12_0.12.83-5_i386.deb) ...
Selecting previously deselected package php4-common.
Unpacking php4-common (from .../php4-common_4%3a4.4.2-1build1_i386.deb) ...
Selecting previously deselected package libapache2-mod-php4.
Unpacking libapache2-mod-php4 (from .../libapache2-mod-php4_4%3a4.4.2-1build1_i386.deb) ...
Selecting previously deselected package php4.
Unpacking php4 (from .../php4_4%3a4.4.2-1build1_all.deb) ...
Setting up libzzip-0-12 (0.12.83-5) ...

Setting up php4-common (4.4.2-1build1) ...
Setting up libapache2-mod-php4 (4.4.2-1build1) ...
 * Forcing reload of apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                         [ ok ]

Setting up php4 (4.4.2-1build1) ...

kokophone@kokophone-laptop:~$ sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                         [ ok ]
kokophone@kokophone-laptop:~$ sudo gedit /var/www/testphp.php
kokophone@kokophone-laptop:~$ sudp apt-get install php5
bash: sudp: command not found
kokophone@kokophone-laptop:~$ sudo apt-get install php5
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libapache2-mod-php5
Suggested packages:
  php-pear
The following packages will be REMOVED
  libapache2-mod-php4 php4
The following NEW packages will be installed
  libapache2-mod-php5 php5
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 1044B/2262kB of archives.
After unpacking 2048kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main php5 5.1.2-1ubuntu3.9 [1044B]
Fetched 1044B in 20s (52B/s)
(Reading database ... 85953 files and directories currently installed.)
Removing php4 ...
Removing libapache2-mod-php4 ...
Module php4 disabled; run /etc/init.d/apache2 force-reload to fully disable.
Selecting previously deselected package libapache2-mod-php5.
(Reading database ... 85950 files and directories currently installed.)
Unpacking libapache2-mod-php5 (from .../libapache2-mod-php5_5.1.2-1ubuntu3.9_i386.deb) ...
Selecting previously deselected package php5.
Unpacking php5 (from .../php5_5.1.2-1ubuntu3.9_all.deb) ...
Setting up libapache2-mod-php5 (5.1.2-1ubuntu3.9) ...

Setting up php5 (5.1.2-1ubuntu3.9) ...
kokophone@kokophone-laptop:~$ sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                         [ ok ]
kokophone@kokophone-laptop:~$ sudo gedit/var/www/testphp.php
sudo: gedit/var/www/testphp.php: command not found
kokophone@kokophone-laptop:~$ sudo gedit/var/www/testphp.php
sudo: gedit/var/www/testphp.php: command not found
kokophone@kokophone-laptop:~$ sudo gedit /var/www/testphp.php
kokophone@kokophone-laptop:~$ sudo apt-get install libapache2-mod-php5
Reading package lists... Done
Building dependency tree... Done
libapache2-mod-php5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kokophone@kokophone-laptop:~$ sudo apt-get install libapache2-mod-php5
Reading package lists... Done
Building dependency tree... Done
libapache2-mod-php5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kokophone@kokophone-laptop:~$ sudo tasksel
sudo: tasksel: command not found
kokophone@kokophone-laptop:~$ sudo tasksel
sudo: tasksel: command not found
kokophone@kokophone-laptop:~$ sudo tasksel lampp
sudo: tasksel: command not found
kokophone@kokophone-laptop:~$ clear

kokophone@kokophone-laptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation: Unknown device 2a00 (rev 0c)
0000:00:02.0 VGA compatible controller: Intel Corporation: Unknown device 2a02 (rev 0c)
0000:00:02.1 Display controller: Intel Corporation: Unknown device 2a03 (rev 0c)0000:00:1a.0 USB Controller: Intel Corporation: Unknown device 2834 (rev 03)
0000:00:1a.1 USB Controller: Intel Corporation: Unknown device 2835 (rev 03)
0000:00:1a.7 USB Controller: Intel Corporation: Unknown device 283a (rev 03)
0000:00:1b.0 0403: Intel Corporation: Unknown device 284b (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation: Unknown device 283f (rev 03)
0000:00:1c.1 PCI bridge: Intel Corporation: Unknown device 2841 (rev 03)
0000:00:1c.5 PCI bridge: Intel Corporation: Unknown device 2849 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation: Unknown device 2830 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation: Unknown device 2831 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation: Unknown device 2832 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation: Unknown device 2836 (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
0000:00:1f.0 ISA bridge: Intel Corporation: Unknown device 2815 (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation: Unknown device 2850 (rev 03)
0000:00:1f.2 0106: Intel Corporation: Unknown device 2829 (rev 03)
0000:00:1f.3 SMBus: Intel Corporation: Unknown device 283e (rev 03)
0000:02:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)0000:06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd.: Unknown device 8136 (rev 01)
0000:07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832 (rev 05)
0000:07:09.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0000:07:09.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 12)
0000:07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0000:07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)kokophone@kokophone-laptop:~$ clear

kokophone@kokophone-laptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation: Unknown device 2a00 (rev 0c)
0000:00:02.0 VGA compatible controller: Intel Corporation: Unknown device 2a02 (rev 0c)
0000:00:02.1 Display controller: Intel Corporation: Unknown device 2a03 (rev 0c)0000:00:1a.0 USB Controller: Intel Corporation: Unknown device 2834 (rev 03)
0000:00:1a.1 USB Controller: Intel Corporation: Unknown device 2835 (rev 03)
0000:00:1a.7 USB Controller: Intel Corporation: Unknown device 283a (rev 03)
0000:00:1b.0 0403: Intel Corporation: Unknown device 284b (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation: Unknown device 283f (rev 03)
0000:00:1c.1 PCI bridge: Intel Corporation: Unknown device 2841 (rev 03)
0000:00:1c.5 PCI bridge: Intel Corporation: Unknown device 2849 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation: Unknown device 2830 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation: Unknown device 2831 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation: Unknown device 2832 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation: Unknown device 2836 (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
0000:00:1f.0 ISA bridge: Intel Corporation: Unknown device 2815 (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation: Unknown device 2850 (rev 03)
0000:00:1f.2 0106: Intel Corporation: Unknown device 2829 (rev 03)
0000:00:1f.3 SMBus: Intel Corporation: Unknown device 283e (rev 03)
0000:02:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)0000:06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd.: Unknown device 8136 (rev 01)
0000:07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832 (rev 05)
0000:07:09.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0000:07:09.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 12)
0000:07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0000:07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)kokophone@kokophone-laptop:~$

code of lspci.....

---

### Post by Pumalite on 2007-11-17
Post:

sudo lshw -C sound

---

### Post by kokophone on 2007-11-17
kokophone@kokophone-laptop:~$ sudo lshw -C sound
  *-multimedia
       description: Multimedia controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel
       resources: iomemory:f8700000-f8703fff irq:74


that is sudo lshw -C sound..

---

### Post by Pumalite on 2007-11-17
Your card is recognized and the module loaded. Just to make sure do this:
sudo apt-get install linux-backports-modules-generic
Report back. I suspect your problem might lie somewhere else.

---

### Post by kokophone on 2007-11-17
kokophone@kokophone-laptop:~$ sudo apt-get install linux-backports-modules-generic
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-backports-modules-generic
kokophone@kokophone-laptop:~$

---

### Post by Pumalite on 2007-11-17
They might have been removed from the repos. Try this link:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by kokophone on 2007-11-17
help me for sound...............:(

---

### Post by Pumalite on 2007-11-17
Sorry, I meant this:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by kokophone on 2007-11-17
kokophone@kokophone-laptop:/usr/src/alsa/alsa-driver-1.0.14$ sudo ./configure --with-cards=hda-intel
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/alsa/alsa-driver-1.0.14
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
kokophone@kokophone-laptop:/usr/src/alsa/alsa-driver-1.0.14$ sudo make
make all-deps
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.14'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.14'

Please, run the configure script as first...

kokophone@kokophone-laptop:/usr/src/alsa/alsa-driver-1.0.14$ sudo make install
if [ -L /include/sound ]; then \
                rm -f /include/sound; \
                ln -sf /usr/src/alsa/alsa-driver-1.0.14/include/sound /include/sound; \
        else \
                rm -rf /include/sound; \
                install -d -m 755 -g root -o root /include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /include/sound; \
                done \
        fi
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1
kokophone@kokophone-laptop:/usr/src/alsa/alsa-driver-1.0.14$


I think i wrong in here...:(
please help me...

---

### Post by Pumalite on 2007-11-17
Have you installed all the GStreamers, checked your volume control?
Wha'st the result of typing this in your terminal:
alsamixer

---

### Post by kokophone on 2007-11-17
I don't know exactly of it!!:(

that is my alsamixer

/home/kokophone/Desktop/alsamixer.png

---

### Post by kokophone on 2007-11-17
alsamixer

---

### Post by Majorix on 2007-11-17
Have you maxed your sound volume using
```
sudo alsamixer
```
?

EDIT: Oops cross-posted. Sorry :)

---

### Post by kokophone on 2007-11-17
what is the meaning of alsamixer???
i don't know it!!!..
and main thing is to get sound back...
urs...
kokophone

---

### Post by daimaru on 2007-11-17
> **kokophone said:**
> kokophone@kokophone-laptop:~$ sudo apt-get install linux-backports-modules-generic
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-backports-modules-generic
kokophone@kokophone-laptop:~$

enable the repository in your /etc/apt/sources.list
normally backports are commented out.
this is assuming that what he mentioned actually works . cause i dont know :)

---

### Post by Pumalite on 2007-11-17
[http://en.wikipedia.org/wiki/Alsamixer](http://en.wikipedia.org/wiki/Alsamixer)

---

### Post by kokophone on 2007-11-17
what is that fri???
I dunna understand it..

---

### Post by kokophone on 2007-11-17
Pumalite

I don't love it at all...
so difficult for me..
but i will try it....
so what can I do for it??

---

