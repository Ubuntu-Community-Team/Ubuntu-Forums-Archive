---
title: "atheros wireless"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by sven_henson on 2007-02-15
I just switched over to Ubuntu today and I am terribly new to linux. Can anyone explain to me how to get my wireless adapter working, I've tried many things but i doubt i did any of em right. I have an Atheros AR5006EG wirless card and it isn't being recognized. Can anyone help

---

### Post by jimrz on 2007-02-15
> **sven_henson said:**
> I just switched over to Ubuntu today and I am terribly new to linux. Can anyone explain to me how to get my wireless adapter working, I've tried many things but i doubt i did any of em right. I have an Atheros AR5006EG wirless card and it isn't being recognized. Can anyone help

check to make sure you have the kernel "restricted modules" installed. easiest way is to go the top panel to System > Administration > Synaptic Package Manager, then search in synaptic and ensure that they are loaded. if not, simply install them, restart and you should be good to go. if not, post back here and tell us which version of ubuntu you have installed and give some particulars on your hardware (especially the make/model of your wifi device).

---

### Post by sven_henson on 2007-02-15
tried installing the restricted modules but no such luck. I think the specifications are:
Atheros AR5006EG
PCI IEEE 802.11b/g
2.4 GHz
Any help would be awesome

---

### Post by Cable on 2007-02-15
I have an Atheros chipset as well, and I simply installed the "linux-restricted-modules-generic" package to get it working perfectly.  I know jimrz already mentioned restricted modules, but I figured I would give the exact package name to be sure that you did indeed install it.

---

### Post by sven_henson on 2007-02-15
Still no luck.

---

### Post by Ehnvis on 2007-02-16
What does iwconfig give you? I'm running an atheros based wlan card in my HP laptop and it worked out of the box with Ubuntu 6.10 as the restricted modules already comes with it.

What kind of errors/problems do you have, the more info you get the better it will be for us that tries to help you.

---

### Post by Spr0k3t on 2007-02-16
Which kernel are you using?

```
uname -r
```

---

### Post by sven_henson on 2007-02-16
Thanks but still no success
Iwconfig gives me:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

How do i find out which kernel i am using...also i've been trying to figure out my kernelpath
Any suggestions?

SVEN

---

### Post by Ehnvis on 2007-02-16
hmm, that iwconfig doesnt say much or your wlan adapter isn't showing. Does lspci show anything about your atheros wlan card? Is the wlan card active? I know i have to press a button on mine to turn it on so it's visible for the system.

---

### Post by sven_henson on 2007-02-16
I have just switched over to the Ubuntu 6.10 OS from windows and i just cant get my wireless card working. I have installed the driver via ndiswrapper but the hardware is not recognized. I am running a toshiba A100 satalite with a Atheros AG5006EG wireless card. The specifications are:
Chipset:                  AR2423
Frequency Band:       2.4 GHz
Network Standard:     802.11b, 802.11g
Modulation Modes:      OFDM with BPSK, QPSK,
                                16 QAM, 64 QAM;
                                DBPSK, DQPSK, CCK
FEC Cocing Rate:         1/2, 2/3, 3&#8260;4
Hardware Security:    AES, TKIP, WEP
Quality of Service:      802.11e (draft)
Media Access Technique:    CSMA/CA
Host Interface:             PCI Express
Peripheral Interface:    GPIOs, LEDs
Supported Data Rates:  IEEE 802.11b 1 to 11 Mbps
                                   IEEE 802.11g 6 to 54 Mbps

ALso here is the lshw output that i think pertains to my wireless card, i'm not 100% positive however:

*-pci:1
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 4
             bus info: pci@00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Ethernet controller
                product: Atheros Communications, Inc.
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list
                resources: iomemory:c0100000-c010ffff irq:233

If any body has any solutions please help me

Thanks
SVEN

---

### Post by sven_henson on 2007-02-16
I have posted a new thread with my cards specifications, lshw output and a summary of where i am under "atheros wireless card troubles". If anyone can help the info is there, this is slowly eating away at my sanity

Cheers
Sven

---

### Post by dannyboy79 on 2007-02-16
next time don't double post, the admins are simply going to combine them now.

sven, the admins will combine this with the other thread you already created, please don't double post anymore. thanx

