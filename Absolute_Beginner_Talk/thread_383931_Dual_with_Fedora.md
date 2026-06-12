---
title: "Dual with Fedora"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Guinness Bug on 2007-03-13
Okay, so I've been working on ubuntu for a while now, and have set up a lot of things. (Thanks to the great help of you wonderful people!)
My question now is- can I dual boot with Fedora Core 6, or will that cause some problems?
Thanks again- I wouldn't be where I'm at if it weren't for you folks!

---

### Post by taurus on 2007-03-13
You shouldn't have any problem dualbooting Ubuntu and FC6.  If you install FC6 last, it will install it own GRUB to MBR and there should be an entry to boot Ubuntu from the menu.  And if you install Ubuntu last, than Ubuntu would do the same.

---

### Post by lamalex on 2007-03-13
You can do it no problem. In my opinion, there's no point. Ubuntu > Fedora, even ask Erik Raymond!!

---

### Post by Guinness Bug on 2007-03-13
> **Iamalex said:**
> You can do it no problem. In my opinion, there's no point. Ubuntu > Fedora, even ask Erik Raymond!!

A lot of people tell me that ubuntu is better than FC6, I just have to have it installed for a Linux class I'm taking. Starts this week- I'm excited!

---

### Post by Gerard Barberi on 2007-03-13
> **taurus said:**
> You shouldn't have any problem dualbooting Ubuntu and FC6.  If you install FC6 last, it will install it own GRUB to MBR and there should be an entry to boot Ubuntu from the menu.  And if you install Ubuntu last, than Ubuntu would do the same.

Once I installed FC5 onto my PC to dual boot with Ubuntu.  For some strange reason I couldn't boot into Ubuntu.  I had to restore grub first.  I wonder if that's something in FC5.

---

### Post by igknighted on 2007-03-13
I think Fedora rocks... I like it more than Ubuntu, but Ubuntu runs better on some of my HW so I use it too.  While you can tell Fedora to not install a bootloader, I find Fedora's grub to be nicer looking (and with Fedora you will update kernels more often) so its better to use their grub.  Just let it install over Ubuntu's.  If you ever get rid of FC6 you can get Ubuntu's grub back easily via the live CD.

---

### Post by Guinness Bug on 2007-03-13
> **igknighted said:**
> I think Fedora rocks... I like it more than Ubuntu, but Ubuntu runs better on some of my HW so I use it too.  While you can tell Fedora to not install a bootloader, I find Fedora's grub to be nicer looking (and with Fedora you will update kernels more often) so its better to use their grub.  Just let it install over Ubuntu's.  If you ever get rid of FC6 you can get Ubuntu's grub back easily via the live CD.

Hey- thanks! This information really is helpful, guys! Wow.
Question, though- can I put an additional hard drive in my computer and just put FC6 on one and keep ubuntu on the other, or is that even possible?

---

### Post by lamalex on 2007-03-13
that is entirely possible, just when you install fc6 tell it to install to the other hard drive.

---

### Post by Guinness Bug on 2007-03-13
> **Iamalex said:**
> that is entirely possible, just when you install fc6 tell it to install to the other hard drive.

Fantastic! This is why I love this place- I get straight answers, and I am learning so quickly.
Thanks!

---

### Post by Salarzae on 2007-03-19
I was running FC6 till now but wanted to try Ubuntu. After playing with my partitions and installing Ubuntu, I came to know that I screwed FC6 as I can't boot that one. I tried to play with Grub as per my knowledge (which is a bit meager) but the last message I got was "Can't mount partition". Now to cut short, what am I missing?

The entry in grub is as follows:-

[COLOR="SlateGray"]title		Fedora Core 6:
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.18-1.2798.fc6 root=/dev/sda7
initrd		/boot/initrd.2.6.18-1.2798.fc6.img
savedefault
boot
[/COLOR]

Any suggestions?

---

