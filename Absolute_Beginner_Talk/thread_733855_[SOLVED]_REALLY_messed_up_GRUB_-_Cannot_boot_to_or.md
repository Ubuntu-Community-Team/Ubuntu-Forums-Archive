---
title: "[SOLVED] REALLY messed up GRUB - Cannot boot to or see XP Partition"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by gams on 2008-03-24
Hey Everyone,

I've really done it now! ;D

I'm prettty new to ubuntu and I've royally messed up my grub menu.lst file since it appeared as though my NTFS partitions and hard drive have disappeared, and XP no longer was a boot option in grub (after much beginner unguided attempts to use every option in super grub disk - may have even messed up the mbr).  I cannot mount to my NTFS drives/partitions or boot into windows.  I've reinstalled kubuntu & ubuntu many times, but that didn't help.

I've solved simple error 17 problems before by fixing the order of the hard drives in the BIOS, but I'm afraid I've gone well past those simple problems into panic zone that I may have just lost all of my pictures on my XP partition.  I wish I never downloaded the super grub disk.

Anyway, here are some details.  I did a '[COLOR="DarkRed"]**_sudu fdisk -_**[/COLOR]l' and you can see the results below. I could have sworn that the 'HPFS/NTFS' items used to be 'NTFS' before but I could be wrong.

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x388f388f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24320   195350368+   7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x014ca97a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           12985       17847    39062047+  83  Linux
/dev/sdb2             487       12984   100390185   83  Linux
/dev/sdb3   *       17848       48641   247352805    7  HPFS/NTFS
/dev/sdb4               1         486     3903763+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x143d143c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4865    39078081   83  Linux

*******************************************************************

my /boot/grub/menu.lst file at one point didn't have any entries for windows (like it did in the past when everything was working nicely).  Now I've just tried to cut and paste various suggestions I've seen in posts (changing the drive reference information) to no avail.  I've seen error 13, error 8, error 11, error 27, and my personal favourite GRUB Geom error which I saw quite a bit.

Now I will say that I've had the system working great for a while with 7.10 with the same partition scheme, so the BIOS, hardware and size of partitions are all okay.

*******************************************************************

I know this is a long email and I will probably have to chat with someone back and forth to help fix this, but I'm pretty worried that I really screwed things up.  I am hopeful that all my data is not lost because I never explicitly instructed the system to reformat the NTFS drives.

Hopefully there is someone out there with enough expertise to solve this problem.  Thanks. 

Gams.

---

### Post by penguinpi.com on 2008-03-24
Dude, Super GRUB

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

it's a live CD so you can install/reinstall GRUB. Try it out

---

### Post by forrestcupp on 2008-03-24
> **penguinpi.com said:**
> Dude, Super GRUB

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

it's a live CD so you can install/reinstall GRUB. Try it out
I would say the same, but he already tried all of the options in Super Grub.

Post your menu.list contents so we can see what you have.  You have 2 NTFS partitions.  Which one is Windows on, sda or sdb?

---

### Post by Sef on 2008-03-24
Here's ["How to Install GRUB in 3 Steps"]("http://supergrub.forjamari.linex.org/?section=documentation#grub_restore") with SGBD.

---

### Post by kolisikepu on 2008-03-24
alternatively... make a Ubuntu boot disk and restore MBR with the Windows XP installation disk.

Restoring MBR will restore windows Master Boot Record and remove Grub, hence why I've asked to create a Ubuntu boot disk so you can boot back into your Ubuntu installation and restore/fix Grub again.

---

### Post by ex-navy on 2008-03-24
Did the same yesterday.

Insert Win XP CD, wait until it asks to repair, install, blah blah blah.

Press R, hit enter

Type FIXMBR

Pull out CD, reboot.

Back to Windows.

Check out your disks in Control Panel, Administrative Tools, Computer Management, Storage.

You can add, delete partitions, etc.

I created free space by deleting a logical drive I did not use. Ubuntu will use this to install ext 3 partition.

Always do the guided steps.........

---

### Post by adrian15 on 2008-03-25
> **gams said:**
> Hey Everyone,

Hi
> **gams said:**
> 
I've really done it now! ;D

I'm prettty new to ubuntu and I've royally messed up my grub menu.lst file since it appeared as though my NTFS partitions and hard drive have disappeared,

Did you remove them... or did they disappear misteriously?
> **gams said:**
> 
and XP no longer was a boot option in grub (after much beginner unguided attempts to use every option in super grub disk - may have even messed up the mbr).

Which options have you used?
Did you try **Boot Windows from second hard disk**?
> **gams said:**
> 
  I cannot mount to my NTFS drives/partitions or boot into windows.

SGD might help you to boot into windows but I think it cannot compromise your NTFS drives so it might be another problem.
> **gams said:**
> 
I've reinstalled kubuntu & ubuntu many times, but that didn't help.

I see.
> **gams said:**
> 
I've solved simple error 17 problems before by fixing the order of the hard drives in the BIOS, but I'm afraid I've gone well past those simple problems into panic zone that I may have just lost all of my pictures on my XP partition.  I wish I never downloaded the super grub disk.

There are some problems that SGD can't solve because it is not perfect, maybe Rescatux will be perfect but we will have to wait for it. I doubt that SGD has damaged your data. 
Sometimes is BIOS order is incorrect you can use the **EASY LIVESWAP** option at SGD quick menu (or the more advanced liveswap options at Boot & Tools menu) and then go into Windows -> Boot Windows and check how your system actually boots.


