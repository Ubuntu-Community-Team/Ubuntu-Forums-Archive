---
title: "New Install - cannot find slave drive"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-05-06
In my previous installation of Ubuntu, I loaded 6.10 onto a 160 GB drive.  I left my dual boot XP partition only 11 GB of space, figuring I would install only XP into that partition, then, install any XP applications into unused ntfs space on that drive or on the 320 GB slave drive that is also installed.

Soon enough, I found that Windows temp files were clogging the XP installation, even though I made a vain effort to direct all applications to store temp files elsewhere.

Long story short, I decided to move all important XP data off the master drive onto the 320 GB slave and reinstall Ubuntu and XP from scratch.

I figured installing XP first would be the best way to go, and I instructed XP to install on the C drive, but, when I clicked to execute the final step before actual install, XP instructed me that it was about to format D instead of C.  The screen previous clearly tells you to highlight your selection (mine was C not D) and press enter - but, each time I tried it, XP persisted in telling me that D would be formatted for the install.

Anyhow, I tried unplugging the D drive, but, my system would freeze during boot up (wouldn't allow me to boot to the XP CD).  

I gave up on the unplugged drive approach and decided to go ahead and install Ubuntu (7.04 this time), and deal with fixing the Grub after going back to install XP as the second OS.

Ubuntu's partitioning routine is so much simpler and direct.  I selected hda, set up my partitions, and installed.

One thing that puzzles me, however, is that my 320 GB drive does not show up in the new Ubuntu install as a drive.  If I open 'hardware manager', the drive shows up there as a slave, but it does not appear on my desktop.

What did I do wrong?

Caruso

---

### Post by jiminycricket on 2007-05-06
Try 'sudo fdisk -l' to see all the drives on your system.  You can also try installing ntfs-config from the universe repository and run ntfsfix to see if it detects it then. (although be careful about always unmounting when removing the drive if it's external)

BTW in my situations with this, I've found a way to fix XP seeing C as D is to set as hidden the partition that it sees as D from gparted, then you unhide it again.  I agree that the Windows system drives are very antiquated ways of dealing with things; I think it's mostly for backward compatibility though.  I think it froze because though windows saw it as d, (unless I'm misunderstanding which is very likely) was actually your master drive so you can't boot without it.

---

### Post by Tundro Walker on 2007-05-06
In the past (like in the past 5 years) you had to toggle some jumpers on the back of drives to set them to master/slave.  Perhaps your slave drive doesn't have its jumper in the right position?

Another case could be the IDE cable is plugged in in the wrong order (but I doubt that...I think jumpers make more of a difference then which plug on the IDE cable you use).  Your IDE / SATA cable could be going bad, though.  Maybe the plug you're putting into your slave drive is just crapping out on you.  You could try swapping out the one you use for your CD / DVD drivers and see if it fixes the issue.  If it does, then ditch that old cable and get a new one.

You can force Ubuntu to recognize slave drives inserting them into the "fstab" drive list.  You'd start by using...

```
 sudo fdisk -l
```

...(that's a lower-case L) to list all of your drives.  Then, open a terminal and type...

```
 gksu gedit /etc/fstab
```

(replace gedit with whichever text editor you prefer using).  Add  in an entry for the drive/partition you want.  EG: 

```
 /dev/hdb1   /mnt/win   (etc...)
```

I'm not 100% certain on the syntax you'd have to use, but a quick search of the forums for "fstab ntfs" should get you some good input on the subject.

To be honest, that's kinda been one of my beef's with Ubuntu.  When I swapped a hard drive from my old computer to my new one, Ubuntu didn't have a problem detecting all the new hardware.  However, it wasn't smart enough to figure out that the HD's place had changed from "hda1" to "hdc1" (I had put the 2 CD players as 1st master/slave pair, and the 2 HD's as 2nd master/slave pair without realizing it.)  My computer wouldn't boot up Ubuntu.  I had to LiveCD boot, correct the hard drive entries in /etc/fstab & /boot/grub/menu.lst, and then it would finally boot.  But, like I said, once I made those 5 second corrections, Ubuntu detected all the other new hardware (new sound card, motherboard, cpu, etc) without a problem.

Honestly, I'm thrilled with Ubuntu, but that one thing kinda annoyed me.  I mean, you can take an MS Windows driver, toss it into a new computer, and you don't have to worry about it wigging out about what order it is on the master/slave sequence...you just have to worry about loading all the stupid drivers for your new hardware.  But in Ubuntu, it'll load all the drivers no problem, but wigs out when it's changed location on the master/slave sequence.  Weird.

---

### Post by carusoswi on 2007-05-06
Either Ubuntu or Windows has corrupted the file system on that data drive.  As I posted earlier, Ubuntu cannot detect the drive at all, and if in XP, I go to MyComputer and right click the drive, it shows as RAW and full, no storage available, no data, etc.

If I used XP's device manager, it is shown as a 128 GB FAT16 partition.

I have downloaded GETDATABACK for NTFS and am scanning the drive now.  Expected files are showing up.

I'm wondeirng how this happened and what I might do to restore access the drive.

I find this very annoying (and I also need at least some of that data and would like to recover all of it - that's why I spent a couple of hours yesterday moving it all onto that drive.

Anyhow, thanks for the replies.  If you have any other recommendations, let me know.

I'm wondering if runing XP's fix MBR would help.

Thanks.

Caruso

---

### Post by carusoswi on 2007-05-06
Good news is that GetDataBack had no problems scanning and detecting the files on the drive.  I have copied the most important files back to the master (G - argh!) drive.

Now, I need to explore this forum to find out how to restore my grub so that I have a proper dual booting machine, then, I'll revisit this topic and see if I can figure out how to rescue that 320 gb drive (even if it's only for future reference).

Thanks for the replies - any additional comments welcome - especially info on why the drive would become RAW and unaccessible by either Ubuntu or XP.

Caruso

---

