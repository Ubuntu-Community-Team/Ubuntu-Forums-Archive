---
title: "Total n00b - how to remove 5.04 and GRUB?"
date: 2005-10-28
forum: Absolute Beginner Talk
---

### Post by timeshift on 2005-10-28
Hi Guys,
I'd sampled with Ubuntu 5.04 for a while and decided earlier today I wanted to remove it and reclaim drivespace for my first partition (XP). Removed the Ubuntu partition with partitionmagic 8 and rebooted, Error 22 on GRUB loader :(

I used partitionmagic 8 for DOS to gain some free space again, then reinstalled Ubuntu, and now I can boot in to my first partition again.

How does a n00b remove GRUB and Ubuntu from a second partition safely without damaging the first partition?

Thanks!

---

### Post by darrenrxm on 2005-10-28
I hate the slang word "noob" for some reason. It sounds so negative to me... anyway, I don't think your a noob or whatever. Just someone who needs help. The easiest way to get rid of grub is to boot with a windows start disk floppy and use the command fdisk /mbr. Then you can use partition magic (or ubuntu disk) to delete the ubuntu partition. To prevent this from happening again. I would suggest you install grub onto a floppy and use that to boot with instead. 

And please stop calling yourself a noob. I've been in your position many times before with different linux installs.

---

### Post by timeshift on 2005-10-28
My modern laptop doesnt have a floppy drive :???:

---

### Post by zerhacke on 2005-10-28
I can't believe I'm going to suggest doing this but... put your Windows XP CD in the CD Rom drive.  Choose to start recovery console.  When logged into recovery console, type in 

fixmbr
fixboot

Hit enter after each word.  Restart.

---

### Post by timeshift on 2005-10-28
Haha... I spent about 30 minutes looking for my XP CD (seriously) to try and run the repair console when I accidently deleted the partition without GRUB (fixed it in the end by reinstalling ubuntu)

So, just to be difficult, I can't use floppy discs and I can't find my XP CD... any other suggestions? :rolleyes:

I do however have partitionmagic 8 for DOS which I booted from CD earlier which had a DOS prompt... any help?

---

### Post by zerhacke on 2005-10-28
You could reinstall Ubuntu again, this time not opting for the standard partitioning.  When you get to partitioning, set it up yourself.  Give yourself a 50Mb /boot partition, a swap, and a / partition.  Let it install.  Edit your /boot/grub/menu.lst file to show ONLY Windows XP.

Then shut down Ubuntu.  Restart to Windows.  Use the computer management console in the Control Panel to wipe out the / and swap partitions, leaving the /boot.  Repartition those partitions so that Windows can use them.

You lose 50Mb in that you must keep that partition there forever, or untill you find your XP CD (that's not pirated, of course) but it gets you back drive space for Windows.

---

### Post by timeshift on 2005-10-28
Well, the drive space was actually meant to be reclaimed so I could install this copy of Vista I have :p

And therefore needs to replace the current GRUB bootloader.

What would happen exactly if I reformatted the Ubuntu partition with plenty of space, rebooted to the error 22 bit in GRUB, but then install Vista as dual boot? Would it overwrite GRUB as the boot loader or what? (or is this linux only, hehe)

---

### Post by zerhacke on 2005-10-28
Then just install Vista.  It'll overwrite the boot sector.

---

### Post by timeshift on 2005-10-28
Positive? Last time when I ran 98/XP as dual boot, I then installed linux and made it tri-boot... will it overwrite or append?

Can I do something with the Ultimate Boot CD? ([www.ultimatebootcd.com](www.ultimatebootcd.com))

---

### Post by Herman on 2005-10-28
Another option only a few people are aware of so far is the GAG boot loader. You can read a bit about it from this link:
[http://www.ubuntuforums.org/showthread.php?t=79286&highlight=GAG+boot+loader](http://www.ubuntuforums.org/showthread.php?t=79286&highlight=GAG+boot+loader)
I'm trying it out right now and I'm starting to think it's a pretty handy thing for lots of reasons, not the least of which is it allows you to change operating systems as often as you like and can be re-configured to suit, and it'll always boot Windows. Check it out if you like. (Herman).

---

### Post by timeshift on 2005-10-28
I had a read of that just then, but the commands it talks of are unknown to me (n00b)... is it easy to install and use? How much command-line is involved?

I don't have a floppy drive, so I can't test it either. It does look very interesting though.

Er......... i went in to the GAG boot loader through the ISO I found... didnt seem much good. It had the first drive there only, and options to add more - tried adding the linux partition, but said it was unbootable, possibly due to the fact i didnt go through the whole ubuntu install - only up to the first reboot. Went back in and out a few times, and then it freezes. Ok, reboot without the cd to make sure the mbr is still fine, but no blinky line that pre-empts the GRUB loader appears, only a black screen.

Then suddenly... "Windows XP ...."

Where did GRUB go?!?!?! Oh well, good riddance!!!!!!!

Now that i'm booting straight to XP, i'm assuming it's now safe to simply remove or reformat the partition with partitionmagic and be on my merry way?

---

### Post by davmac on 2005-10-28
If I were you I'd download and burn a copy of the Ultimate Boot CD from [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

It has go all the tools on there for fixing your MBR and deleting/recreating partitions.

HTH,

Dave Mac

---

