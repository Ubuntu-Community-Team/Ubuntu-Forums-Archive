---
title: "Dual boot: Installing Xp when I've already got Breezy running..."
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by benfinkel on 2006-04-17
Hey Guys,

Maybe I just didn't search enough, but I couldn't find any information about getting Dual-Boot going from this direction.

All of the guides suggest installing XP first, then Ubuntu on top of it, but in all of my past Linux experience the best way to setup a Dual Boot has always been the reverse.

So, I've got Ubuntu installed, and I'm ready to fire up XP also.  Anyone point me towards a decent guide?

Thanks,

-Ben

---

### Post by cilynx on 2006-04-17
The problem is the XP generally does whatever-the-hell it wants to your hard drive.  In my experience, the best route is to format the drive, partition how you want it (making sure to place a FAT32 or NTFS partition), install XP (it'll go onto said partition and set up it's bootloader), install Linux (you can put it where you want and install a reasonable boot / chain loader).  

I know this doesn't answer you question, just pointing out why people say that it goes that way.

---

### Post by Jimmey on 2006-04-17
Yeah, just to reinforce what cilynx says; when you install XP after Breezy, it will re-write the master boot record, leaving you with no option, at boot time, to select Breezy from. The only way to sort this problem is to boot from either a live or a Breezy install CD and install Grub on the MBR.

---

### Post by linjiaoyang on 2006-04-17
I've done this already, it's pretty simple. Here's a short guide:

1. Install Windows XP
2. Put in the Ubuntu Install CD
3. Reboot and boot from the CD
4. Just keep pressing enter until you get to the screen where it asks you which drive you want to install Ubuntu on
5. Choose Manually Edit Partitions
6. Select your Ubuntu partition and change "/dev/hda?" to root "/"
7. Choose Finished editing and apply changes (something like that)
8. It's going to tell you that there's an error and it can't install Ubuntu on that drive, just press continue.
9. Scroll down and select "Install the GRUB bootloader"
10. Restart and now GRUB is installed and you can select which parition to boot from.

---

### Post by benfinkel on 2006-04-17
Ok.

So, it sounds like the trick is to get XP installed on a partition I create ahead of time, and then get Ubuntu to install GRUB into the MBR so I can choose which OS to launch.

Easy enough.  I'd like to create the NTFS partition prior to installed XP, what is the Linux program that'll do that?

Thanks all for the direction!  Side note: please don't think poorly of me because I want to get XP back on, I miss my guild wars :(

-Ben

---

### Post by cilynx on 2006-04-17
Contrary to popular opinion, there are reasons to run Windows.  You'll get no flak from me.

All you have to do prior to installing Windows is to "mark" the partition NTFS, which gParted can easily handle.  The Windows installer will handle "formatting" the partition for NTFS.

---

