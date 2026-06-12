---
title: "Installing wireless network drivers"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by coubury on 2008-02-13
I followed this tutorial on how to get my wireless adapter working but im having a few problems

[http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547)

and also this [http://www.aircrack-ng.org/doku.php?id=rt61](http://www.aircrack-ng.org/doku.php?id=rt61)

but it dosent seem to do anything

--23:26:23--  [http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz)
           => `rt61-cvs-daily.tar.gz.2'
Resolving rt2x00.serialmonkey.com... 208.100.15.174
Connecting to rt2x00.serialmonkey.com|208.100.15.174|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 333,673 (326K) [application/x-tar]

100%[====================================>] 333,673       35.28K/s    ETA 00:00

23:26:38 (32.85 KB/s) - `rt61-cvs-daily.tar.gz.2' saved [333673/333673]

coubury@coubury-desktop:~$ tar xvfz rt61-cvs-daily.tar.gz
rt61-cvs-2008021316/
rt61-cvs-2008021316/FAQ
rt61-cvs-2008021316/THANKS
rt61-cvs-2008021316/CHANGELOG
rt61-cvs-2008021316/CVS/
rt61-cvs-2008021316/CVS/Root
rt61-cvs-2008021316/CVS/Repository
rt61-cvs-2008021316/CVS/Entries.Log
rt61-cvs-2008021316/CVS/Entries
rt61-cvs-2008021316/WPA_Supplicant/
rt61-cvs-2008021316/WPA_Supplicant/drivers.c
rt61-cvs-2008021316/WPA_Supplicant/CVS/
rt61-cvs-2008021316/WPA_Supplicant/CVS/Root
rt61-cvs-2008021316/WPA_Supplicant/CVS/Repository
rt61-cvs-2008021316/WPA_Supplicant/CVS/Entries
rt61-cvs-2008021316/WPA_Supplicant/driver_ralink.c
rt61-cvs-2008021316/WPA_Supplicant/wpa_supplicant_example.conf
rt61-cvs-2008021316/WPA_Supplicant/readme
rt61-cvs-2008021316/WPA_Supplicant/defconfig
rt61-cvs-2008021316/WPA_Supplicant/driver_ralink.h
rt61-cvs-2008021316/WPA_Supplicant/Makefile
rt61-cvs-2008021316/LICENSE
rt61-cvs-2008021316/Module/
rt61-cvs-2008021316/Module/auth.c
rt61-cvs-2008021316/Module/rt2561.bin
rt61-cvs-2008021316/Module/rt2x00debug.h
rt61-cvs-2008021316/Module/md5.c
rt61-cvs-2008021316/Module/rtmp_main.c
rt61-cvs-2008021316/Module/rt_config.h
rt61-cvs-2008021316/Module/assoc.c
rt61-cvs-2008021316/Module/CVS/
rt61-cvs-2008021316/Module/CVS/Root
rt61-cvs-2008021316/Module/CVS/Repository
rt61-cvs-2008021316/Module/CVS/Entries
rt61-cvs-2008021316/Module/STA_iwpriv_ATE_usage.txt
rt61-cvs-2008021316/Module/wpa.c
rt61-cvs-2008021316/Module/rt2561s.bin
rt61-cvs-2008021316/Module/sync.c
rt61-cvs-2008021316/Module/rtmp_data.c
rt61-cvs-2008021316/Module/rtmp_info.c
rt61-cvs-2008021316/Module/iwpriv_usage.txt
rt61-cvs-2008021316/Module/mlme.h
rt61-cvs-2008021316/Module/connect.c
rt61-cvs-2008021316/Module/rtmp_tkip.c
rt61-cvs-2008021316/Module/rt2661.bin
rt61-cvs-2008021316/Module/auth_rsp.c
rt61-cvs-2008021316/Module/oid.h
rt61-cvs-2008021316/Module/rt2661.h
rt61-cvs-2008021316/Module/rtmp_init.c
rt61-cvs-2008021316/Module/TESTING
rt61-cvs-2008021316/Module/rtmp.h
rt61-cvs-2008021316/Module/mlme.c
rt61-cvs-2008021316/Module/md5.h
rt61-cvs-2008021316/Module/wpa.h
rt61-cvs-2008021316/Module/eeprom.c
rt61-cvs-2008021316/Module/rtmp_wep.c
rt61-cvs-2008021316/Module/README
rt61-cvs-2008021316/Module/rtmp_def.h
rt61-cvs-2008021316/Module/Makefile
rt61-cvs-2008021316/Module/rtmp_type.h
rt61-cvs-2008021316/Module/rt2x00debug.c
rt61-cvs-2008021316/Module/ReleaseNote
rt61-cvs-2008021316/Module/sanity.c
coubury@coubury-desktop:~$ cd rt61-cvs-*
coubury@coubury-desktop:~/rt61-cvs-2008021316$ cd Module
coubury@coubury-desktop:~/rt61-cvs-2008021316/Module$ make sudo su
make: *** No rule to make target `sudo'. Stop.
coubury@coubury-desktop:~/rt61-cvs-2008021316/Module$ 




to get my wireless network card working

but now i have the linux driver for the ralink rt61pci

Im a novice and just wanted about of help on how i could install these

the name of the folder on my desktop is rt61pci

could one of use kind souls help me out please

Cheers.

---

### Post by Blutack on 2008-02-13
> make sudo su
is not the correct syntax.
All you want to do is type 
> make
and then 
> sudo make install
if the build is successful.

---

### Post by coubury on 2008-02-13
I put this in first
 wget [http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz)
tar xvfz rt61-cvs-daily.tar.gz
cd rt61-cvs-*
cd Module
make

and i get this (well the last 3 lines because its the same as above 

root@coubury-desktop:/home/coubury# cd rt61-cvs-*
root@coubury-desktop:/home/coubury/rt61-cvs-2008021316# cd Module
root@coubury-desktop:/home/coubury/rt61-cvs-2008021316/Module# make

so what should i do there's already a #make at the end?

keeping in mind this is the installation intructions

Then, as root, type:

make install
modprobe rt61

You also need the following each time you want to use the device in monitor mode:

 iwpriv <interface name> rfmontx 1

---

### Post by spiderbatdad on 2008-02-13
so what kind of wireless adapter are you working with?

---

### Post by coubury on 2008-02-13
Edimax 7128 pci card 

runs on a ralink chip set rx61

---

### Post by spiderbatdad on 2008-02-13
not sure the linux driver for this card supports wpa encryption.

[https://bugs.launchpad.net/ubuntu/+bug/150392](https://bugs.launchpad.net/ubuntu/+bug/150392)

[http://www.edimax.com/en/support_detail.php?pd_id=1&pl1_id=1&pl2_id=44](http://www.edimax.com/en/support_detail.php?pd_id=1&pl1_id=1&pl2_id=44)

---

### Post by coubury on 2008-02-13
would that be why i cant continue on with the installation

actually im nearly 100% certain it should work because iv done abit of research on thats why i installed ubuntu

any ideas why i cant seem to go further?

---

