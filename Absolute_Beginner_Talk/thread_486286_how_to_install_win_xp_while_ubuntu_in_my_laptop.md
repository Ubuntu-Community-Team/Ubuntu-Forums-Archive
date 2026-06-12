---
title: "how to install win xp while ubuntu in my laptop??"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by nooor7772000 on 2007-06-27
hi

i want to have win xp beside ubunt in my laptop 
i install ubuntu in all 80 gb harddisk...............

how to install xp in a partion for example 20 gb....with ubuntu.............please in details???

---

### Post by overdrank on 2007-06-27
> **nooor7772000 said:**
> hi

i want to have win xp beside ubunt in my laptop 
i install ubuntu in all 80 gb harddisk...............

how to install xp in a partion for example 20 gb....with ubuntu.............please in details???

Hi you can use gparted on the live cd and resize your ubuntu partition and then install xp then reinstall the grub using this thread
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
:(

---

### Post by FleetAdmiral74 on 2007-06-27
Boot up using a LiveCD and use gParted to resize the ubuntu partition. From there you will need to install xp, and then edit GRUB to boot into ubuntu again. Search for the details, people have asked this before.

---

### Post by nooor7772000 on 2007-06-27
thanks so so much guys,,,but is there any advice not to loss any data from my laptop while doing that...i mean can i do that safely?

---

### Post by overdrank on 2007-06-27
> **nooor7772000 said:**
> thanks so so much guys,,,but is there any advice not to loss any data from my laptop while doing that...i mean can i do that safely?

If you if you are installing xp I would back up any data I would like to keep but just reinstalling grub I think you are ok. :P

---

### Post by nooor7772000 on 2007-06-29
> **overdrank said:**
> If you if you are installing xp I would back up any data I would like to keep but just reinstalling grub I think you are ok. :P

sorry i did not understand,,,

---

### Post by overdrank on 2007-06-29
> **nooor7772000 said:**
> sorry i did not understand,,,

I would agree after reading that even confused me!:KS

---

### Post by hyper_ch on 2007-06-29
Whenever you alter your partitions make a BACKUP.

---

### Post by Topfs on 2007-06-29
Well I don't really understand, Have you already ubuntu and want to install XP on the laptop or do you have XP and want to install ubuntu.
If you have XP then just restart the laptop and boot the livecd and choose to resize the partition when asked in the installation process, think it's step 4 of 7
And you should be good to go.

if you have Ubuntu and want to install XP, then search the forum because this I haven't done :)

---

### Post by nooor7772000 on 2007-06-29
ok i have ubuntu in my laptop installed in my 80 gb harddisk as one partion...

i use live cd to get a partion free of 20 gb size by gparted but...when i open it and mount it to resize it it say error ,,,,,,,,,,,

how can i get 20 gb free partion for xp installintion...............


[SIZE="7"]help me guys as u can.....................??[/SIZE]

---

### Post by eddieb on 2007-06-29
Please be aware, any Windows O/S (operating system) MUST be on the first partition of the first hard drive. If you have any other O/S on that partition then Windows will always overwrite it. So if you have Linux on it , you will lose it. I think this could be made into a sticky???

---

### Post by bcom on 2007-06-29
You could install VMWare server and then run Windows XP in a virtual machine.

This has the advantage of not having to deal with re-partitioning your hard drive.

---

### Post by nooor7772000 on 2007-07-01
[SIZE="6"]congratulation guys.............[/SIZE]

[SIZE="4"]i did it,,,,,,,,,,,,,,,i install xp ..........after use live cd gparted................and now with ubuntu,,,,,,,

but still need the cd to shift booting from ubuntu to xp..........

is there any way to install that boot from gparted live cd to switch between both at start up boot....

thanks[/SIZE]

---

### Post by buuntuu! on 2007-07-01
congratulations!
if i understand things right, you installed ubuntu first and xp later, is that correct?
(sorry, but the whole thread seems quite confusing so far)
in this case you would have to follow [these instructions]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub") to reinstall grub, because your xp-install would have overwritten it.
good luck

---

### Post by nooor7772000 on 2007-07-01
thanks alot dear...i will look this and it seem big text but i will get off away from medicaal study some and read it ,,,,,,,,,,,hope get small text simple than this to save time for surgery,,:o

---

### Post by jabeamer on 2007-08-10
I need to reinstall my xp with Ubuntu already installed.  If I reinstall the grub will it lose my old kernals for Ubuntu.  Because I can't use the new Kernals (16 and up) with my wireless nic.  I have to use the old one.  I think its 15.

---

### Post by Jonnothin on 2007-08-10
Just a quick side note and don't quote me on this cause I'm not sure. I've heard that if you install Ubuntu and then XP it can cause you to have some problems so just be aware of this.

What kind of problems I'm not sure, but I've heard that you should install windows first then your linux OS.

PS: someone please correct me if I'm wrong.

---

### Post by overdrank on 2007-08-10
> **Jonnothin said:**
> Just a quick side note and don't quote me on this cause I'm not sure. I've heard that if you install Ubuntu and then XP it can cause you to have some problems so just be aware of this.

What kind of problems I'm not sure, but I've heard that you should install windows first then your linux OS.

PS: someone please correct me if I'm wrong.

Hi the only problem I am aware of is the grub. If you reinstall the grub with the live cd you still should have all your kernel updates if not you can correct the through synaptic. There you can add the kernel needed for your wireless. Good luck! :popcorn:

---

### Post by stinger30au on 2007-08-10
get as copy of win4lin pro

[http://www.win4lin.com/](http://www.win4lin.com/)

---

