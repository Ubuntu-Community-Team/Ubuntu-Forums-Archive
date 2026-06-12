---
title: "DamnSmallLinux on 64mb intern HDD"
date: 2012-02-04
forum: Any Other OS
---

### Post by Pastortom on 2012-02-04
First of, I realize this is the wrong forum for this. So I apoligize in advance. 

Second, I write here since any DSL forums Ive come across are dead. So this is the only place I know of that maybe can help :)

Ive got this T5530 Thin Client pc here with very weak hardware.

[IMG]http://www.norsystems.net/img/hpThinT5530_front.jpg[/IMG]


800mhz cpu, 128mb ram and 64 hdd intern ATA flash chip.

Running DSL from USB without problem. Everything works fine. But when I try to install to the internal 64mb hdd, I get problems.

When Im using cfdisk to configure hda1 and hda2 (swap and linux OS partition) and try to start the hddinstall it fails since it asks for 200mb in swap. 

Now, since Damn Small Linux only takes 50mb, and my pc got 64mb hdd, shouldnt it work to use 14mb for swap and 50mb as OS partition?

I just want this Thin Client to boot DSL from within its hdd, instead of using a USB flash stick.

I havent tried installing from a Live CD, which will be my last option. So far Ive only tried running it and installing it from my usb stick.

Any help is deeply appreciated :) 

PS! If ubuntu works better on this system, instead of DSL, Im open for this as well.

---

### Post by nothingspecial on 2012-02-04
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by Lars Noodén on 2012-02-04
64MB is likely too small for anything you're going to find nowadays.  Even [Puppy Linux](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm) is now around 100MB.  If you could put in a second drive or even a USB stick, then you could use the 64MB as the /boot partition.

---

### Post by Pastortom on 2012-02-04
> **Lars Noodén said:**
> 64MB is likely too small for anything you're going to find nowadays.  Even [Puppy Linux](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm) is now around 100MB.  If you could put in a second drive or even a USB stick, then you could use the 64MB as the /boot partition.

Well, Damn Small Linux runs on 50mb, doesnt it? Cant I install that on the 64mb HDD of my T5530?

---

### Post by Lars Noodén on 2012-02-04
The last release of DSL appears to be back in 2008:

