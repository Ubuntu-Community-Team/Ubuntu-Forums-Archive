---
title: "Trouble booting on fresh install + usb wifi trouble"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by greatwolf on 2007-03-28
Hi all,

I'm new to ubuntu and just recently downloaded the ubuntu install/livecd 7.04 beta. Running to a lot of problems in getting ubuntu to boot after clean install and unable to get my netgear wpnt121 wirelss usb adapter to work.

Here's what I've tried so far:

ubuntu was installed on primary slave on second partition of hd. Installed grub bootloader and said yes to writing on master boot record. Reboot displays "Error Loading Operating System". Wiped the second partition again and reinstalled but this time used Lilo bootloader. It loads up but it seems to get stuck somewhere amist all those commands and the ubuntu login never comes up. Putted livecd in again and tried to execute linux rescue by pressing F6. It loads for a bit and then it stop at a spot complaining unable to mount root="". Retried it with linux rescue root=/dev/hdb2 and again it gives me the same thing unable to mount root='hdb2'. So it looks like I can't even get to the shell from the livecd. 

Eventually I just wiped my first partition of 2nd hd, switched the jumpers around so my primary slave is master and primary master is slave. Did a complete repartition and reinstall in text mode so the partition is on the very first sectors of the hd. Now a reboot finally works and Ubuntu boots up. 

so my problem is what is up with grub boot loader? Does ubuntu know how to properly configure the boot sectors of my hd or what? It seems if ubuntu isn't installed on the very first primary master and on the first starting partition(where my first windows install was) then it fails to boot with that stupid error msg. 

Ok, my second problem is getting my netgear wpnt121 usb adapter to work. I mainly tried it from the liveboot environment. I installed ndiswrap from the synaptic package manager. there were 2 versions there, so I went with the later 1 first. Popped open the terminal and did the standard commands for installing them found in the ubuntu documentation. The problem starts when I tried to sudo modprobe ndiswrapper. It causes a complete system lock -- absolutely nothing would respond. so i had to do a cold reboot. Rebooted back into windows and downloaded the latest stable release of ndiswrapper (1.39 at time of this post). Rebooted again into livecd ubuntu. Did a make and make install on the ndiswrap 1.39 I just downloaded. Performed the procedures and again same thing, hard lockup at sudo modprobe ndiswrapper. Unplugged my adapter and did those procedures again. This time no lock up but the moment I plug my adapter back in it locks up again. 

So this time I installed the other older ndiswrapper from the livecd (1.1 I believe) through synaptic package manager. Did the steps again and surprisingly it didn't lock up this time. ndiswrapper -l shows my adapter is installed but how do I actually use it and get it to connect? iwconfig just shows lo (loopback) and eth0 (my onboard ethernet) and they both say no wireless extension. How do you get wlan0 to map to my netgear usb wireless device and show up in iwconfig so I can actually configure the damn thing?

Thanks

---

### Post by greatwolf on 2007-11-06
Could I at least get a response on getting my wireless adapter to work?

Thanks

---

