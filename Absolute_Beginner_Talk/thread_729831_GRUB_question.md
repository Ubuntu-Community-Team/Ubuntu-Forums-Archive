---
title: "GRUB question?"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by mahela007 on 2008-03-20
I would like to uninstall Ubuntu. (I just TEMPORARYLY need the extra hard disk space). 
According to what I have read the only way to uninstall ubuntu is to format the partition on which it is installed.
But when that is done what about the GRUB boot loader? Will it update itself to show that ubuntu is no longer installed on the computer? That is, will it update itslef to show that only windows is installed? 
If it doesn't do that I am prepared to uninstall it. I just dont know how to do it. Has anyone else uninstalled ubuntu? Thanks fo your help

---

### Post by spiderbatdad on 2008-03-20
GRUB is used by Ubuntu to boot operating systems located on your HD. Windows uses a MBR (master boot record) To uninstall Ubuntu, one generally inserts the windows xp cd,  boots into recovery mode, and runs fixmbr. If you "google" uninstall ubuntu, you will find numerous examples of this procedure.

---

### Post by Duck2006 on 2008-03-20
Some reading may help.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Edit: Sorry disregard i been doing 10 thinks a once here today

---

### Post by bumanie on 2008-03-20
It would probably be esier to source an external drive or something. If unable to do that, as you need the extra space for a temorary time, you will have to format the ubuntu partition. This will not remove grub from the mbr. Not sure whether you are using xp or vista, but you will have to overwrite the mbr with windows bootloader. The method is slightly different between xp and vista. In xp, enter recovery console. Choose which installation (usually 1) then type your administrator password. Next type fixboot --> enter
fixmbr --> enter
exit --> enter
Under vista it depends whether you have a recovery disc or only a recovery partition.

---

### Post by Dr Small on 2008-03-20
> **spiderbatdad said:**
> GRUB is used by Ubuntu to boot operating systems located on your HD. Windows uses a MBR (master boot record) To uninstall Ubuntu, one generally inserts the windows xp cd,  boots into recovery mode, and runs fixmbr. If you "google" uninstall ubuntu, you will find numerous examples of this procedure.
That simply will not uninstall ubuntu. It just overwrites GRUB with Windows MBR.
Ubuntu would still be on it's partition, simply without GRUB to access it.

Dr Small

---

### Post by mahela007 on 2008-03-20
bit of a problem.
I dont have the XP cd

---

### Post by philinux on 2008-03-20
This can do the fixmbr without the xp disk.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by forrestcupp on 2008-03-20
> **philinux said:**
> This can do the fixmbr without the xp disk.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

+1
Super Grub worked for me, when fixmbr did not.  There is an option in Super Grub to restore the Windows boot loader.

You will still have to format the Ubuntu partition.

---

### Post by spiderbatdad on 2008-03-20
> **Dr Small said:**
> That simply will not uninstall ubuntu. It just overwrites GRUB with Windows MBR.
Ubuntu would still be on it's partition, simply without GRUB to access it.

Dr Small

Thank you for pointing that out, however, where is the solution? One could of course use the xp cd to reformat the entire disk. Seems like the Community Documentation needs a good guide for this matter.

---

### Post by Dr Small on 2008-03-20
> **spiderbatdad said:**
> Thank you for pointing that out, however, where is the solution? One could of course use the xp cd to reformat the entire disk. Seems like the Community Documentation needs a good guide for this matter.
Here's how I would do it. To begin with, if I needed to get Ubuntu off of a dualboot system, I would begin by loading the Gparted LiveCD and delete the Ubuntu Partitions.

Then the next time you boot, you will get a GRUB error. Pop in the XP cd and fix the MBR. This allows you to use XP again, and gives you back all of your original disc space.

Dr Small

---

### Post by forrestcupp on 2008-03-20
> **Dr Small said:**
> Here's how I would do it. To begin with, if I needed to get Ubuntu off of a dualboot system, I would begin by loading the Gparted LiveCD and delete the Ubuntu Partitions.

Then the next time you boot, you will get a GRUB error. Pop in the XP cd and fix the MBR. This allows you to use XP again, and gives you back all of your original disc space.

Dr Small

And if that doesn't work, use the Super Grub disk.

---

### Post by mahela007 on 2008-03-20
so whats my best course of action?
I dont have the xp cd and it looks like I need to uninstall ubuntu. what to do?

---

### Post by caravel on 2008-03-20
If you want to do it from windows your best course of action is the logical disk manager (run -  "diskmgmt.msc"), you can remove and reformat the linux partitions into NTFS or FAT32 from there (don't nuke your windows partitions in the process!).  To restore the bootloader you can use any Win9x bootdisk, e.g. an old Windows 98 or 95 one and just boot from that to a command line and do: "fdisk /mbr" from the and that will fix it (the M$ MBR hasn't changed for eons).  You can also do the "fixmbr" command from the recovery console of a Windows NT/2000 disc to achieve the same effect.

---

### Post by forrestcupp on 2008-03-20
> **mahela007 said:**
> so whats my best course of action?
I dont have the xp cd and it looks like I need to uninstall ubuntu. what to do?

If you don't have your XP CD, your best course of action is to download [GParted LiveCD](http://gparted-livecd.tuxfamily.org/) and [Super Grub](http://supergrub.forjamari.linex.org/).  Then burn both images to CDs and they will both be bootable CDs.

First, boot to the GParted LiveCD and use it to format your Ubuntu partitions to NTFS, or delete them and resize your Windows partition to take the full amount.

Then because what you just did erased all of your GRUB data, you will boot to the Super Grub disk and choose the option to restore the Windows boot loader.  It's been a while, and I don't remember exactly where it is in the menus, but you'll find it.

When I went through this a while back, all of the fixmbr and other commands didn't work anyway.  Super Grub was the only thing I found that worked.

---

### Post by mahela007 on 2008-03-20
ok thanks. I'll try that

---

### Post by mahela007 on 2008-03-20
Just one more question.
what if I reinstalled ubuntu?
that is in the following way.
 Boot form the live cd. 
 use the partitioner and delete the partition of linux that is already on my computer.
 then without turning the computer of i reinstall ubuntu from the live cd
 will that prevent the GRUB form messing itself up?

(I have  a few problems with ubuntu. thats why I want to reinstall it)

---

### Post by forrestcupp on 2008-03-21
So you don't want to get rid of Ubuntu, you just want to reinstall?  Wow.  That changes everything.  If that is the case, you don't need to do anything we've said.

You just need to rerun the Ubuntu installation CD.  When it gets to the partitioning part, choose Manual partition.  Select the partitions you want to use for Ubuntu and make sure it is set up to mout as '/' or root, and also if you have a separate /home directory, make sure the partitioner is set to mount it as /home.  Then you can check the box next to your Linux partitions that says 'format' to format them and reinstall to those partitions.

When you reinstall Ubuntu, it will automatically reinstall GRUB and set it up correctly for you.  You won't have any conflicts.

---

### Post by mahela007 on 2008-03-21
wooow! thanks !!!

by the way i like your avatar. I USED to be an indiana jones fan when i was about 11. still like the movies though

---

### Post by forrestcupp on 2008-03-22
> **mahela007 said:**
> I USED to be an indiana jones fan when i was about 11. still like the movies though
I'll always be a fan.  I saw Raiders of the Lost Ark in the theater when it came out.  I can't wait for the new one to come out in a couple of months.

---