this has been posted as a bug with madwifi, check it out here. [http://madwifi.org/ticket/859](http://madwifi.org/ticket/859)
i am not sure which madwifi version edgy is using but you might want to compile madwifi from source


10/02/06 19:04:06: Modified by mrenzmann
Support for PCI express cards has been fixed in HAL 0.9.18.0, which has been added in r1711. So it should work if you use a matching repository snapshot of r1711 or later (for example from [http://snapshots.madwifi.org/madwifi-ng](http://snapshots.madwifi.org/madwifi-ng) ). However, HAL 0.9.18.0 needs further testing and is currently suspicious of containing some bugs that need to be fixed. 

10/02/06 19:05:40: Modified by mrenzmann
status changed from new to closed. 
resolution set to fixed. 
milestone set to version 0.9.3. 
For now I close this ticket as "fixed". Feel free to reopen it if it shows up that there are still issues with this PCI express chipsets in r1711 or later. 

01/17/07 12:43:10: Modified by VladoK

---

### Post by sven_henson on 2007-02-16
Sorry, i'll keep that in mind. Still in desperate need of help

---

### Post by bapoumba on 2007-02-16
Thanks, threads merged ;)

---

### Post by dannyboy79 on 2007-02-16
> **sven_henson said:**
> Sorry, i'll keep that in mind. Still in desperate need of help

well, did you see my post about HAL and madwifi? I can't help more than simply point this out to you. I luckily have the Atheros AR5212 chipset in a Netgear WG511T and mine works out of the box. good luck

---

### Post by sven_henson on 2007-02-16
I am having some troubles with madwifi and HAL. Can some one give me a detailed step by step how to get both of these up and running. Sorry but i am mad n00bish.

Thanks
SVEN

---

### Post by Lonthong on 2007-02-22
I have the exact same card (Atheros AR5006EG).
The latest madwifi driver still does not support this card.
Instead, you should try madwifi-ng r 1711 or later. You can download it from [here]("http://snapshots.madwifi.org/madwifi-ng/")

If you have restricted-modules already installed, you must disable & uninstall it first
$ sudo ifconfig ath0 down
go to your madwifi folder
$ cd scripts
$ ./madwifi-unload.bash
$ ./find-madwifi-modules.sh /lib/modules/
$ cd ..
$ sudo make
$ sudo make uninstall   (just to make sure the older driver will be completely  uninstalled)
$ sudo make install
$ sudo modprobe ath_pci
$sudo modprobe wlan_scan_sta
$ sudo ifconfig ath0 up
System - administration - networking: You should now see your wireless device there

---

### Post by ubuntu_demon on 2007-02-22
> **sven_henson said:**
> 
...
How do i find out which kernel i am using
...


$uname -r

And now choose one of these :
$sudo aptitude install linux-386
$sudo aptitude install linux-686
$sudo aptitude install linux-generic

---

### Post by ubuntu_demon on 2007-02-22
> **sven_henson said:**
> I have just switched over to the Ubuntu 6.10 OS from windows and i just cant get my wireless card working. I have installed the driver via ndiswrapper but the hardware is not recognized. 
............


Don't use ndiswrapper for atheros based cards. Please undo the steps you did to set up ndiswrapper. Install the correct restricted kernel modules like I explained in my previous post (can't hurt). And then follow Lonthong's instructions.

good luck!

---

### Post by twk3 on 2007-02-25
I am having the same problem with my atheros wireless card. 


And, like me, sven_henson won't be able to follow Lonthong's steps because our cards are Unclaimed and will not have a logical name. So ath0 in the first step will return "No Such Device" 

Is there a way we can reference the physical device without a logical name?

---

### Post by twk3 on 2007-02-26
Sorry I just realized that that line is for people who have already have a module installed. 


My next problem is that, even when I am logged in as root, I do not have permission to run the make command. I have noticed that in a text mode I do not have permission to run any files at all. Only run commands. Even when I do a gedit from a terminal I get that error (but then the gedit application come up).

---

### Post by dannyboy79 on 2007-02-26
that doesn't make any sense? waht happpens when you do ```
groups yourusernamehere
``` your user should be within the adm and admin groups which allows you to sudo. As far as not being able to run make even as root, that sounds even more messed up. is your make file executable? ```
sudo chmod +x make
``` would make it executable.

---

### Post by twk3 on 2007-02-26
My problem was that when I installed I was was playing around with it to get the feel and I think I installed the file system as Read Only. I have just reinstalled, and that fixed that, I grabbed the debian testing madwifi tools package and installed it, then I installed my unrestricted packages, restarted and now my wireless is working fine. 


I hope sven_henson can get his working. Thanks for the help.

---

### Post by sven_henson on 2007-02-27
hi all
It seems that i was having the same problems as twk3 so i will try what he described. I'm gonna have to reinstall ubuntu however as i had to switch back to windows sadly as i desperately nedd my wireless access. However, i will try again soon and hopefully when i post again my wireless will be working

Thanks all
Sven

---

### Post by sven_henson on 2007-03-01
still tryin to getmy card working. While following the steps i get several errors. First:

root@steve-laptop:/home/steve/madwifi-ng-r2165-20070301# sudo ifconfig ath0 down
ath0: ERROR while getting interface flags: No such device

Then if i continue:

root@steve-laptop:/home/steve/madwifi-ng-r2165-20070301# cd scripts
root@steve-laptop:/home/steve/madwifi-ng-r2165-20070301/scripts# ./madwifi-unload.bash
FATAL: Module ath_pci not found.
FATAL: Module ath_rate_sample not found.
FATAL: Module ath_hal not found.
FATAL: Module wlan not found.


Still no idea what to do. If anyone cna help it would be more than appreciated.

Cheers
Sven

---

### Post by sven_henson on 2007-03-08
Hi all
It seems i got past the errors mentioned above however when preforming the make command i get a number of errors such as:

/root/madwifi-ng-r2182-20070308/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory

And at the very end:

make: *** [modules] Error 2

Can anyone help, i dont wanna have to go back to windows

Thanks
Sven

---

### Post by sven_henson on 2007-03-09
Hey all
I finally got it working. I used apt and the debian repository to auto install it. Now that its working i can finally take windows of my computer for good. Just wanted to say thanks for all ur help, u guys rock

Cheers
Sven

---

### Post by sven_henson on 2007-03-11
Hey
I figured i would post how i solved my problem for anyone with the same problem, this solution is great for those new to linux like myself because it is pretty much automated. Just follow this guide:

[http://madwifi.org/wiki/UserDocs/Distro/Debian/MadWifi](http://madwifi.org/wiki/UserDocs/Distro/Debian/MadWifi)

Cheers

Sven

---

