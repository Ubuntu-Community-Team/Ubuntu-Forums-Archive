---
title: "Problem restoring an Acronis Image"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Scantabout on 2007-05-04
As an absolute newcomer to Linux & Ubuntu, any help resolving a problem concerning reinstating images of my Ubuntu partition using Acronis True Image 10 would be very much appreciated.

My problem is that after reinstating an Acronis image, Ubuntu won't run.

I have a multi boot situation with two Windows XP partitions + Ubuntu on the first drive, and Vista on the second, and use OSL2000 Bootmanager to select which operating system I want to boot. This boot manager requires that Grub be installed on the partition and not in the mbr.

After installing Ubuntu 7.04 (using the 'alternate' disk) everything worked fine and I could boot Ubuntu or any of the Windows partitions.  

Before proceeding to experiment with Ubuntu, I made an image of the partition using True Image 10, a program which has always worked very well for me.

I then decided to test the image by reinstating it - but found that after selecting Ubuntu from the OSL200 Bootmager menu, all I got was a blank screen with the cursor flahing in the top left corner (normally I would get the Grub menu at this point).

Disabliing OSL2000 with the Ubuntu partition set to active resulted in the message 'Missing OS'.

From my VERY limited knowlege, I assumed the problem was a corrupted Grub, and so after a Google search used two different methods - including using the 'Super Grub' disk - to reinstall Grub on to the partition; but all to no avail.

I've reinstalled Ubuntu several times, made several Acronis images, and reinstated them - but always with the same result :confused: 

Any help/suggestions would be most welcome - many thanks.

---

### Post by starcraft.man on 2007-05-04
Ummmm, firstly, I did a quick google and I am wondering why you would pay 25$ for a bootloader? You do know that [GAG]("http://gag.sourceforge.net/") exists, it supports almost every OS in existence I think.

As for Acronis, I have it and still use it to some extent, I'm looking for a opensource backup manager. As far as I know, as long as you imaged your entire hard drive, if you restore it it should be fine. I've done it plenty of times when I've screwed up my parition and I've never failed to boot into it. So, I can definitely tell you it has nothing to do with Ubuntu itself.

Can I recommend something? Back up any files with Ubuntu, and then reinstall it and this time let GRUB install on the MBR, or try GAG, I don't know anything about this program but I don't really think you should be paying to boot into Ubuntu. It should detect your windows partition and add it to the list, if it doesn't flash gag to your MBR and give it a shot with acronis.

---

### Post by Scantabout on 2007-05-04
Thanks for the comments.  As regards GAG, I tried it sometime ago and found that it wasn't suitable for my setup.  By the way, in my view, OS2000  is an excellent bootloader and well worth the $25.  Bear in mind that I'm basically a Windows guy and have only just started experimenting with Linux.  Prior to OSL I used BootMagic as my bootloader, but the advent of Vista put paid to that!

The Acronis images I make are, as is normal, of individual partitions and not the whole disk - bit much to back up a 500 GB drive when you only want a 15 GB partiition backed up. :)  All the individual windows partitions backed up this way always reinstate with no problems.

Did actually try the suggestion about installing GRUB on the MBR.  This wiped out the OSL bootloader, and didn't list all my windows partitions correctly (one XP partition was shown as being Vista).  Consequently, I didn't try doing an Acronis image of this to see if it would reinstate properly.

Any further suggestions from anyone would be very welcome!

---

### Post by menawollas on 2007-05-05
I have exactly(ish) the same problem and I do use GAG.

I installed Ubuntu on a logical partition. Created an Acronis Image. Restored the image. Tried to boot from GAG on a floppy, and it complained about an invalid partition Boot sector, or something like that (Grub should have been on the partition in question). 

Any thoughts?

---

### Post by Herman on 2007-05-05
Hello menawollas,
It doesn't make any difference whether we have Linux in a primary or a logical partition, Linux operating systems will still boot just as well, so don't worry about that.

GAG Boot Manager works by 'chainloading' the operating system by the boot sector which is the first sector of each partition.
By default Windows always installs an IPL for its bootloader, NTLDR, in the bootsector of its partition so you can always boot Windows with GAG very easily.