[http://distrowatch.com/table.php?distribution=damnsmall](http://distrowatch.com/table.php?distribution=damnsmall)

While DSL may install, there will be patches, especially security patches, that will be missing unless you are up to doing them by hand. 

I've not tried Tiny Core, but it claims to be even smaller:

[http://distro.ibiblio.org/tinycorelinux/welcome.html](http://distro.ibiblio.org/tinycorelinux/welcome.html)

Digging around, I found a review of some of the other small ones:

[http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552](http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552)

---

### Post by Pastortom on 2012-02-04
> **Lars Noodén said:**
> The last release of DSL appears to be back in 2008:

[http://distrowatch.com/table.php?distribution=damnsmall](http://distrowatch.com/table.php?distribution=damnsmall)

While DSL may install, there will be patches, especially security patches, that will be missing unless you are up to doing them by hand. 

I've not tried Tiny Core, but it claims to be even smaller:

[http://distro.ibiblio.org/tinycorelinux/welcome.html](http://distro.ibiblio.org/tinycorelinux/welcome.html)

Digging around, I found a review of some of the other small ones:

[http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552](http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552)


Thanks for your feedback.

But I think my problem can be easily solved by someone who has some skills with bootup/linux HDD installation-aspects.

a) The guides Ive followed says DSL requires 200mb for Swap hdd (hda1) I can only spare 14mb.
b) DSL supposedly only needs 50mb to run, seeing as my internal HDD has 64mb it should work. Right?
c) When I set hdb1 with 50mb as boot (type 83) and hda1 with 14mb as swap (type 82), and try to install, it fails due to writing to hda1 above 14mb.

Now, I could "solve" my issue, by just buying a 2gb flash stick with high write/read speed, and just let it run from that (this machine got like 6 usb ports and 2 hidden usb ports, I can easily fit a usb stick in one of the hidden ones and boot DSL from there).

But Id rather see DSL run without any usb sticks. Plain from internal flash 64mb ATA chip.

If someone could write some steps on how I can accomplish this, Id be forever thankfull!

---

### Post by kerry_s on 2012-02-04
+1 for tiny core
dsl has been dead since the move to tiny core, same developer by the way.

i don't think you can put 50mb in 64mb, you need that 50mb + space to run, for example /tmp is created on each run, as well as /mnt & others.

Tiny core is only 12mb for the GUI version, you'll have plenty of room to run, plus that project is very active & you can get plenty of help there straight from the developer.

---

### Post by Pastortom on 2012-02-04
> **kerry_s said:**
> +1 for tiny core
dsl has been dead since the move to tiny core, same developer by the way.

i don't think you can put 50mb in 64mb, you need that 50mb + space to run, for example /tmp is created on each run, as well as /mnt & others.

Tiny core is only 12mb for the GUI version, you'll have plenty of room to run, plus that project is very active & you can get plenty of help there straight from the developer.


Really? :D Do you know how to install it from USB stick? That's so great, I will go check it out! Thank you so much!

---

### Post by mörgæs on 2012-02-04
Are you sure that it pays to struggle with such old hardware at all?

Let's say that you get Tiny Core running (as others have already said, DSL is a no-no). After that, have you imagined  how slow this computer will be for normal tasks like surfing the web and  viewing Flash? Editing a picture in Gimp? 

Used hardware is so cheap that you are better off finding something else. 


I am not trying to be negative here; just to avoid that you are wasting your time.

---

### Post by mips on 2012-02-04
I would suggest,

1. Upgrade the Compact Flash card inside the unit to bigger one. 2GB-4GB should be pretty cheap, you might even have some lying around.

2. Removed the CF card and adapter inside the unit and plug a 2.5" 44-pin PATA hard drive into the unit. You also might have one of these lying around

---

### Post by Pastortom on 2012-02-04
> **mips said:**
> I would suggest,

1. Upgrade the Compact Flash card inside the unit to bigger one. 2GB-4GB should be pretty cheap, you might even have some lying around.

2. Removed the CF card and adapter inside the unit and plug a 2.5" 44-pin PATA hard drive into the unit. You also might have one of these lying around


There's no CF card inside this actually. None that I can see anyways, had it open since I got it.

But I do see a blue PCB adapter with 3 lean "ram-size" sockets with no chip in them. Its the size of half a creditcard.

---

### Post by kerry_s on 2012-02-05
most thin clients are very limited as far as upgrades, I've seen some with just a single board with everything soldered on.
if you have to you can run swap on a flash drive, i used a 256mb flash drive as swap on a old rig that only had 128mb ram, ran it like that for over a year. makes it very much more usable.

some times they hide stuff, like ram & cf card on the under side of the board, you can't access it with out pulling the board. just a thought.

---

### Post by kerry_s on 2012-02-05
i think your going to have to run from USB, the OS it comes with is a ROM, which means you'd have to flash it with a new ROM, you can't just install on it.
so maybe 1 USB for the OS & 1 for swap, it will run better if there not on the same device.

on the up side, they do got a few goodies on there site for windows ce, that media player 9 would be handy, not to sure about the ie6, the vnc server could be useful.

---

### Post by mips on 2012-02-05
> **Pastortom said:**
> There's no CF card inside this actually. None that I can see anyways, had it open since I got it.

But I do see a blue PCB adapter with 3 lean "ram-size" sockets with no chip in them. Its the size of half a creditcard.

Can you post a pictures of the inside please?
Also provide the exact model#/part# as per the label on the back/bottom.

I saw a pic of the insides of the same model with a 44-pin ide connector to which a CF adapter board was plugged into. Probably a different revision board.
[http://www.parkytowers.me.uk/thin/hp/t5530/index.shtml](http://www.parkytowers.me.uk/thin/hp/t5530/index.shtml)



.

---

### Post by Pastortom on 2012-02-05
> **mips said:**
> Can you post a pictures of the inside please?
Also provide the exact model#/part# as per the label on the back/bottom.

I saw a pic of the insides of the same model with a 44-pin ide connector to which a CF adapter board was plugged into. Probably a different revision board.
[http://www.parkytowers.me.uk/thin/hp/t5530/index.shtml](http://www.parkytowers.me.uk/thin/hp/t5530/index.shtml)



.

This is what I love about this forum, the intense knowledge and experience behind the users :D

You are absoluetely right, the board was perfectly covering the 44-pin ide slot, once removed I can throw this 64mb flash away and install a internal 2,5" hdd :D

---

### Post by Pastortom on 2012-02-05
> **mips said:**
> Can you post a pictures of the inside please?
Also provide the exact model#/part# as per the label on the back/bottom.

I saw a pic of the insides of the same model with a 44-pin ide connector to which a CF adapter board was plugged into. Probably a different revision board.
[http://www.parkytowers.me.uk/thin/hp/t5530/index.shtml](http://www.parkytowers.me.uk/thin/hp/t5530/index.shtml)



.

Think its possible to use 16GB Disk-on-Module upgrade for my T5530? 

[http://www.ebay.com/sch/i.html?_nkw=Disk+on+Module+16gb&_sacat=0&_odkw=Disk+on+Module&_osacat=0&_from=R40](http://www.ebay.com/sch/i.html?_nkw=Disk+on+Module+16gb&_sacat=0&_odkw=Disk+on+Module&_osacat=0&_from=R40)

---

### Post by mips on 2012-02-05
> **Pastortom said:**
> Think its possible to use 16GB Disk-on-Module upgrade for my T5530? 

[http://www.ebay.com/sch/i.html?_nkw=Disk+on+Module+16gb&_sacat=0&_odkw=Disk+on+Module&_osacat=0&_from=R40](http://www.ebay.com/sch/i.html?_nkw=Disk+on+Module+16gb&_sacat=0&_odkw=Disk+on+Module&_osacat=0&_from=R40)

No idea, dunno what (if any) size limitations there are. Should work though but you might only be able to format to a smaller size.
Don't you have some spare CF cards lying around?

---

### Post by Pastortom on 2012-02-07
> **mips said:**
> No idea, dunno what (if any) size limitations there are. Should work though but you might only be able to format to a smaller size.
Don't you have some spare CF cards lying around?

Only generic low size CF cards, like 8mb and 16mb. Havent had a CF card since the stone ages xD

But I do have a 44-pin ide cable from an old apple tv, and also got a bimodular 44-pin IDE to Sata adapter + an 2,5" 20gb sata harddrive. 

Think its possible to use the adapter with this Thin Client and format the 20gb for use as OS disk? I will try later today and come back to you.

---

### Post by mips on 2012-02-07
> **Pastortom said:**
> Only generic low size CF cards, like 8mb and 16mb. Havent had a CF card since the stone ages xD

But I do have a 44-pin ide cable from an old apple tv, and also got a bimodular **44-pin IDE to Sata adapter + an 2,5" 20gb sata harddrive**. 

**Think its possible to use the adapter with this Thin Client and format the 20gb for use as OS disk?** I will try later today and come back to you.

I can't see any reason why it would not work.

---

### Post by Pastortom on 2012-02-07
> **mips said:**
> I can't see any reason why it would not work.


Just connected an old 2,5" 10GB IDE drive to it with the cable from my apple tv. It worked like a charm, showing up as 10gb in Bios, BUT, it says "10 181 Flashable MB". Does this mean trouble when installing WinXP/Linux? 

When I tried to install Linux on the flash drive earlier it seemed to both manage partitioning, file system and copying files like a normal harddrive. So I hope it works now. I'll keep you updated.

---

### Post by Pastortom on 2012-02-07
[[IMG]http://img4.imageshack.us/img4/7204/003lqa.th.jpg[/IMG]](http://img4.imageshack.us/i/003lqa.jpg/)
[[IMG]http://img40.imageshack.us/img40/5199/004qvo.th.jpg[/IMG]](http://img40.imageshack.us/i/004qvo.jpg/)

It worked! :D 

Windows partitioned and copied files just fine, this must mean linux also will :)

This is so awesome <3

---

