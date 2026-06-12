---
title: "new to ubuntu"
date: 2005-07-14
forum: Absolute Beginner Talk
---

### Post by JamesW on 2005-07-14
I got a ubuntu disk from a bud. I no nothing about ubuntu.
I now run windows xp. Can i install ubuntu on the same hard 
drive without hurting xp so that I continue to use xp until I learn
how to use ubuntu? If so, then how?

---

### Post by AntiDragon on 2005-07-14
Quick answer: Yes!  :razz: 

Longer answer: How easy it is depends on your current setup. You will need to dedicate some of your existing disk space to Ubuntu. You will need to re-size your Windows partition to do this. 

Best answer: Use the forum search feature for "dual boot". This question gets asked all the time and there's a wealth of information out there.

My preferred answer:  As long as your comfortable with it, fit a second harddrive and install Ubuntu to that. You can leave your Windows install untouched then. (Yeah, that's what I did...hehe..)

---

### Post by Kvark on 2005-07-14
As always, backup your files before doing anything major (such as editing partitions).

---

### Post by AntiDragon on 2005-07-14
What he ^^^^ said!  :grin: 

If you do opt for a second HDD and dual boot with that, you need to know which harddrive is first in your boot sequence. Ubuntu uses a program call Grub to handle the startup of your Operating System. You'll be using this to choose wether to boot into Ubuntu or Windows.  However, to keep you windows system "clean", you will want to have your Ubuntu disk as the first harddrive (primary master, as it's listed in you PCs BIOS). But Windows complains if it realises it's not the first disk, so you need to configure Grub into making Windows believe it's on the first disk when it boots.

A lot of technical jargon, I know (I don't know how experienced you may be :) ) - but feel free to ask more questions as needed!

---

### Post by JamesW on 2005-07-14
[QUOTE=AntiDragon]What he ^^^^ said!  :grin: 

If you do opt for a second HDD and dual boot with that, you need to know which harddrive is first in your boot sequence. Ubuntu uses a program call Grub to handle the startup of your Operating System. You'll be using this to choose wether to boot into Ubuntu or Windows.  However, to keep you windows system "clean", you will want to have your Ubuntu disk as the first harddrive (primary master, as it's listed in you PCs BIOS). But Windows complains if it realises it's not the first disk, so you need to configure Grub into making Windows believe it's on the first disk when it boots.