You can boot Ubuntu or other Linux with GAG Boot Manager quite easily too, but most Linux operating systems have an empty boot sector and install the IPL for their bootloaders to MBR by default instead. So when GAG looks at the boot sector for Ubuntu, nothing is there, because we have to do it ourselves and probably no-one did so yet.
It is quite simple to install the IPL for Grub or Lilo boot loaders to a Linux boot sector. 
Grub is the most popular. To install Grub to the partition you can use a Ubuntu 'Desktop' live CD or Knoppix, GParted LiveCD or any liveCD that has Grub in it.   You just type 'sudo grub' at a terminal, for a Grub prompt. ```
sudo grub
``` Then type 'find /boot/grub/stage1' to find out which partition(s) has/have Grub in it that you want to install somewhere. Grub's stage1 file contains the IPL for the Grub bootloader. ```
find /boot/grub/stage1
``` The answer should be like: (hd0,1) probably, but it could be (hd1,0) or some other disk number and partition number, counting from zero.
Then you need to tell Grub to focus or 'root' to that partition with a 'root' command, lets pretend it's (hd0,1),
```
root (hd0,1)
```Next you need to tell Grub where you want the stage1 file installed to. You can install it to the same partition's first sector, or to the hard disk's MBR, to another hard disk's MBR, to a floppy disk, or a USB drive maybe. You want to install it to the same partition's first sector right now, so here's the command,
```
setup (hd0,1)
```Now you should see some lines of information like:
```
grub> setup (hd0,1)
  Checking if "/boot/grub/stage1" exists... yes
  Checking if "/boot/grub/stage2" exists... yes
  Checking if "/boot/grub/e2fs_stage1_5" exists... yes
  Running "embed /boot/grub/e2fs_stage1_5 (hd0,1)"... failed (this is not fatal)
  Running "embed /boot/grub/e2fs_stage1_5 (hd0,1)"... failed (this is not fatal)
  Running "install /boot/grub/stage1 (hd0,1) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded
 Done.