> **gams said:**
> Anyway, here are some details.  I did a '[COLOR="DarkRed"]**_sudu fdisk -_**[/COLOR]l' and you can see the results below. I could have sworn that the 'HPFS/NTFS' items used to be 'NTFS' before but I could be wrong.

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x388f388f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24320   195350368+   7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x014ca97a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           12985       17847    39062047+  83  Linux
/dev/sdb2             487       12984   100390185   83  Linux
/dev/sdb3   *       17848       48641   247352805    7  HPFS/NTFS
/dev/sdb4               1         486     3903763+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x143d143c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4865    39078081   83  Linux


In your particular case I would try the Windows -> Windows (Advanced) -> Boot Windows from another hard disk and try to find the hard disk where Windows is which I bet it is the third one but it is only a bet.

**If you go to Boot & Tools -> Show Partitions and tell us what you find in hd0, hd1 and hd2 menues. This will help me a lot to give you the right SGD option and thus a solution**


> **gams said:**
> 
my /boot/grub/menu.lst file at one point didn't have any entries for windows (like it did in the past when everything was working nicely).  Now I've just tried to cut and paste various suggestions I've seen in posts (changing the drive reference information) to no avail.  I've seen error 13, error 8, error 11, error 27, and my personal favourite GRUB Geom error which I saw quite a bit.

I do not like a lot of the howtos that are found on the web. They pretend you can boot Windows with the root (hd0,0) command, in fact you should use rootnoverify (hd0,0).
> **gams said:**
> 
Now I will say that I've had the system working great for a while with 7.10 with the same partition scheme, so the BIOS, hardware and size of partitions are all okay.

Something has happened to Windows then.
> **gams said:**
> 
I know this is a long email and I will probably have to chat with someone back and forth to help fix this, but I'm pretty worried that I really screwed things up.  I am hopeful that all my data is not lost because I never explicitly instructed the system to reformat the NTFS drives.

When you said before that you could not mount the ntfs partition... did you mean not mounting it from the live cd or from your system.
> **gams said:**
> 
Hopefully there is someone out there with enough expertise to solve this problem.  Thanks. 

I am trying to help you. If you are right (which I doubt) there is a bug somewhere in SGD that screws systems and I should fix it. :).

adrian15

---

### Post by kolisikepu on 2008-03-25
I think it's best that he starts his Ubuntu venture again with a clean install.  I think he's panicing that his Windows no longer bootable, hence why I've suggested to fixmbr via Windows repair disk.  I think that's more his worry, just getting back to Windows.

---

### Post by adrian15 on 2008-03-25
> **kolisikepu said:**
> I think it's best that he starts his Ubuntu venture again with a clean install.  I think he's panicing that his Windows no longer bootable, hence why I've suggested to fixmbr via Windows repair disk.  I think that's more his worry, just getting back to Windows.

If we have to advise him to fix windows and the recover grub with super grub disk then some more commands than fixmbr are needed in my opinnion, maybe a system restore.

However I still would try to boot its windows from SGD... we can either find what are the right commands for its menu.lst, we can find if the BIOS offers the windows hard disk for booting or not (maybe the hard disk is not connected ok) and we can find which Windows error is displayed when booting.

adrian15

---

### Post by gams on 2008-03-25
> **kolisikepu said:**
> I think it's best that he starts his Ubuntu venture again with a clean install.  I think he's panicing that his Windows no longer bootable, hence why I've suggested to fixmbr via Windows repair disk.  I think that's more his worry, just getting back to Windows.


Thank you all for your suggestions.  I was finally able to spend a bit more time on this tonight and I'm happy to report that it was successful.

I removed all of the hard drives that were not being used and then I took the suggestion to attempt to FIXMBR from the windows recovery CD (I actually tried this part soon after I read the post).  When I was in C:\ and tried to list the contents of the directory, I couldn't see anything.  Tonight I typed 'help' while in the XP recovery mode and saw a command 'FIXBOOT' along with FIXMBR, so I tried them both and that seemed to work as I could then see the contents of the disk.

I rebooted and everything was there.  Next I added my other drives back (ones with the pictures) and rebooted and all is well in the universe again.

Thank you all so much for your suggestions.  I'm going to go buy a big drive where I can back up all my important stuff, then perhaps after attempt to install ubuntu again.

Really appreciate all of the posts.....that FIXMBR was sweet!

Cheers,

Rob.

---

### Post by kolisikepu on 2008-03-25
> **gams said:**
> Thank you all for your suggestions.  I was finally able to spend a bit more time on this tonight and I'm happy to report that it was successful.

I removed all of the hard drives that were not being used and then I took the suggestion to attempt to FIXMBR from the windows recovery CD (I actually tried this part soon after I read the post).  When I was in C:\ and tried to list the contents of the directory, I couldn't see anything.  Tonight I typed 'help' while in the XP recovery mode and saw a command 'FIXBOOT' along with FIXMBR, so I tried them both and that seemed to work as I could then see the contents of the disk.

I rebooted and everything was there.  Next I added my other drives back (ones with the pictures) and rebooted and all is well in the universe again.

Thank you all so much for your suggestions.  I'm going to go buy a big drive where I can back up all my important stuff, then perhaps after attempt to install ubuntu again.

Really appreciate all of the posts.....that FIXMBR was sweet!

Cheers,

Rob.

Rob... 

Good to hear FIXMBR helped.  Honestly, Ubuntu is awesome if you can get working right.  Hardy should make life alot easier for alot of us too.

Can you please mark your thread as solved. :popcorn:

---

