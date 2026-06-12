---
title: "Difficulty installing wifi wrapper"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by Rusty-83 on 2007-07-07
Hi all, I'm a complete nub at linux and would appreciate some help getting my wifi connection up and running so I can start using / learning linux on a daily basis.

Problem being Ubuntu (latest version) isn't detecting my wifi card in the 'administration -> network tools' menu.

I have tried installing the ndiswrapper but I get a lot of error messages along way, the installation instructions explain I should have an 'include' folder which I have and a '.config' file which I can't see.
Reading the error messages its possible I don't have the source on my computer? Though looking through the options in Ubuntu when I try tick the source option it says I need an internet connection (ironic), there is an option to install from driver disc but nothing happens if I try use the installation cd.

I have included below some console commands and results that might help diagnose the problem, thanks:
(note that to simpllify matters I have disabled the onboard ethernet ports through bios, and I have a linksys wifi pci card)


[COLOR="red"]lspci:[/COLOR]
01:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

[COLOR="Red"]ifconfig:[/COLOR]
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:1332 (1.3 KiB)  TX bytes:1332 (1.3 KiB)

[COLOR="red"]iwconfig:[/COLOR]
lo        no wireless extensions. 

eth1      IEEE 802.11b/g  ESSID:"D"  Nickname:"Broadcom 4306" 
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off 
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

[COLOR="red"]ls /lib/modules/`uname -r`/build:[/COLOR]

arch  block  crypto  drivers  fs  include  init  ipc  kernel  lib  Makefile  mm  Module.symvers  net  scripts  security  sound  ubuntu  usr 

[COLOR="red"]make:[/COLOR]
make -C driver 
make[1]: Entering directory `/home/dave/wifi_driver/ndiswrapper-1.47/driver' 
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/dave/wifi_driver/ndiswrapper-1.47/driver 
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic' 
  Building modules, stage 2. 
  MODPOST 1 modules 
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic' 
make[1]: Leaving directory `/home/dave/wifi_driver/ndiswrapper-1.47/driver' 
make -C utils 
make[1]: Entering directory `/home/dave/wifi_driver/ndiswrapper-1.47/utils' 
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c 
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory 
loadndisdriver.c:16:19: error: stdio.h: No such file or directory 
loadndisdriver.c:17:19: error: errno.h: No such file or directory 
loadndisdriver.c:18:20: error: string.h: No such file or directory 
loadndisdriver.c:19:20: error: libgen.h: No such file or directory 
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory 
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory 
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory 
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory 
loadndisdriver.c:26:20: error: unistd.h: No such file or directory 
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory 
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7, 
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11, 
                 from loadndisdriver.c:28: 
etc...

---

### Post by chamberlain2006 on 2007-07-07
Your problem is that you have to install the "build-essential" package (sudo apt-get install build-essential)

---

### Post by macogw on 2007-07-07
You don't need ndiswrapper for that wireless card.  The drivers are already there. All you need is firmware.  You can get it like this:
> sudo apt-get install bcm43xx-fwcutter

---

### Post by Rusty-83 on 2007-07-07
Not sure what I'm doing wrong but when I run this apt-get commands I get a message like:

Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
E: Couldn't find package bcm43xx-fwcutter 

I've managed to install the build essential package through the package manager and it has helped me install the ndiswrapper (thanks)  but I'm still not having any joy detecting my wireless card.

[COLOR="Red"]iwconfig [/COLOR]
lo        no wireless extensions. 

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306" 
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off 
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

[COLOR="red"]ndiswrapper -l [/COLOR]
bcmwl5c : driver installed 
        device (14E4:4320) present (alternate driver: bcm43xx) 


Also I can't find the firmware mentioned in the package manager, how else can I obtain it? thanks.

---

### Post by Vague on 2007-07-07
> **Rusty-83 said:**
> Not sure what I'm doing wrong but when I run this apt-get commands I get a message like:

Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
E: Couldn't find package bcm43xx-fwcutter 

Do you have the Universe repository enabled?

---

### Post by Fran89 on 2007-10-19
> **chamberlain2006 said:**
> Your problem is that you have to install the "build-essential" package (sudo apt-get install build-essential)

THANK YOU THANK YOU THANK YOU this solved my problem at least !!:) i need this to compile and install the wrapper thanks now my D-Link DWA-130 is up and running

---

