---
title: "GRUB error code 18"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by delb2k on 2007-02-02
Hi there, i`ve recently tried to install the latest version of the ubuntu live cd (ver. 6.10) on my old PC after building the new one.  I managed to go through the whole installation fine but when it attempted to load off the install it stated GRUB error code 18.

Does anyone know what this means and how to get around the issue? Be aware this is my first  attempt at unix so i might not get all the shortcut commands.

System spec is 

800MHz AMD CPU
ATi Radeon Graphics card
512 MB RAM

Thanks everyone

---

### Post by quirks on 2007-02-02
This could help:
[http://ubuntuforums.org/archive/index.php/t-77042.html](http://ubuntuforums.org/archive/index.php/t-77042.html)

Or an update for your BIOS.

quirks

---

### Post by saxofoner on 2007-02-02
Also try attaching the cable on your hard drive tighter if this is your build.

---

### Post by delb2k on 2007-02-03
I believe the error stems from the fact i was trying to install onto a 160gig hard drive which put the boot area on the outer edges of the disc which meant that it could not load the boot part. OK i thought, instead i`ll set up a small 20 gig partition for the boot and the rest on a second partition. Now i get a error code 17 which usually means a errored partition. I need a place that will detail a step by step installation method from the live cd as right now i`m getting nowhere. Can anyone help?

---

### Post by lieobry on 2007-02-04
I have exactly the same problem!!!!!

Can anybody give some help....

---

### Post by rumli on 2007-02-14
Try selecting the recovery mode option in the GRUB menu and then if you can successfully boot, try commenting out the "savedefault" lines in your /boot/grub/menu.lst

More details at [http://ubuntuforums.org/showpost.php?p=2156493&postcount=3]("http://ubuntuforums.org/showpost.php?p=2156493&postcount=3").

---

### Post by w00dchaz on 2007-02-14
I was getting that too (plus a few other boot error messages), after several days of the system working. Then randomly it would work again, then sometimes not. A techie friend of mine finally decided the BIOS was messed up in some way, in addition to being outdated. Or else something's wrong with the motherboard. Anyway, I'm getting a new motherboard, processor, etc., and starting over.

---

### Post by Patrick K on 2007-02-14
When I got error 17, it turned out grub was pointing to the wrong partition (after the recent upgrade, my partitions were renamed). I booted to the livecd and ran GNOME Partition Editor (GParted) (System>Administration). From it I was able to get the new partition names. I rebooted and when grub came up I selected the new kernel and pressed "e" to edit the commands. I changed the partition grub was looking for to the correct one and hit "b" to boot. Once in Ubuntu, I edited /boot/grub/menu.lst so it had the correct partitions. 

IMPORTANT: Don't forget that hda1 (Linux speak) is hd0,0 (BIOS speak) when editing. They are the same drive and partition (the numerals are one lower in BIOS speak). Both are in menu.lst, I don't recall if they are in Grub's editable menu at boot. 

I also had to edit fstab due to these changes but that may not be an issue for you.

---

