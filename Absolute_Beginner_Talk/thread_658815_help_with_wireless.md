---
title: "help with wireless"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by winsall on 2008-01-05
hi all, my names michael.

ive had ubuntu (v7.04 "feisty fawn") on my laptop for about 6 months now, but i havent really used it.
but now im fed up with vista. so im trying to switch to ubuntu. everything is going great, except for my wireless. it just doesnt work.
im using an ACER extensa 4214wxmi which, as far as i can tell, is using a built in atheros wireless card/chip set thinggy.
i followed the instructions here [http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html) to the letter, how ever i just cant get it to work! :(

this is frustrating, as i love ubuntu.
does anyone have any suggestions on what to do/what ive done wrong?

thanks in advance,
michael

P.S. if you need to know, my wireless router is a D-Link DI-624.

---

### Post by the_sorrow on 2008-01-05
Sometimes some distributors share the Idea of wolrd conquest with microsoft, so they only design drivers for microsoft distribution, and those are avaible in Linux, but don't panic there is always another way.
download the a program called ndiswrapper from this link
[http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=562382](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=562382)

follow the instructions on the "install" file and you are done
.
Anything just ask

---

### Post by winsall on 2008-01-05
thanks for such a quick reply! ive downloaded it, and for some reason, i follow the instructions, and it starts off good, but ends in errors.
is it something im doing?

---

### Post by the_sorrow on 2008-01-05
what errors??

---

### Post by winsall on 2008-01-05
haha sorry i realised after i posted that i was kinda vague

well when i go to make install, at the end i get
"mkdir: cannot create directory `/lib/modules/2.6.20-15-generic/misc': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/winnie/ndiswrapper-1.51/driver'
make: *** [install] Error 2"

just to clarify, to change the directory, is the command CD *directory*?

---

### Post by the_sorrow on 2008-01-05
cd is the correct command.
You have to be in the specified folder or it won't work
second the Permission denied it's because you are doing it as a common user type this

sudo -s

it will ask for password type it then press enter, and you will be running as root or administrator in the simple word, follow the steps again...

---

### Post by winsall on 2008-01-05
ok now i get the error

loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’
loadndisdriver.c:549: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/winnie/ndiswrapper-1.51/utils'
make: *** [install] Error 2

it says that about 50 odd times with various variations.

also, it says in the instructions:
You need a recent kernel, at least 2.6.6 or 2.4.26, with header files
for the kernel. Make sure there is a link to the kernel source from
the modules directory. The command

  ls /lib/modules/`uname -r`/build

should have at least 'include' directory and '.config' file.

however i only seem to have include, but not .config. could this be a problem?

sorry for being so newbish :)

---

### Post by zipperback on 2008-01-05
Please open a terminal window and post the output of the following:

ifconfig

iwconfig

lspci



I have an acer with an atheros chip set as well.

- zipperback
:popcorn:

---

### Post by yourpalal on 2008-01-05
I feel like your kernel should be proper if you are running 7.10 try reinstalling ndiswrapper, also try the gui if you haven't already it might work (didn't for me) if you are lucky or typing something wrong in the console.. make sure you "sudo ndiswrapper" or else it will not work, as was previously mentioned

---

### Post by winsall on 2008-01-05
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:24:3A:15:D9  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe3a:15d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13953 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12428 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14379303 (13.7 MiB)  TX bytes:1788791 (1.7 MiB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by theRightNee on 2008-01-05
i've had similar issues

instead of using 

make uninstall

use 

make distclean

i find it works better

---

### Post by winsall on 2008-01-05
thanks for trying nee, but that unfortunately didnt work, it is still displaying the same error

---

### Post by spiderbatdad on 2008-01-05
have you tried runing ```
sudo apt-get update
sudo apt-get upgrade
``` then try to  install again.

---

### Post by ugm6hr on 2008-01-05
> ive had ubuntu (v7.04 "feisty fawn") on my laptop for about 6 months now, but i havent really used it.

In that case, why not just reinstall with Gutsy instead?  The kernal has been updated, and may recognise your device.  Even if it doesn't, you can get a fairly up-to-date version of ndiswrapper from Synaptic Package Manager (with minimal effort), unlike in Feisty.

PS: What Atheros chipset does Vista say the wifi has?  This is the madwifi compatibility list: [http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros)

---

### Post by spiderbatdad on 2008-01-05
you might try the search files application and enter "kernel" as the search and use the drop down menu to tell it to look in "filesystem"  scroll to "kernel.release" and click on it. I believe you must have at least 2.4.26. but 2.6.xx would be better.

---

### Post by winsall on 2008-01-06
thanks for all the help, i was surprised how fast it came in!!

ive decided that it might just be easier to go with ugm6hr's idea and switch to gutsy.
heres to hoping it goes well! :D

---

