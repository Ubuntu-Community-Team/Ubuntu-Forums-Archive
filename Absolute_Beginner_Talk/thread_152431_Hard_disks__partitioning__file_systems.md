---
title: "Hard disks / partitioning / file systems"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by TheDevil on 2006-03-29
Hi all, 

just wondering,

i wish to dual boot on my machine, i've got currently got a hard disk that's totally used up by win 2k and xp. i really don't want to fiddle around configuring the current system. 

is there a way to install ubuntu on a new slave hard disk? does the installation boot auto detect the unallocated hd?

and also please if you guys and gals have any links to resources dealing with partitioning / hdas concerning linux etc i'd really appreciate it.

cheers

thedevil :twisted:

---

### Post by pietro_spina on 2006-03-29
I took my windows HD made it a slave and have been dual booting ever since... I'll post my widows grub entry in a second if iI can find it...

---

### Post by jgoguen on 2006-03-29
[quote=TheDevil]is there a way to install ubuntu on a new slave hard disk? does the installation boot auto detect the unallocated hd?[/quote]
So you have one drive with Win2k/WinXP on it, and a second drive with nothing?  Yes, Ubuntu will pick up the unallocated disk.  You can even tell Ubuntu to automatically partition using only that disk.  GRUB (your default bootloader) will also pick up your existing Windows installations, so you can access all systems with nothing special done by you.

> and also please if you guys and gals have any links to resources dealing with partitioning / hdas concerning linux etc i'd really appreciate it.
I recommend using ReiserFS.  It probably doesn't make any difference for you...it's just a preference of mine for performance reasons :)

---

### Post by pietro_spina on 2006-03-29
[QUOTE=pietro_spina]I took my windows HD made it a slave and have been dual booting ever since... I'll post my widows grub entry in a second if iI can find it...[/QUOTE]

and my grub entry is...
```
title Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
chainloader +1
boot
```

this is with windows 2000 installed on a HD that was previously set as "master" for the installation and then switched to being slave while I installed various linux distros on my new HD...

that's my experience for what it is worth... it works for me...

-p

---

### Post by belikralj on 2006-03-29
You can have Ubuntu on the slave drive but you must install GRUB the Ubuntu boot loader if you want all three systems to boot. Ubuntu should automatically detect on install but even if it doesn't if you know what partitions you have your windows on you can do this manually. And if everything goes to pieces you can still recover Windows with the windows boot disk using "fdisk /mbr" but you most certainly will not have to do this because 99.999999999% of people have perfect Ubuntu installs. So you will most likely never have to resort to that sort of thing, but if you do it's nice to know there are several ways out of an UNLIKELY bad situation.

Once you set up Ubuntu come back and we can halp you tweak your boot.

---

### Post by TheDevil on 2006-03-30
Thankyou all for generous replies. they were all very helpful. (surprised cause i wasn't expecting much!).

can you ubu guys and buntu gals point me to a direction where i can find information about everything i need to know concerning disks, partitions, swap files etc? 

i don't quite understand what hda1, hda0 and all that means. my puppy linux seemed to boot run live from cd and "copy" "home" files to my harddisk during the installation i was given the chance to "mount" to dev/hdb1

what on earth does that mean?

by the way i can't wait for my 5 FREE CDs!!! i ordered them about 2 weeks ago.

cheers all

---

### Post by pietro_spina on 2006-03-30
[QUOTE=TheDevil]
can you ubu guys and buntu gals point me to a direction where i can find information about everything i need to know concerning disks, partitions, swap files etc? 
[/QUOTE]
I'm having a little trouble finding what I would call a clear and concise explanantion... Someone else might have a nice link in their back pocket though. However, you ought to know what the terms primary/secondary master/slave and how it relates to your hardware... 

enjoy your Ubuntu..
-p

---

### Post by NetMatrix on 2006-03-30
You can download Knoppix, burn it to a CD (It's a live distro) and resize the windows partition.  Be sure to defrag your windows partition first to be sure that you don't lose any data.  I think this is a complete set of instructions.

[URL="http://users.tkk.fi/~tkarvine/linux-windows-dual-boot-resizing-ntfs.html"]
http://users.tkk.fi/~tkarvine/linux-windows-dual-boot-resizing-ntfs.html[/URL]

I did it to a company laptop and it worked quite well.  Good Luck.

---

