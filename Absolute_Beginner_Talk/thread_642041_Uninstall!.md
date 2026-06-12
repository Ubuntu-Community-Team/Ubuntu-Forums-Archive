---
title: "Uninstall!"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Cheat King on 2007-12-16
OK, so, I have searched for how to do this, but I only get results for uninstalling using XP.

So, my problem is that I have Ubuntu on my laptop, but I want to remove it so that I can install windows Vista and the re-install Linux so that I can dual boot. So can anyone help me please? My Ubuntu is running really slow at the moment, so I am running from a 7.04 Live CD.

Help appreciated...

---

### Post by macogw on 2007-12-16
You don't need to uninstall OSes.  You just install something on the hard drive, and it'll overwrite it.  It's possible XP might be confused by the hard drive being ext3 right now, so you can boot your Ubuntu CD and go system > admin > partitioner and then do your partitioning first (which is really the best way, IMO, to go about dual-booting) and make sure to set the XP partition as NTFS or FAT32 when you partition it, then Windows will definitely not be confused.

---

### Post by Cheat King on 2007-12-16
Hmm, you musn't have read my post very well. I am wanting to install Vista. I didn't know if it was any different. And I do not have the 'Partioner' option on my Live CD.

---

### Post by macogw on 2007-12-16
> **Cheat King said:**
> Hmm, you musn't have read my post very well. I am wanting to install Vista. I didn't know if it was any different. And I do not have the 'Partioner' option on my Live CD.
OH yeah sorry I read the first line as you seeing info for uninstalling XP (as opposed to "with XP")

It's the same, anyway though.  FAT32 works with everything.  NTFS is for XP or Vista, and Ubuntu can read & write with it.

It should be there.  It might be called GNOME Partition Editor or something?  You can alt+f2 to get a runbox and type "gparted"

---

### Post by Gone fishing on 2007-12-16
I think if when you install Vista (ughh) you will be able to tell it to use all the hard drive. However, if you want to remove Ubuntu first boot up on the live CD open the partition editor   (System > Administration > Partition editor) and delete the Ubuntu partition. If you are going reinstall Ubuntu you could leave the swap partition.

If your Ubuntu's slow I dread to think what Vista's going to be like (actually I have a friend how says Vista's quite cool if you have 4 Gig of RAM)

---

### Post by macogw on 2007-12-16
> **Gone fishing said:**
> I think if when you install Vista (ughh) you will be able to tell it to use all the hard drive. However, if you want to remove Ubuntu first boot up on the live CD open the partition editor   (System > Administration > Partition editor) and delete the Ubuntu partition. If you are going reinstall Ubuntu you could leave the swap partition.

If your Ubuntu's slow I dread to think what Vista's going to be like (actually I have a friend how says Vista's quite cool if you have 4 Gig of RAM)

Odd.  At 4GB on 32bit Vista with 64bit hardware, Vista throttles data transfer speeds on peripherals severely.  [http://www.commonsense4commonpeople.net/2007/12/how-adding-more.html](http://www.commonsense4commonpeople.net/2007/12/how-adding-more.html)

---

### Post by zabien1970 on 2007-12-16
I'm actually interested in how this turns out, from what I've read Vista is a nasty creature that likes to be installed first.
 If you have the 'live-cd' of ubuntu I'd suggest installing vista first then installing ubuntu, there is a sticky in this forum at the top which tells you how, good luck




Edit: if you install vista I believe it will reformat your harddrive which will erase ubuntu, xp, and everything else, then as I said you can start new

---

### Post by dgoosens on 2007-12-16
hi,

I don't really understand your problem...

I'd say, just pop in the Vista CD (although it is even worse than XP) and boot. You should be ask what to do. Select format HD. Then, you should be able to create a new partition as big as you want and install Vista on that partition (don't touch the rest of the HD).
When done installing Windows, pop in Ubuntu 7.10 live CD and install on the "clean" partition... Ubuntu will format it into ext3 (or something else if you want to) and also install Grub for the dual-boot.
Ubuntu will recognize the NTFS partition where Windows is installed and I know there are plugins to enable that silly Windows to write-read on ext3 partitions...

Hope this helps.
dGo

---

### Post by macogw on 2007-12-16
> **dgoosens said:**
> 
Ubuntu will recognize the NTFS partition where Windows is installed and I know there are plugins to enable that silly Windows to write-read on ext3 partitions...

Hope this helps.
dGo
fs-driver.org is only for xp to read/write to ext3, not vista

---

### Post by Gone fishing on 2007-12-16
>  Odd. At 4GB on 32bit Vista with 64bit hardware, Vista throttles data transfer speeds on peripherals severely. [http://www.commonsense4commonpeople....ding-more.html](http://www.commonsense4commonpeople....ding-more.html) 

I suspect he's using the 64 bit as the 32 bit Vista can only use 3.12 GB [http://support.microsoft.com/kb/929605](http://support.microsoft.com/kb/929605) - however, I think your article must refer to pre-Vista  x86 Windows Vista runs so slow on 1GB Ram and 512 MB is just pure torture.

---

