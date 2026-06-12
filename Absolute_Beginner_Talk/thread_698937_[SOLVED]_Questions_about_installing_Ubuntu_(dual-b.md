---
title: "[SOLVED] Questions about installing Ubuntu (dual-boot)"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by marty1011 on 2008-02-16
Hi, I am a complete newbie to Linux. I have acquired the Gutsy Gibbon CD couple of days ago and from what I saw in the live session I really liked it. I want to install Ubuntu (dual-boot with Vista) in my brand new HP Pavilion dv6000. I have already looked at the following threads :

[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Now, I have a few questions:-
1. When I shall partition my hard drive, will all the data in the hard drive be erased?

2. Is it better to partition my hard drive before the installation? If so can anyone PLEASE give me an easy-to-follow instruction (thread/website will be appreciated too)? I am a novice and very afraid that I will cause a disaster. However I do want to learn more about Linux and move away from Windows.

3. How much space should I allocate to Ubuntu? 

4. During the live session the speakers and the headphone (8280 ich8, most probably. Sorry for the inconvenience) were not working. After some research I found out that I can tweak the system to solve the problem. Can anyone PLEASE give me an easy-to-follow instruction to solve this problem. (I did find some solutions involving ALSA in my research, but what I found were very puzzling for me)

5. My wireless card is not working with Ubuntu either. It is not my primary concern yet, but I would love to have a functioning wireless card. It is Intel (R) PRO/Wireless 3945ABG. Is there a way to solve the problem?

I really appreciate your help. Thank You.

---

### Post by MasterJS on 2008-02-16
It would be wise to back up your data before creating partitions to avoid this, you shouldn't lose your files because you should be taking space away from your main disk and not deleting Windows. You could use GParted to create partitions before installation.[http://gparted-livecd.tuxfamily.org/]("http://gparted-livecd.tuxfamily.org/")
Basically the amount of space depends on you. The minimum should be about 6 GB so that Ubuntu has enough space for itself (about 3 GB) and space to grow in if you install alot of programs. And the reason your wireless card was not working was because you were using a live cd and the restricted drivers (meaning the proprietary drivers for your wireless card) were not installed. This means Ubuntu could not use it. When you install it, you'll have the choice to install those drivers and have it work properly.

---

### Post by mevets on 2008-02-16
1. Nothing will be earsed. People recommend defraging before partition, but if its a new install of vista its not really necessary.

2. It probably better but not necessary. During the install process you are presented with a partitioning tool.

3. 10 GB is good for a new user. If you decide you like ubuntu alot you may want to ncrease that number in later installs.

5. I have that same card in my Gateway mx6931. The ip3945 driver loads automatically for me. I dont understand why it wouldnt load for you. You might have diabled it using the restricted-manager, but it is enabled by default.

---

### Post by JoshuaRL on 2008-02-16
I agree with MasterJS on most of that, but I would suggest just using the installer to partition.  That is pretty bombproof if you defrag Windows first.  Just much easier and more stable if you're new.

Welcome to Ubuntu!

---

### Post by marty1011 on 2008-02-17
Thank You Everyone! Right now I am typing this message from Ubuntu. I have installed Ubuntu in my laptop without any trouble. Thank You Everyone for your help. I have one more question: 

How can I enable my wireless card now?

Sorry for the trouble. Again Thank You Very Much!

---

### Post by JoshuaRL on 2008-02-17
What type of card do you have?  Can you post the exact make and model?

---

### Post by marty1011 on 2008-02-17
> **JoshuaRL said:**
> What type of card do you have?  Can you post the exact make and model?

Thanks for helping me. My card is Intel (R) PRO/Wireless 3945ABG. Again Thanks A Lot.

---

### Post by JoshuaRL on 2008-02-17
[http://ipw3945.sourceforge.net/INSTALL](http://ipw3945.sourceforge.net/INSTALL)

That should tell you how to install the driver for it.

I also found:

[http://ubuntuforums.org/showthread.php?t=695756](http://ubuntuforums.org/showthread.php?t=695756)
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/66266](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/66266)
[https://help.ubuntu.com/community/WifiDocs/Driver/iwlwifi_Intel_3945_4965/gutsy?highlight=%28intel%29%7C%283945ABG%29](https://help.ubuntu.com/community/WifiDocs/Driver/iwlwifi_Intel_3945_4965/gutsy?highlight=%28intel%29%7C%283945ABG%29)
[http://intellinuxwireless.org/](http://intellinuxwireless.org/)

---

### Post by marty1011 on 2008-02-17
Thanks A Lot for your help JoshuaRL. I will follow the instructions in the websites. I have solved my sound problem as well. Here is the site that I used:

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

Again Thanks A Lot for your help.

---

