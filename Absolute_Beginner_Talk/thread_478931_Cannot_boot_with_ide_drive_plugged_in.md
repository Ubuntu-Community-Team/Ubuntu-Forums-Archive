---
title: "Cannot boot with ide drive plugged in"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by ps6000 on 2007-06-19
I have had problems with this in the past.

Ubuntu works like a dream when I have my two Sata Drives plugged in into 1 and 3 on my motherboard. But when I plug my ide HD with windows installed and reboot I get error 17 or 21.

I remember installing ubuntu with the three hard drives but I couldn't get it to work without unplugging my ide drive. This was fine as I wanted to stay away from windows, But now I need to boot that windows install.

What does GRUB do when I plug in an ide drive?
When i plug in an ide drive should the location of root be changed in my menu.lst?

Thanks. 


title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=71a11b38-435c-4155-a314-6688dcaad4cf ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

---

### Post by sdrawkcab on 2007-06-19
I'm a new guy, but do you boot from that IDE drive at all? 'Cause if you do, it could be a problem with your boot order or something. Just a thought.

---

### Post by jusmurph on 2007-06-19
Yeah, first thing you want to do is check your boot order in your bios.

Post back with your motherboard brand if you do not know how to enter the bios.

---

### Post by ps6000 on 2007-06-19
I should try and explain myself.
Ubuntu is installed on the sata drive and can boot fine from that.
But when the ide is attached I can't
I have an asus mobo but I think this problem is isolated to GRUB and how it handles drives.
I was hoping that the ide would be recognized as "just another drive" but I fear that when an IDE is plugged in GRUB changes the HD#'s.

---

### Post by confused57 on 2007-06-19
> **ps6000 said:**
> I should try and explain myself.
Ubuntu is installed on the sata drive and can boot fine from that.
But when the ide is attached I can't
I have an asus mobo but I think this problem is isolated to GRUB and how it handles drives.
I was hoping that the ide would be recognized as "just another drive" but I fear that when an IDE is plugged in GRUB changes the HD#'s.
It might be that when an IDE drive is connected, your bios automatically designates it as the first hard drive in the boot sequence.  When this happens, your SATA drive with Ubuntu would be hd1...it's not really grub's fault, because if you're able to set your SATA drive as the first hard drive booted in bios, then it would still be hd0 and boot without any problems.

If you're not able to set the SATA drive first in the hard drive boot sequence, your only other alternative might be to install grub to the IDE drive's mbr...you'd have to modify your menu.lst and add an entry to boot Windows.

You might want to burn a copy of the Super Grub Disk, in case of problems:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

I could be wrong, but I think this might be what's happening with your IDE drive connected.

---

### Post by ps6000 on 2007-06-20
That makes sense... I would still like to blame GRUB though.

How would I go about installing grub to the MBR on the IDE drive?

---

### Post by ps6000 on 2007-06-20
Oh and thanks for the link to the super grub disk!

---

### Post by DoricMan on 2007-06-20
I found I could not install my Dual Boot Ubuntu 7.04 and XP Home configuration until removed two old IDE hard disks. These contained Win 98SE and files I wished to keep. They were not essential to the Dual Boot and I can always access anything on an external HD Caddy. The 3 remaining serial 200GB hard disks work as I intended.
It seems that Feisty Fawn does not like IDE hard disks. Has any one experienced this? :D

---

### Post by ps6000 on 2007-06-20
I have installed feisty on plenty of ide "driven" computers without a problem. 
But I have had this problem before on a computer with both ide and sata when you install the os on the sata.

---

### Post by confused57 on 2007-06-20
> **ps6000 said:**
> I have installed feisty on plenty of ide "driven" computers without a problem. 
But I have had this problem before on a computer with both ide and sata when you install the os on the sata.

Have you tried the Super Grub Disk to boot your Ubuntu drive?  Make sure to burn a copy before you try anything else.

Here's how to install grub, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
I'm not sure if this will work, since your menu.lst probably already shows (hd0) for the SATA drive...but you can try.

I'm hesitate to suggest much else...don't want to make your Ubuntu unbootable.

You might want to boot the live cd with all 3 drives connected and post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

If installing grub with the live cd doesn't work, you could probably mount your Ubuntu partition and run:
```
sudo grub-install /dev/hda
```
don't do this yet, I'm just throwing out ideas for you to consider.

---

### Post by ps6000 on 2007-06-20
I had no idea about the grub boot disk until you mentioned it.
I d/l and burned a copy and will try as soon as I get home.

Actually the sata drive is hd1,0

I posted part of the menu.lst

---

### Post by confused57 on 2007-06-20
> **ps6000 said:**
> I had no idea about the grub boot disk until you mentioned it.
I d/l and burned a copy and will try as soon as I get home.

Actually the sata drive is hd1,0

I posted part of the menu.lst

Installing grub with the live cd to (hd0) might work, if your IDE drive is recognized as hd0...if you can, you might set your bios hard drive boot order to: IDE, Ubuntu SATA drive, then the other SATA drive.
If grub is actually installed to the IDE mbr, then Ubuntu "should" still boot, since the menu.lst root is (hd1,0).
You would need to add an entry to boot Windows:
```
title  Windows XP
root  (hd0,0)
savedefault 
makeactive
chainloader +1
```

You should burn a copy of SGD before attempting to reinstall grub, if that's what you decide on...see if SGD can boot your Windows and Ubuntu drive.

I saw your menu.lst entry, somehow I assumed that was how you thought your menu.lst should look, not the actual entry...another bad assumption was that you were booting first to your Ubuntu SATA drive, making it hd0...that's what I get for assuming.

---

### Post by ps6000 on 2007-06-20
!!! SUCCESS !!!

I am now able to boot ubuntu with that IDE drive plugged in.

I reinstalled grub and now

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=71a11b38-435c-4155-a314-6688dcaad4cf ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

Boots fine!!!

What I cannot do is boot windows using any number of commands.
I can boot windows when I use the super grub boot disk, but when I try to use the same option in my menu.lst it does not work. I get an error that says unsupported executable format. Any thoughts?

The super grub boot disk option I use is with (hd2,0)

---

### Post by confused57 on 2007-06-20
Try this Window's entry:
```
title  Windows XP
root   (hd2,0)
savedefault
makeactive
map   (hd0) (hd2)
map   (hd2) (hd0)
chainloader +1
```

This "should" work...

---

