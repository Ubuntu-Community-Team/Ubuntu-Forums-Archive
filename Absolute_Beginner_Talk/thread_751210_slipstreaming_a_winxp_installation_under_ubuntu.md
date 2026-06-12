---
title: "slipstreaming a winxp installation under ubuntu"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by case_thrives on 2008-04-10
Hello all, i'm new to the forums and to the ubuntu os as well.
I bought myself a laptop recently (hp 503), which came with vista os installed on it.
Owning a ubuntu livecd and much excitement to give it a try, i formatted the not so wanted vista from the hdd, and booted into ubuntu and installed it shortly.
I read about dual-booting, and tried to install (after ubuntu successfully installed, and I had my time to play a little bit with it...) win-xp for my pleasure of running games (i read somewhere that 'wine' is extremely complicated) that linux might not run.
The installation wouldn't recognize my hdd as I booted from the winxp cd.
I read a little about it, and found out that my SATA hdd didn't have any supporting drivers on the winxp cd (which is service pack 2). The solutions I found didn't really help me, because they were either windows related, partition related or required a floppy.
Firstly before even finding out that the installation didn't support my hdd, i created a NTFS partition for winxp, and a small FAT32 partition for sharing with gparted.
Later, when I found out about my hdd problem, I read a bit more.
Basically (from what I understood) I need to slipstream the drivers for the hdd into a new installation of winxp that I'm going to burn, so that the installation would recognize my SATA hdd . However, the solutions I have read offer nLite as a software for the slipstream, which is run under windows alone.
I don't know if it can run with 'wine', as I don't have any experience with this kind of API, especially running it under linux (... linux looks like a wild jungle to me).
Are there any softwares that can slipsteam files into a winxp installation, that run under ubuntu ?
I debate on whether i should locate a vista installation to simplify the process... 

thank you all for your help,
your friendly neighbor's cat :)

---

### Post by OffAxis on 2008-04-10
Have you tried the F6 "Install RAID or 3rd party drivers" during the installation process of WinXP?
It'll flash that message briefly at the bottom (3 or 5 seconds) about 1 or 2 minutes after you start booting from the WinXP cd.
You should be able to install your hdd driver then.

---

### Post by case_thrives on 2008-04-10
Thanks for the fast reply :)
I just checked out  F6, and it seems as though it requires a floppy only to load up the drivers.
I don't own a floppy on my  laptop .
Can it be done with a usb flash disk instead ? or any other media ?

---

### Post by OffAxis on 2008-04-10
I've only used floppies for it; so I'm not sure about the USB. Since USB is probably bootable on your new laptop I would think so, but can't say for certain.

The cd drive should be readable, so you could burn it to a disc and swap it out temporarily when it asks for the driver (without having to slipstream it into the windows disc)

---

### Post by case_thrives on 2008-04-10
do you think the installation will let me swap cds ?
i'll try the usb flash disk first, hope it works :)

---

### Post by OffAxis on 2008-04-10
ya, the installation pauses when you hit the the F6 key. 
After you're done with the installation of the driver, you can pop it out and it'll pick up where it left off.

---

### Post by case_thrives on 2008-04-10
I'll report back when I'm done tracking down the drivers I need :)

---

### Post by OffAxis on 2008-04-10
good luck.

---

### Post by Victormd on 2008-04-10
Just a thought, you're trying to install XP after Ubuntu? If so, I would advise you not to do that, or if you really need XP, (i) format the entire drive to install windows; and (ii) partition to reinstall Ubuntu, as Windows will not recognize your ubuntu partition and mess up your boot.  Since this is a new comp., I would think that you don't have anything important, right?

---

### Post by OffAxis on 2008-04-10
It will mess up the boot, but it's just a reinstall of the grub way from being corrected.
The easiest way is to use the supergrub disc.
[http://supergrub.forjamari.linex.org](http://supergrub.forjamari.linex.org)

---

### Post by Victormd on 2008-04-10
> **OffAxis said:**
> It will mess up the boot, but it's just a reinstall of the grub way from being corrected.
The easiest way is to use the supergrub disc.
[http://supergrub.forjamari.linex.org](http://supergrub.forjamari.linex.org)

That'll work, but he'll have to partition from Ubuntu, because windows won't recognize the partition

---

### Post by Jose Catre-Vandis on 2008-04-10
Long way round:

install VirtualBox on ubuntu

install XP in Virtualbox

Do all your slipstreaming work in XP inside VirtualBox

Save out your new ISO to Ubuntu for burning

Boot the new ISO and install

Fix grub as above

However, you may find that XP in Virtualbox does what you need, in which case you can run ubuntu and XP at the same time :)

---

