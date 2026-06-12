---
title: "Triple booting"
date: 2013-08-26
forum: Apple Hardware Users
---

### Post by DurpnHard on 2013-08-26
Hey everybody, I'm trying to triple boot my macbook pro but having a hard time doing this. I would like to have mtn lion, ubuntu, and windows 7. The hardware I have is Macbook Pro 15" (early 2011); 8,2. I have looked pretty much everywhere but nothing is very much help.

First of all, a few questions I have:
 
I know that macs run with uefi, is this really that big of an issue seeing as windows runs bios? 
Is it an going to be an issue upgrading versions of ubuntu, or switching distros if it ever comes to that?
What bootloader has the best track record for holding this kind of stuff together? I have heard rEFInd suggested and suggested I do not use.

Any tips/points in the right direction would be more than appreciated, also explanations of why it wont work if it cant will do just as well.

---

### Post by SilverOne on 2013-08-26
Hi, 

apples' boot loader cannot handle triple boot and will only get you bios compatibility mode when booting other partitions through it. this means that if you have a >=15" mbp you will only have access to the amd/nvidia card. However, you should know that getting gpu switching to work is extremely difficult and at the moment there is no guaranteed method for it to work. 

here's a method by custom kernel compiling: [http://ubuntuforums.org/showthread.php?t=2115317]("http://ubuntuforums.org/showthread.php?t=2115317")
here's another method i did not have success with. [http://ubuntuforums.org/showthread.php?t=2157775]("http://ubuntuforums.org/showthread.php?t=2157775")

you can find some general directions to triple boot here: [https://wiki.archlinux.org/index.php/MacBook#Mac_OS_X.2C_Windows_XP.2C_and_Arch_Linux_triple_boot](https://wiki.archlinux.org/index.php/MacBook#Mac_OS_X.2C_Windows_XP.2C_and_Arch_Linux_triple_boot)

i highly recommend you make a backup disk image of your macs drive so you can simply go back if you mess things up. you can do this from disk utility. 

i've personally used refind, its works perfectly although it's a little annoying to have an extra bootscreen.

---

### Post by DurpnHard on 2013-08-27
So you're suggesting to use a custom bootloader such as rEFInd instead? If I use rEFInd does that increase the probability of having a successful triple boot? 

Also thanks for the backup suggestion, I swapped out my hard drive for a larger one so I am working with a brand new mtn lion install at the moment.

Any other tips?

---

### Post by SilverOne on 2013-08-27
> **DurpnHard said:**
> So you're suggesting to use a custom bootloader such as rEFInd instead? If I use rEFInd does that increase the probability of having a successful triple boot? 


Yes, you will not run into any bugs with refind. it works. 

> 
Also thanks for the backup suggestion, I swapped out my hard drive for a larger one so I am working with a brand new mtn lion install at the moment.


still, might save you time.

> 
Any other tips?


Unfortunately , no. I have the same macbook you do, and my only issue is gpu switching. 

also, a slight annoyance is the speaker system. apple uses some sort of weird config where the left speaker is actually a sub woofer - sounds kinda dull and low under linux.

---