A lot of technical jargon, I know (I don't know how experienced you may be :) ) - but feel free to ask more questions as needed![/QUOTE]
 What is easier, spliting one hdd & installing on that, or puting a 2nd hdd & installing on that?

---

### Post by AntiDragon on 2005-07-14
That mostly depends on your expertise. 

Fitting a second HDD and using that is *safer* as you will avoid fiddling around with your existing Windows drive. If it all goes wrong, you still have windows.

But (there's always one) you need to know how to safely fit an additional drive. It's not too complicated but there's always the danger of causing damage if you don't know what you're doing.

The alternative (Squeezing a new partition or two onto your existing drive) will avoid fiddling with your computer hardware. But you will need software to resize you Windows partition. And if that goes wrong you'll lose it.

So, first - backup! Burn your important files to CD, make sure you have a record of any licence keys for Windows software and you have the CDs for it as well. That part is common sense though - I'd advise you do that regularly or before installing a WIndows Service Pack as well :)

Then, if you are comfortable, I'd go for the 2nd HDD option. Yes, it means buying another drive but it makes things a lot safer and easier. Plus you won't be sacrificing your Windows disk space. 

However, if you have no idea about fitting drives (or a don't have a friend who does) then the resize option is the way to go.

---

### Post by aysiu on 2005-07-14
[QUOTE=JamesW]What is easier, spliting one hdd & installing on that, or puting a 2nd hdd & installing on that?[/QUOTE] It depends what you call easier. In a theoretical sense, using a second hard drive is easier because you don't have to partition things. I have read a lot posts about people having difficulty with second hard drives and master boot records.

If you get a good graphical partitioner (QTParted, for example; my personal favorite is DiskDrake), partitioning and resizing isn't such a big deal. Just remember to back up all your files!

---

### Post by JamesW on 2005-07-14
[QUOTE=AntiDragon]That mostly depends on your expertise. 

Fitting a second HDD and using that is *safer* as you will avoid fiddling around with your existing Windows drive. If it all goes wrong, you still have windows.

But (there's always one) you need to know how to safely fit an additional drive. It's not too complicated but there's always the danger of causing damage if you don't know what you're doing.

The alternative (Squeezing a new partition or two onto your existing drive) will avoid fiddling with your computer hardware. But you will need software to resize you Windows partition. And if that goes wrong you'll lose it.

So, first - backup! Burn your important files to CD, make sure you have a record of any licence keys for Windows software and you have the CDs for it as well. That part is common sense though - I'd advise you do that regularly or before installing a WIndows Service Pack as well :)

Then, if you are comfortable, I'd go for the 2nd HDD option. Yes, it means buying another drive but it makes things a lot safer and easier. Plus you won't be sacrificing your Windows disk space. 

However, if you have no idea about fitting drives (or a don't have a friend who does) then the resize option is the way to go.[/QUOTE]
 Thanks, I have friends who can help install new hardware (hdd).
Also, where can I get this " offical install manual"?

---

### Post by AntiDragon on 2005-07-14
[QUOTE=aysiu]It depends what you call easier. In a theoretical sense, using a second hard drive is easier because you don't have to partition things. I have read a lot posts about people having difficulty with second hard drives and master boot records.

If you get a good graphical partitioner (QTParted, for example; my personal favorite is DiskDrake), partitioning and resizing isn't such a big deal. Just remember to back up all your files![/QUOTE]

Yes. Although getting dual-boot to work properly is not just limited to multi-drive systems.

Now, this isn't a recommendation, but what I did is make my new drive the **primary** (first in the boot sequence) and installed to that. Infact I temporarily disconnected my Windows drive before installing (Hey, I'm allowed to be paranoid!). After booting and making sure Ubuntu was running, I re-attached my drive. I thyen had to add and entry to Grub's config file to enable Dual booting for Windows. In adition I had to "alias" the drives for the Windows boot to make Windows believe it was on the **primary** drive.

It's not a walk in the park, but it made sure Grub never touched my Windows drive.  The biggest problem with dual boot on two drives was the whole "Windows must be installed on the first Hard Drive" stuff, which is resolved thanks to Grub's ability to er...lie...to the OS it's booting.  :grin:

---

### Post by poofyhairguy on 2005-07-14
[QUOTE=JamesW]What is easier, spliting one hdd & installing on that, or puting a 2nd hdd & installing on that?[/QUOTE]

Its easier to add a second hard drive. The biggest problem would be if you accepted the default partitioning option of the Ubuntu installer. By default, it will install to the primary drive (the one with XP) so you have to tell the installer to use the secondary drive.

This article helps a bunch:

[http://www.tipmonkies.com/2005/06/23/linux-filesystems-and-partitioning-a-primer/](http://www.tipmonkies.com/2005/06/23/linux-filesystems-and-partitioning-a-primer/)

---

### Post by UbuWu on 2005-07-14
[QUOTE=JamesW]Thanks, I have friends who can help install new hardware (hdd).
Also, where can I get this " offical install manual"?[/QUOTE]

There is no official installation manual, but this page comes close to what it should be:
[http://www.mrbass.org/linux/ubuntu/install/](http://www.mrbass.org/linux/ubuntu/install/)

---

### Post by Ken.Lank on 2005-07-14
Also, if you just want to play around with ubuntu rather than install it you could also play with the LIVE cd.

As people said, if you can install a 2nd HD then that gives you the free space to install without having to mess around with your partition sizes.  Also, if you want to force yourself to try ubuntu, you could always pull your windows drive and install the new drive and ubuntu.  If you don't like it, then you can just swap the drives back and no harm done.

---

### Post by poofyhairguy on 2005-07-14
[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

---