### Post by dstew on 2007-03-19
You might need to edit the root entry. Is your sda disk really (hd0)? If so, the root should probably be (hd0,6).

---

### Post by Salarzae on 2007-03-20
BTW, I tried it another way but still was not able to rectify the problem. Is it that Ubuntu can't recognize the LVM partition or what?

Here is the edited lines in grub:

[I][COLOR="DimGray"]root		(hd0,7)
kernel		/boot/vmlinuz-2.6.18-1.2798.fc6 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
initrd		/boot/initrd-2.6.18-1.2798.fc6.img[/COLOR][/I]

Anticipating!

---

### Post by Salarzae on 2007-03-20
> **dstew said:**
> You might need to edit the root entry. Is your sda disk really (hd0)? If so, the root should probably be (hd0,6).

It is hd0 and as per fdisk screen shot below, it must be hd0,7!

[COLOR="DimGray"][I]dev/sda1 1 12 96358+ de Dell Utility
/dev/sda2 * 13 2951 23607517+ 7 HPFS/NTFS
/dev/sda3 2952 11769 70830585 f W95 Ext'd (LBA)
/dev/sda4 11770 12161 3148740 c W95 FAT32 (LBA)
/dev/sda5 2952 5891 23615518+ 7 HPFS/NTFS
/dev/sda6 5892 8831 23615518+ 7 HPFS/NTFS
/dev/sda7 10464 10476 104391 83 Linux
/dev/sda8 10477 11769 10385991 8e Linux LVM
/dev/sda9 8855 10202 10827778+ 83 Linux
/dev/sda10 10203 10463 2096451 82 Linux swap / Solaris[/I][/COLOR]

---

### Post by dstew on 2007-03-20
Grub counts from 0, so hd0,7 = /dev/sda8, which is your LVM partition. Are you really trying to boot from the Linux LVM partition?

Per the LVM how-to ([http://tldp.org/HOWTO/LVM-HOWTO/index.html)](http://tldp.org/HOWTO/LVM-HOWTO/index.html)), boot loaders "do not yet understand LVM volumes". You need to boot to a regular partition. If you want a big LVM, you at least need to make a small boot partition to boot to.

---

### Post by Salarzae on 2007-03-28
Boot Loaders don't understand LVMs but I'm still not able to boot with regular partition.

I changed it to: 

root (hd0,6)
kernel /boot/vmlinuz-2.6.18-1.2798.fc6 root=/dev/sda7
initrd /boot/initrd-2.6.18-1.2798.fc6.img

Still not resolved!

---

### Post by scatfly on 2007-03-28
so i have ubuntu on my one sata drive and FC6 on IDE drive.  When IDE is connected though it does not give me a boot menu where i can choose with one to start!

---

### Post by jerryrw on 2007-03-28
Check if your FC kernels are in the sda7 base dir or in a directory called /boot.  the root command in the grub menu.lst tells it that all paths are relavent to the base dir of sda7(hd0,6).  FC likes to install separate /boot partitions and graft them into the root file system so maybe removing the /boot/ specifier form you kernal commands may do the trick

---

### Post by Salarzae on 2007-04-01
> **jerryrw said:**
> Check if your FC kernels are in the sda7 base dir or in a directory called /boot.  the root command in the grub menu.lst tells it that all paths are relavent to the base dir of sda7(hd0,6).  FC likes to install separate /boot partitions and graft them into the root file system so maybe removing the /boot/ specifier form you kernal commands may do the trick


It was a great help! This is what I did and bang, it worked as fine as ever before.

The new grub loox like this and now both OS are booting as I wanted it to be!

[I][B]title Linux Fedora Core 6
	
root		(hd0,6)
kernel		/vmlinuz-2.6.18-1.2798.fc6 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
initrd		/initrd-2.6.18-1.2798.fc6.img[/B][/I]

The /boot was removed and /dev/VolGroup00/LogVol00 was added to the menu.lst. 

CASE SOLVED! Thanks again for the help!

---

