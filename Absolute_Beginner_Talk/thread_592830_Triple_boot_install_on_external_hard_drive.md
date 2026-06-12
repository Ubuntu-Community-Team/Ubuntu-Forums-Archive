---
title: "Triple boot install on external hard drive?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Crandom on 2007-10-26
Basically, I have been with windows all my life, although I have been looking at using linux, particaually Ubuntu for a long time. I finally want to install GG (now with ATI drivers install already:)) onto my system. Currently it has:

[LIST]
[*]hd0 - 4.33Gb - ACER recovery thing for XP
[*]hd1 - 53.2Gb - 2.95Gb free - XP system
[*]hd2 - 53.6Gb - 5.67Gb free - Vista system
[*]sda - 320Gb - 249Gb free - External storage HDD
[/LIST]

I am running an ACER Aspire 5103WLMi (not on the Laptop list thing) and want to install Ubuntu onto my External HDD (sda) as a triple boot with vista and xp (I installed xp first). I have a few questions:

[LIST]
[*]Will it boot if I put ubuntu onto a partition that is not the first on sda? I want to keep the data I already have on it first so gparted doesn't have to move it and so windows will defnately recognised it.
[*]Can you install unbuntu onto ntfs now?
[*]Could you manipulate GRUB in some way so that I don't have the choice to run ubuntu when sda is not in? Install it on the sda and boot from it mabye?
[*]How much space should I have on my ubuntu partition to install it?
[*]I heard there was a way to make your documents stay while making another partition for system data to do a clean install for each update. How would you do this?
[/LIST]

My BIOS has the ability to load from an external USB HDD.

Thanks in advance.

---

### Post by Crandom on 2007-10-26
bump - its late

---

### Post by Crandom on 2007-10-27
bump - plz help me!

---

### Post by Duck2006 on 2007-10-27
> **Crandom said:**
> Basically, I have been with windows all my life, although I have been looking at using linux, particaually Ubuntu for a long time. I finally want to install GG (now with ATI drivers install already:)) onto my system. Currently it has:

[LIST]
[*]hd0 - 4.33Gb - ACER recovery thing for XP
[*]hd1 - 53.2Gb - 2.95Gb free - XP system
[*]hd2 - 53.6Gb - 5.67Gb free - Vista system
[*]sda - 320Gb - 249Gb free - External storage HDD
[/LIST]

I am running an ACER Aspire 5103WLMi (not on the Laptop list thing) and want to install Ubuntu onto my External HDD (sda) as a triple boot with vista and xp (I installed xp first). I have a few questions:

[LIST]
[*]Will it boot if I put ubuntu onto a partition that is not the first on sda? I want to keep the data I already have on it first so gparted doesn't have to move it and so windows will defnately recognised it.
[*]Can you install unbuntu onto ntfs now?
[*]Could you manipulate GRUB in some way so that I don't have the choice to run ubuntu when sda is not in? Install it on the sda and boot from it mabye?
[*]How much space should I have on my ubuntu partition to install it?
[*]I heard there was a way to make your documents stay while making another partition for system data to do a clean install for each update. How would you do this?
[/LIST]

My BIOS has the ability to load from an external USB HDD.

Thanks in advance.

Linux will not run on a NTFS formated drive. The only way to do this is to run it from some thing like VMWare. If you want it to run from the external you will have to partition a part of the drive to run GG from, round 20Gb sould be ok.

---

### Post by Crandom on 2007-10-27
would W95 FAT32 be ok for linux or does it have to be ex2?

---

### Post by Duck2006 on 2007-10-27
> **Crandom said:**
> would W95 FAT32 be ok for linux or does it have to be ex2?

It has to be ext2 or ext3.

---

### Post by mkc on 2007-10-27
>>Could you manipulate GRUB in some way ...

It just so happens that someone was talking about booting from external HDs in Linux Format this month - He said that hitting F8 at bootup will give you a list of devices to boot from in any computer post 2002. So put GRUB on the external disk with Ubuntu and at boot time if you want to use your ubuntu setup rather than your M$ one you can select that disk. At all other times your computer will boot as it currently does.

