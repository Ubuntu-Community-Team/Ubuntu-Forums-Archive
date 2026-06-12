---
title: "Installer Freezes Immediately"
date: 2012-04-26
forum: Apple Hardware Users
---

### Post by dotbat on 2012-04-26
I have been trying to install Ubuntu (11.10, 12.04, 32 and 64-bit) on my Macbook Pro for a while, and every version gives me the same problem. I can boot into the CD or DVD just fine, and even run it live, install drivers, etc, just fine. The problem occurs when I try to install. When I hit continue on the first page (language page), it gives me the loading cursor and never gets past that screen. I haven't been able to find this issue online anywhere. Any help?

Macbook Pro 5,4
Core 2 Duo
8 GB RAM
HDD in HDD bay (with my data)
SSD in Optical bay (with my OS)
Burning/Booting from USB optical drive

I'm trying to install onto some free space on my HDD.

Thanks!

---

### Post by pounsg on 2012-04-27
Hi,
I can't help you because I have exactly the same problem when trying to install 64bit 12.04 on a macbook pro 5,2. The installation stop on the "prepare to install" page. No debug information from ubiquity. 11.10, 11.04, 10.10 and 10.04 installation work on the same machine :(
I try with the alternate CD and let you know...

---

### Post by Ronan0912 on 2012-04-27
Hi,

It's the same problem for me. Installation freezes when I hit the continue button (64bit 12.04). I have a macbook pro 8.1. I boot from a CD because I can't boot from a USB key (With the old version of ubuntu, it was necessary to boot with a USB key and a CD).

Anyone have an idea ?

Ronan

---

