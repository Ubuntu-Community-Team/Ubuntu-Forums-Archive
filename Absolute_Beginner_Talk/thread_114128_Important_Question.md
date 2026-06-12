---
title: "Important Question"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by Glass Casket on 2006-01-07
So I just finished trying to dual boot XP with Ubuntu. I set up my first linux partition as the primary and all other partitions logical. Then it asked me if I wanted to load the bootstrap loader in the MBR, I didnt know exactly what to do, so I checked yes.

Then when my system finished rebooting to finish the instalation, it goes straight to XP. So i'm now begining to think that I wasen't supposed to put the bootstrap loader in the MBR.

If that's what stopped me from dual booting, is there a way I can move the bootstrap loader? Or do I have to redo the whole instalation and pick not put the bootstrap loader in the MBR?

Thanks.

---

### Post by Glass Casket on 2006-01-07
So I tried it again, and when it's time to reboot, it simply loads Windows :(

---

### Post by Glass Casket on 2006-01-08
No one?

---

### Post by pbb on 2006-01-08
We need more information about the order in which you did things. Did you first install Ubuntu, and then installed XP?

You talk about your "first linux partition". Is this the first partition on your bootdisk, or is your first linux partition not your first harddisk partition?

Was it the Ubuntu setup, the XP setup, or another application that asked about loading the bootstrap in MBR?

---

### Post by Glass Casket on 2006-01-08
Here is my setup, I have three hardrives.

Drive #1: One partition with all my music in NTFS.
Drive #2: Windows XP with 5 partitions.
Drive #3: Trying to get Linux on it.

The bootloader was GRUB.

Also, when I was setting up al my partitions on the third disk, I put it as type '/' (root). But there was also an option to put it as type boot.

I set up XP first.

---

### Post by Nikusan on 2006-01-08
Maybe try changing your bios settings to boot from Drive #3. The installer might have put grub on that drive? I'm not sure though.

---

### Post by Glass Casket on 2006-01-08
[QUOTE=Nikusan]Maybe try changing your bios settings to boot from Drive #3. The installer might have put grub on that drive? I'm not sure though.[/QUOTE]

I've tried that, but the third drive dosen't show up in the boot priority list.

Like when it asks me if I want to put the bootstrap loader in the MBR, it shows that I have XP already installed and that I should pick yes so when the system boots, i'll see both operating systems.

Is there a tutorial on how to dual boot with two drives? I've Googled arround and can't seem to find something that would suit me.

Thanks.

Also, maybe it's because I didnt pick the right type of partitions. The first time I chose '/', then I chose '/boot'. After 5 re-installs, I chose the option that automatically partitions.

---

### Post by Glass Casket on 2006-01-08
So i've tried three more times and still nothing.

Any help would be greatly appreciated.

---

### Post by pbb on 2006-01-09
[QUOTE=Glass Casket]So i've tried three more times and still nothing.

Any help would be greatly appreciated.[/QUOTE]

It is the Ubuntu setup CD you are running every time? Or are you installing in another way?

And do you clear all the partitions on drive 3 every time your try, or not?

---

### Post by frodon on 2006-01-09
When you install XP after ubuntu it destroy your GRUB and that's why your computer boot only on windows.
All you have to do to solve your issue is to re-install GRUB : [http://www.ubuntuforums.org/showthread.php?t=76652](http://www.ubuntuforums.org/showthread.php?t=76652)

---

### Post by pbb on 2006-01-09
[QUOTE=frodon]When you install XP after ubuntu it destroy your GRUB and that's why your computer boot only on windows.[/QUOTE]

This guy says he's installed XP *first*. So I think his problems have another reason.

---

### Post by tabinin on 2006-01-09
Am I just old-school thinking that you need to re-work your systems so you have a setup like this?

Drive 0: Windows
Drive 1: Linux (Ubuntu)
Drive 2: Storage (music)

It might be a pain to start from scratch like this, but you will end up with an easier to support system and have less headaches going forward, I should think.

While your at it, make Drive 2 (music) FAT32 format so Linux can read/write to it.  The read support is there in Linux, but not ready for write support.

---

