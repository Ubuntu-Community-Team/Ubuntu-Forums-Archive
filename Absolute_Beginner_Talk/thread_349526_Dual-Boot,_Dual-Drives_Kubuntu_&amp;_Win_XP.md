---
title: "Dual-Boot, Dual-Drives Kubuntu &amp; Win XP"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by blocks885 on 2007-01-30
Ok everyone, I understand this post may already be on here somewhere, but I have had no luck finding a forum thread that would solve this so unfortunately I may have to repost and I would appreciate it if someone walked me through it here. 

Through my research I have found the best way to dual-boot is with two separate drives, one for Windows XP and one for Kubuntu Linux, and also make the Windows the Master and Kubuntu the slave.  I have also found that installing GRUB will mess things up, and I found that out the hard way; it was a tip to not install GRUB during setup and then go back and set it up.  But that's my problem.

I have 3 drives, the 3rd drive is 80gb IDE on a ATA/133 PCI card just as extra storage, I'd like to be able to use this but have disconnected this for most of the time until I figure this out since it really doesn't play a factor in this installation.

My 1st drive is 250gb IDE and I would like to set it as master since it has Windows XP loaded on it.  My 2nd drive is 200gb IDE and it has a 10gb partition with Kubuntu Linux and a 2nd partition formatted fat32 with my 60gb of music.  (I do not want to lose ANYTHING!!!)

Right now in order to start in linux I have to disconnect the 1st drive (Windows) and connect the 2nd drive (Linux) as master and it's all fine; however, I can not access my music or the movies on my windows drive.  I would really like to have all the drives connected and have a choice of which OS to run, however I'm just a beginner, in college too, so I don't have much time to thoroughly research the internet.  I know there are a few things out there but it's very mixed.  I know the best thing so far I've seen is making Windows master and Linux slave and it's fine.  When I first installed it, I had so many problems and wound up losing all of "My Documents" off of the Windows drive.  I really wouldn't like that to happen again...  

Can anyone walk me through all of this and help me? ASAP!

Thanks!

---

### Post by sonny on 2007-01-30
Perhaps [this]("http://www.ubuntuforums.org/showthread.php?t=179902") how-to will help you, an other [how-to.]("http://www.ubuntuforums.org/showthread.php?t=24113") Or [this]("http://www.ubuntuforums.org/showthread.php?t=275728") one.

---

### Post by blocks885 on 2007-01-30
I was just wondering if someone can answer my specific question, those how-to's seem to be in the middle.  I noticed I can reinstall GRUB since the Kubuntu is on slave and Windows on master.. So I disconnect Windows so that I'm running Kubuntu itself..I reinstall GRUB how??!?!????  Then once I reinstall GRUB then what?? 

*Still confused* and would rather be responded here rather than trying to read another forum since it's not specific...any help would be greatly appreciated!!!

---

### Post by sonny on 2007-01-30
Well... I could jut copied the thread over my answer... would that make a difference?, I know that being new is hard, but if you get stuck in one step you can always ask... we are here to help... if there's something you don't understand you can ask, but the steps you have to follow are those in the how-to.

---

### Post by blocks885 on 2007-01-30
Okay.  I don't understand how to install grub.  I have a dual-drive setup.  It says to install grub to your linux drive.  Do I keep the windows drive disconnected?  I can't follow the instructions to install grub to the linux drive.  Do I run it off the install cd, and if so, how?  Or do I boot from the linux cd and do it from there?

Next, once grub is installed, can I reconnect my windows drive and should it see the windows drive and all work out?

---

### Post by sonny on 2007-01-30
Well... if you are following the first guide, then you sould let the win drive disconneted, if you want to restore it from the live cd, then you should conect both drives.

Once you restore grub, you'll be able o dual boot without having to take your HD's out.

---

### Post by sonny on 2007-01-30
You should READ the 3 how-tos, and try to see if you understand them, after you finish reading them, you have to decide which one you think is easier to follow, if you find them equally hard, then I suguest you to follow the live-cd one, I think that is the esiest way, but you have to decide for one.

---

### Post by blocks885 on 2007-01-30
Okay--so I've made progress, just a little bit of help if someone doesn't mind...

I now have Kubuntu as master, Windows as slave (how it should be ;-) )

I installed Grub with the Super Grub cd and I've edited it -- however it gives me an error when I choose Windows XP that "ntldr is missing"... I'm confused... I'm going to paste in my fdisk -l results here and the menu.lst addition i added, and maybe someone can tell me what I've done wrong?

Disk /dev/hdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1216     9767488+  83  Linux
/dev/hdc2            1217       24321   185590912+   5  Extended
/dev/hdc5            1217        1398     1461883+  82  Linux swap / Solaris
/dev/hdc6            1399       14453   104864256    7  HPFS/NTFS
/dev/hdc7           14454       24321    79264678+   7  HPFS/NTFS

Disk /dev/hdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        4295    34499556    7  HPFS/NTFS
/dev/hdd2            4296       30401   209696445    5  Extended
/dev/hdd5            4296       30401   209696413+   7  HPFS/NTFS

Disk /dev/hdg: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1   *           1        9729    78148161    7  HPFS/NTFS


My linux drive is hdc and then I have a fat32 partition there hdc7.  And my windows drive is hdd1 (i believe).  My drives are set up as follows:
200Gb drive: 10Gb linux 1.5Gb swap and the rest to fat32
250Gb drive: 35Gb or so Windows and the rest to storage (NTFS format)
80Gb drive: on a ATA/133 card as more storage.

My Grub edit under menu.lst looks like this:

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
### BEGIN AUTOMAGIC KERNELS LIST

Can someone help--?? Thanks!

---

### Post by confused57 on 2007-01-31
Your Windows grub entry looks like it should work...leave your system set up as Linux on master controller & Windows on slave controller, just as you have it.
What you might want to try is going into bios and make sure the hard drive boot order is:
Linux Drive as first boot hard drive
Windows Drive as 2nd
Storage drive as 3rd(may not have to set this, but shouldn't hurt anything)

I don't know if this will work, but worth a shot.  I assume you can still boot Windows when connected to the master controller.

---

### Post by blocks885 on 2007-01-31
The bios settings are right, the linux drive 1st, windows drive 2nd...

I can boot into linux just fine, it's actually what I'm using... When I try to use windows it gives that error message "ntldr is missing" ... I was wondering if it's because I have to add linux to the c:/boot.ini???  Or do I have to add something from windows to Linux???

---

### Post by confused57 on 2007-01-31
> **blocks885 said:**
> The bios settings are right, the linux drive 1st, windows drive 2nd...

I can boot into linux just fine, it's actually what I'm using... When I try to use windows it gives that error message "ntldr is missing" ... I was wondering if it's because I have to add linux to the c:/boot.ini???  Or do I have to add something from windows to Linux???

I suppose this means you're unable to boot Windows when connected to the master controller...if that is the case you'll need to use your Windows install cd(not a recovery cd) and repair the mbr and ntldr, see Herman's response at the end of this thread:
[http://www.ubuntuforums.org/showthread.php?t=349778](http://www.ubuntuforums.org/showthread.php?t=349778)


Also, here's some excellent information from Herman's site on repairing Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

If you're able to boot Windows when connected to the Master controller, then the above wouldn't apply, we'd need to look elsewhere for a solution.

And you can't  boot Windows, using the Super Grub Disk?

---