### Post by pounsg on 2012-04-27
alternate cd is not a good option. grub-update silently fails and let you with a grub prompt at reboot. I have chrooted with a live CD, reinstall grub and make a grup-update with no luck. It doesn't boot. It stops on a purple screen. I'm burning a 11.10 CD :(

---

### Post by Ronan0912 on 2012-04-27
Apparently, it's a problem with the 64 bits release. A colleague said to me that he installed with success the 32 bits version on his macbook pro 6.2 (he had the same problem with the 64 bits version).

I think we will have to wait for the next iso :(.

Ronan

---

### Post by dotbat on 2012-04-28
> **Ronan0912 said:**
> Apparently, it's a problem with the 64 bits release. A colleague said to me that he installed with success the 32 bits version on his macbook pro 6.2 (he had the same problem with the 64 bits version).

I think we will have to wait for the next iso :(.

Ronan

I can't even get the 32 bit to work... but I might try a couple more.

---

### Post by bravegag on 2012-04-28
Hi there!

I just installed Ubuntu 12.04 in my MBP 17'' 64b Intel 2 Core Duo 5,2 Mid 2009 running latest OS X Lion.

I was having the same problem until I found this guide, and this is the closest that describes what I did after a lot of trial and error:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:_Mac_OSX_and_Ubuntu](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:_Mac_OSX_and_Ubuntu)

If you put in the Ubuntu installation CD, and restart it will do nothing, it just freezes. So what worked for me:

1- put the CD in
2- restart (press Alt-Option key while restarting)
3- This is the MOST important bit, you must stop the booting of the CD as described/quoted below and get to the **nomodeset** install option otherwise you are gonna hang on that black screen forever:

"Booting into Ubuntu this way takes many minutes, including a  minutes-long period where Ubuntu appears to have locked up on the boot  menu. Most likely it has not. **Just wait! *note I had to set the boot option to nomodeset. If you press function f6 at the boot options screen you can choose that option.* *Note 2: I had to press function f6 when I saw a man and keyboard.***"

HTH,
Best regards,
Giovanni

---

### Post by bradleyjones on 2012-04-28
I had this problem a while ago and for me it had something to do with just using the standard iso image from ubuntu.com/download page (i.e. the one meant for standard Desktop PCs) and not the mac specific image.

Not sure if you are already trying the mac specific version but if not you can find it here for 12.04 -  [http://cdimages.ubuntu.com/releases/precise/release/ubuntu-12.04-desktop-amd64+mac.iso](http://cdimages.ubuntu.com/releases/precise/release/ubuntu-12.04-desktop-amd64+mac.iso)

---

### Post by Ronan0912 on 2012-04-29
I tried with the normal and +mac version. In both cases, it freezes after clicking on the "continue" button of the "preparing to install" step.

I also tried what bravegag explained previously. Even with  the **nomodeset** install option the installation stops at the same step.

I don't know what more I can do !

---

### Post by bravegag on 2012-04-29
I remember it worked for me to first do "Try Ubuntu" and once I was in, then I started the installation process. Maybe you can try this as well. Are you sure you set the nomodeset correctly? if you e.g. "Esc" it will discard the setting and continue or restart not sure. 

What I can do is repeat step by step what I did and post it here but now is 2am so need to go2bed :(

---

### Post by Ronan0912 on 2012-04-30
It is not working even if I try ubuntu before. Moreover, I am quite sure to set the nomodeset correctly and after I choose Install Ubuntu from the menu. Is there something special to do after ?

I believe that when the problem occurs, the installer checks the disks status and the existing partitions. So, maybe there is a problem with my partition table but I don't know what. I have a partition for Mac OS X, a swap space of the old version of ubuntu (11.10) and a free space formatted in Ext4 where I want to install ubuntu 12.04. I also have a SSD.

I found on the french ubuntu forum people with exactly the same problem : [http://forum.ubuntu-fr.org/viewtopic.php?id=897031](http://forum.ubuntu-fr.org/viewtopic.php?id=897031)

---

### Post by pounsg on 2012-05-01
> **Ronan0912 said:**
> It is not working even if I try ubuntu before. Moreover, I am quite sure to set the nomodeset correctly and after I choose Install Ubuntu from the menu. Is there something special to do after ?

I believe that when the problem occurs, the installer checks the disks status and the existing partitions. So, maybe there is a problem with my partition table but I don't know what. I have a partition for Mac OS X, a swap space of the old version of ubuntu (11.10) and a free space formatted in Ext4 where I want to install ubuntu 12.04. I also have a SSD.

I found on the french ubuntu forum people with exactly the same problem : [http://forum.ubuntu-fr.org/viewtopic.php?id=897031](http://forum.ubuntu-fr.org/viewtopic.php?id=897031)

Are you french too ? I have the same problem (with +mac or normal version, freeze when clicking on "continu"...) and I choose french langage. Maybe it is just related to language. Have you tried to make the installation in english ? I'm not at home, but I will try this tomorrow...

Edit : I've just read the french post, it seems more related to partition detection... I was too simple :)

---

### Post by Ronan0912 on 2012-05-01
> **pounsg said:**
> Are you french too ? I have the same problem (with +mac or normal version, freeze when clicking on "continu"...) and I choose french langage. Maybe it is just related to language. Have you tried to make the installation in english ? I'm not at home, but I will try this tomorrow...

Edit : I've just read the french post, it seems more related to partition detection... I was too simple :)

Yes, I am french too. I tried only with English language but I don't think the problem comes from here ...
Apparently, from the log file (/var/log/syslog), the problem is due to the detection of mac os x partition. Indeed, there is this error message : "macosx-prober: debug: /dev/sda2 is  an HFS+ partition".
I succeed in unfreezing the installer by killing several times the "grub-mount" process. Nevertheless, the grub is not installed correctly at the end so it's not possible to boot on ubuntu from the refit menu.

Why ubuntu 12.04 64 bits hates the hfs+ partition so much ?

---

### Post by bravegag on 2012-05-02
Hi there!

So this is how it worked for me in detail (I had to reinstall Ubuntu today):

MBP 17'' Mid 2009 Lion latest on Intel 2 Core Duo, Ubuntu 12.04

1) Place Ubuntu CD 
2) restart Mac OS X 
3) Press Alt (Opt) key
4) Wait for the Ubuntu CD to load
5) Choose the CD icon labeled "Window" make sure you pick the CD icon and not the HDD icon. You must choose "Window", the other CD icon choice did not work for me.
6) When is loading press Fn->F6 at the same time i.e. F6 key. You will probably see a man and a keyboard but even if you don't keep Fn->F6 down and wait
7) At this point you should see the Ubuntu install options and menu.
8 ) Press Fn->F6 again and set the nomodeset option.
9) At this point you can do whatever you want but I choose "Try Ubuntu".
10) Once Ubuntu is running you can use the icon in the Desktop "Install Ubuntu"
11) Make sure to choose carefully how much HDD space you use as two dialogs will overlap, there are two dialogs and one ends up on top of the other somehow. By mistake I ended with a 28GB big MBR partition which only requires 1MB very stupid default for installing Ubuntu alongside Mac OS X btw. I had no choice but reinstall Ubuntu and delete the BOOTCAMP partition explicitly otherwise the same issue would happen again of this wasted high amount of GB for the Ubuntu MBR partition.

I could not figure out how to have a smaller swap partition. It gets assigned automatically and since I have 4GB RAM it gets 4GB of SSD disk space and this is not cheap given the SSD space prices ... I'd prefer the swap to be at most 1GB and not 4GB.

That's it. I have done this above at least 3 times and it always works.

HTH,
Best regards,
Giovanni

---

### Post by Searge on 2013-02-21
> **bravegag said:**
> Hi there!

So this is how it worked for me in detail (I had to reinstall Ubuntu today):

MBP 17'' Mid 2009 Lion latest on Intel 2 Core Duo, Ubuntu 12.04

1) Place Ubuntu CD 
...
11) Make sure to choose carefully how much HDD space you use as two dialogs will overlap, there are two dialogs and one ends up on top of the other somehow...

Giovanni, make sure u carefully read this topic.
IT FREEZES BEFORE YOU ABLE PARTITION HD!!!!!

BTW. Does anyone solve problem with partition on Macbook Pro 5,3? I have same problem, tried Ubuntu 12.10 amd64/amd64+mac, 12.04 x86/amd64... neither works )-:

---

