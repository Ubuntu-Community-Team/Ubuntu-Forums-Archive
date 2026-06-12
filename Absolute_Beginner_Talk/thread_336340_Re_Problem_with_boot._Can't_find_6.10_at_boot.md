---
title: "Re: Problem with boot. Can't find 6.10 at boot?"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by kojack3175 on 2007-01-11
Hey
 First of let me say hello and to say thankyou to the people behind this OS, it is gona change my computing life big time. So long Bill and company. 
 My problem lies with boot. I did a clean install of Edgy 6.10 desktop on a 160GBWD HD.
Did the partion for root and left about 10GB for swamp file and the os did its thing and installed onto my system without much hassel, got to the end and was asked to reboot and remove cd. Wnen my system boots up it can't find the os, i've gone back into bios and reset it to boot from my hd but when it gets past post it can't find the os and bios askes me for a bootable disk etc etc. Where have i gone wrong and how can i correct this as im dying to get to grips with this os.

---

### Post by goodfella on 2007-01-11
You can try to boot again from the live cd and reinstall grub.  I had a similar problem myself and this solved it.  Here is my forum post which explains briefly how to do it.

[grub install from live cd]("http://www.ubuntuforums.org/showthread.php?t=334149")

---

### Post by AbeJarano on 2007-01-11
Hi Kojack3175,

 I would really recommend you allow the partitioning system in the installer to use it's defaults.  For example, 10Gb is excessive for a swap partition.  Less than 1 GB is better.  I installed Kubuntu 6.06 lately and it made two swap partitions under 1Gb, letting it use defaults and just telling it what partition to put the system on.
As to your questions, the boot loader (Grub) might not be installed.  Or it might have installed in hda, or your first IDE master.  That's the default install location.
 
Good luck,
Anthony

---

### Post by kojack3175 on 2007-01-11
Man oh Man, I hate to come back with the same issue but im damed if i can get Edgy 6.10 to boot after a clean install. I only have one ide on my master controller its not a dual boot and i've tried sooo many varations of installs and still i need the cd to start the os. I have also used super grub disk and that keeps telling me that is having no joy! between trying to get the inital iso to work and install and trying to get the os to boot of its own accord i've spent the whole day at it but still haven not lost my temper yet as i like the look of this os and really want to have some fun with it. Needless to say ill be farily expert at installing it yet with many more fun filled days ahead ;->
 Ps I'm so new to the World of Linux its unreal but its by far the most fun im gona have for a while to come

---