>>Will it boot if I put ubuntu onto a partition that is not the first on sda?...
I don't think that's a problem, although you may need a small (50Mb) boot partition at the top of the disk to make this work. I would sugest a more reliable/simpler way would be getting Windows to move your current partition- That way you've no worries about loosing information - windows know's how to use NTFS properly (at least you'd hope so!) and Gparted won't have to do anything more than create your linux partition during the install.

>>Can you install unbuntu onto ntfs now? 
I don't think Ubuntu's installable on NTFS as the NTFS write drivers are experimental but you'd have to make an Ubuntu partition anyway so there shouldn't be any loss in you using ext3. 

>> How much space should I have on my ubuntu partition to install it? 
It depends how much software you're putting on it and if you're using separate partions for /home, /var and the like.
I prefer to keep my home partition separate and install quite a bit of software so I have 9GB root (which is plenty), 512MB swap and the rest is /home.

The reason I keep home separate is incase I wan't to do a clean install/ try a different distro/ my root patition gets screwed! - in installation you can just say which partition you want to use as /home, you don't have to format it, so you can use an old home partition in a new /clean install.

On that note though, particularly when using laptops etc you're likely to spend a good while making everything work just as you like, so doing a fresh install every 6months (the update cycle) is a little foolish - ubuntu does updates brilliantly without the need for wiping everything and starting again!

To allow you to keep all your files - windows and linux - in one place I'd suggest you just put a link in your home directory to one of your windows My Docs folders. Again you won't be able to just mount an NTFS/FAT partition as your home because linux keeps settings and stuff in your home folder and doesn't like using none Unix partitions for this.

Hope that helps.

mark

---

### Post by Crandom on 2007-10-27
hopefully this will work - im going to skip the 50mb boot partition as vista can't create space before a volume when shrinking. Im just going to hope for the best try not to overwrite my windows partition like i did last time. Just in case, if i umount hda1 and hda2 will setup detect them?

---

### Post by meierfra on 2007-10-27
> Could you manipulate GRUB in some way so that I don't have the choice to run ubuntu when sda is not in? Install it on the sda and boot from it mabye?

Yes. Install grub to /dev/sda and set  sda to be first in the boot order in the bios.

---

### Post by Crandom on 2007-10-27
Ok i have just tried to install it and failed MISERABLE - although it's probably not because of me. Basically, my external HDD now looks like this:

SDA
[LIST]
[*]sda1 - ntfs - 289GB
[*]unallocated - notused - 6.38MB - I CAN'T GET RID OF IT! although it probably doesn't matter.
[*]sda2 - ext3 - 6GB - Mounted as: /
[*]sda3 - ext3 - 1GB - Mounted as: /home
[*]sda4 - linux-swap - 2GB - Mounted as: swap
[/LIST]

Basically, I set the install up as above with sda2 and sda3 being formatted and when it comes to install, it jumps to 15%, saying "Detecting Filesystems" and stays there. I left it for 1.5 hrs and it did nothing. No disk activity, cd not spinning and cpu doing nothing. I have verified cd data and md5 of iso. Any idea whats wrong? Oh, and when i'm selecting my partions to install to, it says that the space used in sda1 is "unknown", and hda1 is mounted as /media/hda1 and hda2 as /media/hda2 and hda3 as /media/hda3. Does this have any significance in respect to the installation process?

Finally, in step 7, you can select advanced options and choose where to install GRUB. Default is "(hda)". Why is it in brackets? Should I put "(sda)" (then how would know to install to sda2) or "/dev/sda2" or "(/dev/sda2)" to put it in sda2. Also, should I make sda2 have the flag "boot" in gparted for it to boot from there or just leave it?

Any help would be extremely appreciated as I'm going off linux..................................................

---

### Post by Crandom on 2007-10-27
also, the install program has failed to run sevral times when I tried to start it and gparted crashes whenever it tries to rescan the drives after an operation is carried out.

---

### Post by Crandom on 2007-10-28
help?!?!? please?

---

### Post by logos34 on 2007-10-28
> **Crandom said:**
> Basically, I set the install up as above with sda2 and sda3 being formatted and when it comes to install, it jumps to 15%, saying "Detecting Filesystems" and stays there. I left it for 1.5 hrs and it did nothing. No disk activity, cd not spinning and cpu doing nothing. I have verified cd data and md5 of iso. Any idea whats wrong? Oh, and when i'm selecting my partitons to install to, it says that the space used in sda1 is "unknown", and hda1 is mounted as /media/hda1 and hda2 as /media/hda2 and hda3 as /media/hda3. Does this have any significance in respect to the installation process?

Finally, in step 7, you can select advanced options and choose where to install GRUB. Default is "(hda)". Why is it in brackets? Should I put "(sda)" (then how would know to install to sda2) or "/dev/sda2" or "(/dev/sda2)" to put it in sda2. Also, should I make sda2 have the flag "boot" in gparted for it to boot from there or just leave it?

If you're only gonna give /home 1 gb you might as well not even bother...and 1 gb swap is more than enough.  Can't you make a little more room for linux by shrinking ntfs partition some more?  If it's having a problem recognizing sda1 boot into windows and run defrag on it and error-checking (chkdsk) if necessary.  Boot up the ubuntu live cd, system>admin>gparted...if it recognizes sda1 shrink it some more (has to be unmounted first).  Then try the install process again...6-9 gb for /, 1 gb swap and rest of free space for /home.  For grub-install you want to type in **/dev/sda** or** (hd1)**.  That will put it on the USB drive's MBR.  But then you will need to edit menu.lst so 'root' lines point to (hd**0**,1):

[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)
(-->post #502)

---