``` That's it! :) 
Just type 'quit' to get out of the grub shell and back to your normal terminal prompt ```
quit
``` Then close your terminal and reboot.
Now you should be able to boot with GAG-Grub. (GAG will be your *boot manager* now, and Grub will be your *boot loader* that actually loads your Linux kernel into the RAM to boot up your system).

Regards, Herman :)

---

### Post by menawollas on 2007-05-06
Thanks for that, however I had (or thought I had) done just that, and installed grub on the linux partition. I had Gag working one minute, and then refusing to the next. 

I have a quad boot system, XP1 / XP2 / Vista /Ubuntu, and have just blown it all away and rebuilt it from scratch, repartitioning the disk, and now I have then all booting from Grub in the MBR, even after a restore of Ubuntu from Acronis, so the problem seems solved.

Just about to move grub to the partition, so we'll see what happens then !

---

### Post by starcraft.man on 2007-05-06
> **menawollas said:**
> Thanks for that, however I had (or thought I had) done just that, and installed grub on the linux partition. I had Gag working one minute, and then refusing to the next. 

I have a quad boot system, XP1 / XP2 / Vista /Ubuntu, and have just blown it all away and rebuilt it from scratch, repartitioning the disk, and now I have then all booting from Grub in the MBR, even after a restore of Ubuntu from Acronis, so the problem seems solved.

Just about to move grub to the partition, so we'll see what happens then !

Just curious but by XP1, do you mean service pack 1? Why would you need to have both service pack 1 and 2? Service pack 1 is very insecure now a lot of patches have been deemed SP2 only by microsoft. Just a thought.

Glad to know your problem is fixed.

---

### Post by menawollas on 2007-05-07
Nope not XP SP1

XP Partition 1 (Main Version)  XP Partition 2 (Clean version for using music software, as for some reason MIDI got f*cked on partition 1 - I blame the latest Audigy Drivers).

---

### Post by Del Piero on 2007-12-31
I have the exact same problem but i am using GRUB as the main boot-loader to boot both the windows partition and the Ubuntu partition which is using Lilo, Looking back when i first started during GRUB i remember the horror and the epic threads and countless problems i had with it so no thanks Lilo is the best for me. Anywho after restoring the Ubuntu partition after a failed try to upgrade from Edgy to Feisty ironically using Acronis i encountered the same error message from Grup (NO BOOT SECTOR), so can someone please tell me how to save the day using Lilo instead of grub?

---

### Post by Herman on 2008-01-01
:) Hello Del Piero, 
If you can boot into your system somehow, (use   [Super Grub Disk]("http://sgd.benjamin-butschko.de/") if you can't boot the normal way), you just need to run 'liloconfig'. That should fix it for you.
It is illustrated in the following link, skip the part about editing /etc/fstab since you are not installing for the first time, here is the link,  [Run Liloconfig]("http://users.bigpond.net.au/hermanzone/p4.html#Run_Liloconfig").

Regards, Herman :)

---

### Post by Del Piero on 2008-01-01
> **Herman said:**
> :) Hello Del Piero, 
If you can boot into your system somehow, (use   [Super Grub Disk]("http://sgd.benjamin-butschko.de/") if you can't boot the normal way), you just need to run 'liloconfig'. That should fix it for you.
It is illustrated in the following link, skip the part about editing /etc/fstab since you are not installing for the first time, here is the link,  [Run Liloconfig]("http://users.bigpond.net.au/hermanzone/p4.html#Run_Liloconfig").

Regards, Herman :)

Silly me, i was a bit drunk when i made the last post sorry for that. When i said i am using Grub as the main boot loader, i meant GAG. And i can't boot into my system, i don't know how to do that using the alternate CD or the Linux Rescue. But i will try the super GRUB disk anyway. Thanks for reply, and Happy New Year :).

---

### Post by Herman on 2008-01-01
Okay, Super Grub Disk should help you boot into your system, but if you're not using GRUB, you need to look for the option to 'Boot Linux Directly', which will boot your kernel via the symlinks.
If you try the other option in Super Grub DIsk it looks for your /boot/grub/menu.lst file and uses the information from that to boot with, but you won't have one of those if you haven't got GRUB installed.

Things have improved a lot with GRUB and booting up Ubuntu since the old days. I remember too. We still have a lot of posts asking questions about GRUB, but these days there are maybe between ten or one hundred times the number of installations being carried out every day, so most people are not having as much trouble with GRUB any more like they used to a couple of years ago.

adrian15's Super Grub Disk makes life a lot easier for most people too. That has helped a lot of people.

Regards, Herman :)

---

### Post by Del Piero on 2008-01-01
> **Herman said:**
> Okay, Super Grub Disk should help you boot into your system, but if you're not using GRUB, you need to look for the option to 'Boot Linux Directly', which will boot your kernel via the symlinks.
If you try the other option in Super Grub DIsk it looks for your /boot/grub/menu.lst file and uses the information from that to boot with, but you won't have one of those if you haven't got GRUB installed.

Things have improved a lot with GRUB and booting up Ubuntu since the old days. I remember too. We still have a lot of posts asking questions about GRUB, but these days there are maybe between ten or one hundred times the number of installations being carried out every day, so most people are not having as much trouble with GRUB any more like they used to a couple of years ago.

adrian15's Super Grub Disk makes life a lot easier for most people too. That has helped a lot of people.

Regards, Herman :)

Thanks, worked like magic and order is restored now a new problem, i don't have swap!!

---

### Post by Herman on 2008-01-01
A swap area is easy to make, you will need to use a Live CD, if you already have the Ubuntu Gutsy Gibbon Live CD you can use GParted Partition Editor in that to resize your Ubuntu partition a little smaller and make room for a swap area.
Then just make a swap area.
If you don't have the Ubuntu Gutsy Gibbon Live CD you can download [GParted -- LiveCD]("http://gparted.sourceforge.net/") and use GParted as a stand-alone live CD. It's not such a big download and it's very very handy.

You will need to register your new swap area in your /etc/fstab file. 
You can do that when you reboot and your hard disk operating system is running would be the easiest.
I imagine you know how todo that already, but if you need help just tell me and I'll give you more detailed instructions.

Regards, Herman :)

---

