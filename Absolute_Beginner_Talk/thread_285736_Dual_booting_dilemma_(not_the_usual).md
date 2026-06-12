---
title: "Dual booting dilemma (not the usual)"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by Cybernetic Being on 2006-10-27
Here's the story: like many people, I want to use Linux but still have to have Windows around, so I want to set up a dual boot system. Now, I know this problem has been dealt with a few thousand times before and I've read all the guides I can find on the subject.

My laptop (generic unbranded make) on which I want to install Ubuntu, has _a single hard disk split into two partitions_, known to Windows as drive C and D. C is about 17 GB and D is about 20 GB. All my Windows system data is on drive C, and drive D has very little on it. So, my idea was to install Ubuntu on drive D and have a menu to choose which one to boot from on startup.

Unfortunately, I'm still confused about how exactly to act on the advice I've found on the net, as the guides I have read describe different 'pre-Ubuntu' system configurations than mine: either a single, unpartitioned hard disk with Windows on it that is partitioned, or two independent hard disks. As you can tell my laptop does not fully fit into either category.

So because my hard disk is *already* partitioned, I'm very confused about what to do. Is it possible to install Ubuntu on one *existing* partition of a single hard disk and retain the option of booting from another? Can I do this without screwing up all my data? I would, of course, back up everything important, but what I mean is I really don't want to risk messing up the whole disk and having to wipe it clean and start again with Windows.

To make things worse, both partitions are NTFS formatted, and I think I remember reading something about Linux having problems with this format. I also read something about having to create more than two partitions and some booting tool called GRUB... basically I'm royally confused.

Can anyone offer any advice? Please? :-?

---

### Post by Archmage on 2006-10-27
I think the easiest way would be to delete the partition for D and than go on in the manuals that assume that you resize your windows harddrive and go to the point where they are creating the additional partitions for windows.

**Please make sure that you delete the right partition.**

---

### Post by dmizer on 2006-10-27
> **Archmage said:**
> **Please make sure that you delete the right partition.**

good advice.  also make sure you have backups of your critical files in case you brick the whole thing.

if you have it in your posession, i suggest playing with a different computer you don't mind messing up.  you can get a feel for how things work.  practice makes perfect.

don't worry about the ntfs thing yet.  you'll need to think about that later after you have both systems up and running correctly.

---

### Post by NewbieNik on 2006-10-27
First and foremost, Backup any data you have on the D: drive, also make sure you have your boot CD supplied with the laptop (This is the only way you can recover the boot menu if it all goes pete tong)
Then in windows, right click on "My Computer" (Either in the start menu or on the desktop) and select "Manage"
In there is a disk manager. Here you can right-click on the D: drive and delte the partition, leaving you with C: at 17Gb and an unpartitioned space at 20Gb
Reboot the laptop with your Ubuntu CD inserted and follow the on-screen messages until you get to partitioning. Make sure you select "Use largest continous free space" and this should automatically choose the unpartitioned space.
Once installed you cannot just delete the Ubuntu drive as the GRUB bootloader information is stored there, so if you do want to remove it (I can't see why, but if you do) you need to boot from the original WIndows boot cd and choose the repair option and log in as administrator on the repair console and run fixmbr.

---

### Post by jmtjet on 2006-10-27
Here's a good how to for installing ubuntu;
[http://www.cs.cornell.edu/~djm/ubuntu/](http://www.cs.cornell.edu/~djm/ubuntu/)

Just remember to backup _all_of your important data on your Windows partition first. The boot loader-GRUB-needs to go on the Linux partition or you won't be able to boot to Windows. After your Ubuntu install it will take a little time to get everything setup the way you want, but after a while you'll be glad you installed ubuntu. Good luck,and have fun. 

PS: I use Ubuntu about 90% of the time now. It's as solid as a rock. :D

---

### Post by Cybernetic Being on 2006-10-27
Thank you all for your replies.

To my regret I gave away the old computer I originally intended to use as a testing ground for Linux, so I'll have to take my chances with my laptop.

So if I understand NewbieNik and the guide whose link jmtjet posted, here's what I should do: delete the D partition as you described, then reboot, start installing Ubuntu, and the installer will automatically detect the empty space once occupied by drive D and create a bootable Ubuntu partition, correct?

I'm still a little confused about the role of GRUB. The guide jmtjet posted says '*...you can decide to keep any existing Windows partition(s) (in which case Ubuntu will install itself with dual boot options*' so I assume the installer will deal with setting GRUB up... right?

Sorry if these are really silly questions but I hadn't even heard of Ubuntu at the start of this week ;)

---

### Post by gn2 on 2006-10-27
If you are going to install a dual-boot, first thing you need to do is get every piece of data you want to keep backed up to removeable media.

Alternatively you could always replace the hard drive, and install to that, keeping your existing one on a shelf safe from potential harm.
This effectively gives you a separate PC to play around with trying it out.

(and additional storage if you get a USB enclosure)

Removing a laptop hard drive isn't always a major problem, on some it's just one screw holding it in!

---

### Post by CatKiller on 2006-10-27
> **Cybernetic Being said:**
> ...so I assume the installer will deal with setting GRUB up... right?

That is the plan in principle. If it doesn't quite work in pracise - GRUB gets installed to the MBR but doesn't have a Windows entry, for example - it's quite easy to fix.

Good luck, and enjoy your Ubuntu.

EDIT:
> and the installer will automatically detect the empty space once occupied by drive D and create a bootable Ubuntu partition, correct?
Select the "use largest continuous free space" option - the place that used to have your D: partition is the largest free space by quite some margin. Actually, it will create two partitions in this space - one for the actual data, and one for the swap partition. The swap partition is like Windows swap file, except that you get to use an optimised filesystem for it.

It should be fairly apparent that deleting the D: partition will delete the data on it. Move it somewhere else, like your C: drive, if you want to keep it.

---

### Post by elchinovi on 2006-10-27
I have a different idea...
Do you have free space on your C: drive to move the files from D:?
Because if you don't, or if you want to keep those files where they are and have a different partition to store some files, what you can do is shrink D: as much as you want, and then use that empty space to install Ubuntu there...
It's just a different approach.
My 2 cents!
Good Look!

---

