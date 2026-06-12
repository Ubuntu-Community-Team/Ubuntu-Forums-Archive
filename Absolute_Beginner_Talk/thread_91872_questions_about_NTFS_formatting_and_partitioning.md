---
title: "questions about NTFS formatting and partitioning"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by zexoc on 2005-11-18
At the moment my win xp professional system has 2 ntfs partitions, on a 40gb harddisk: C drive is 23.5gb and D drive is 14.7gb.

do I need to repartition? from what I've read 14.7gb should be enough for Ubuntu.

even though the D drive is empty as far as windows explorer is concerned, My Computer shows it as: Total Space 14.7gb , Free Space as 14gb. 
What is 700mb used for?

Can I install Ubuntu 5.1 onto the ntfs D drive, or does it need to be reformatted into fat32 for Ubuntu to install?

Does Ubuntu automatically install GRUB (which I'm guessing is a dual boot loader)?

Lastly

On [this](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html)  page the 15th image down shows that the hard disk has been partitioned into 3,  the final partition #5 logical is 423.1mb is **swap**. What is **swap**?

Thanks in advance for any replies/experiences.

---

### Post by xmastree on 2005-11-18
[QUOTE=zexoc]do I need to repartition? from what I've read 14.7gb should be enough for Ubuntu.

Can I install Ubuntu 5.1 onto the ntfs D drive, or does it need to be reformatted into fat32 for Ubuntu to install?
[/QUOTE]You would be best to remove the secondary partition completely, and ubuntu will install itself there. 14GB is plenty, mine is installed in a 10GB partition.

If you wish to share files between the two, you will need a FAT32 partition somewhere. Perhaps make a 4GB FAT32 which will be d: and install ubuntu in the remaining 10GB.

---

### Post by rpaller on 2005-11-18
[QUOTE=zexoc]At the moment my win xp professional system has 2 ntfs partitions, on a 40gb harddisk: C drive is 23.5gb and D drive is 14.7gb.

do I need to repartition? from what I've read 14.7gb should be enough for Ubuntu.

even though the D drive is empty as far as windows explorer is concerned, My Computer shows it as: Total Space 14.7gb , Free Space as 14gb. 
What is 700mb used for?

Can I install Ubuntu 5.1 onto the ntfs D drive, or does it need to be reformatted into fat32 for Ubuntu to install?

Does Ubuntu automatically install GRUB (which I'm guessing is a dual boot loader)?

Lastly

On [this](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html)  page the 15th image down shows that the hard disk has been partitioned into 3,  the final partition #5 logical is 423.1mb is **swap**. What is **swap**?

Thanks in advance for any replies/experiences.[/QUOTE]

Swap is equivalent to the paging file or swap file used by Microsoft Windows. It is used to place the memory footprint of inactive (sleeping) processes/programs so active programs have access to the RAM they need. In Ubuntu your swap file is generally 1 - 1.5 times the amount of RAM in your computer.

Ubuntu, and Linux in general, can only read NTFS partitions

If there is nothing on your 14.5 GIG D: partition/drive I would use that for Ubuntu. I would split it up as follows:

500MB - 1GB for swap
5 - 10 GB for Ubuntu (ext3 default file system for Ubuntu)
Remainder as FAT32 to provide read/write shared space for Windows and Ubuntu.

Ubuntu will install GRUB and it should detect your Windows installation.

The 700MB "missing" may be consumed by your paging file for Windows, recycle bin, and possibly restore points for system recovery.

---

### Post by zexoc on 2005-11-18
Is swap something the ubuntu installer installs automatically or does it need to be done manually?

xmas tree:

ok, how would I remove the secondary partition or split the secondary partition into 2: one 10 gb the other 4gb, can the **qtparted** utility on System Rescue CD be used for that?

also would I need to format D drive in order to repartition? and into what file system?

thanks

---

### Post by zexoc on 2005-11-18
ok I think I'd need 4 partitions:

1 23.5gb, existing C Drive NTFS running Win XP Pro
1 10gb, D **?** drive Ubuntu 5.10
1 4.5gb, E **?** drive partition to be shared by Ubuntu and Windows 
1 768mb swap

and somehow dual boot the WinXP and Ubuntu partitions?

---

### Post by xmastree on 2005-11-18
[QUOTE=zexoc]xmas tree:
ok, how would I remove the secondary partition or split the secondary partition into 2: one 10 gb the other 4gb, can the **qtparted** utility on System Rescue CD be used for that?[/quote]I would use fdisk. I'm not farmiliar with qparted. There's also an option in the comtrol panel, under computer administration > storage (I think) which may be easier.
> would I need to format D drive in order to repartition? and into what file system?Drive D is (presumably) a logical drive in the secondary partition. It will disappear when you remove the partition. There will then be 14GB unpartitioned space. Create a 4GB partition and create a logical drive within it. This will be your new 4GB drive D and should be formatted as FAT32.
Ubuntu installer will then give you the option to install in the remaining space. Take that option and accept its suggestion for automatic partitioning.
Don't worry about the swap, it wil all be done automatically.

Manual partitioning can be more effective if you know what you are doing, but the automatic option is more suited to new users.

---

### Post by zexoc on 2005-11-18
[QUOTE=xmastree]Drive D is (presumably) a logical drive in the secondary partition. It will disappear when you remove the partition. There will then be 14GB unpartitioned space. Create a 4GB partition and create a logical drive within it. This will be your new 4GB drive D and should be formatted as FAT32.
Ubuntu installer will then give you the option to install in the remaining space. Take that option and accept its suggestion for automatic partitioning.[/QUOTE]

do I need to format D which is now empty except for the 700mb ?

**1.** ok pardon my noviceness, but once I remove partition D, am I right in guessing that the whole of the 40gb harddisk will be ntfs ?

**2.** Once I create a 4gb partition and create a logical drive within it, as in step 1. that will leave(i'm guessing) my c drive with a 36gb ntfs partition how will ubuntu be able to install onto that?

---

### Post by xmastree on 2005-11-18
[QUOTE=zexoc]**1.** ok pardon my noviceness, but once I remove partition D, am I right in guessing that the whole of the 40gb harddisk will be ntfs ?[/quote]No. Drive C will remain as it is now, 23.5GB. The remaining space will be unused. Blank in other words. That's not the same as an empty drive.

Here's an analogy:
Imagine your drive is a big sheet of blank paper, and it's 40 square inches in area. Each square inch represents 1GB. Right now you have a line drawn across it dividing it into 23.5 and 14.7 sq in.
Each section is filled in with tiny squares, like graph paper. Those are your 'drives'.
I'm suggesting you erase all the squares in the 14.7 section and draw another line across it, dividing the 14.7 into 4 and 10 (don't worry about the .7, that's the width of the line... :-) ) Then format the 4GB (put the squares back in) and leave the rest blank for ubuntu to use as it wishes.

Hopefully that makes it clear without sounding too patronising. :rolleyes:

---

### Post by zexoc on 2005-11-18
i managed to partition and install Ubuntu, thanks for the help xmastree and rpaller.

on first go, it is a very nice gui, it takes a bit longer than xp professional to boot up tho.

i'm glad it managed to recognise my usb flash disk without any drivers.

---

### Post by xmastree on 2005-11-18
Excellent! :) :) :) 

Were you able to mount your Windows partitions too?

Next thing is to [read this]("http://www.ubuntuguide.org/") to learn how to set it all up to your liking.

---

### Post by zexoc on 2005-11-18
i'm not sure what 'mount' means but the grub loader allows me to boot up windows xp as well.

the only thing is that i cant seem to find that 4 fat32 gig partition aka drive d:, all it shows in computer is floppy cdrom and filesystem.

---

### Post by rpaller on 2005-11-18
Can you open a terminal window and execute the following:

```
sudo fdisk -l /dev/hda
```

sudo allows you to run a command that requires "super user" or "root" level permission. It will likely prompt you for a password, which should be the password you entered for your personal user account.

And then copy and paste the results here? It should look similar to this:

```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
16 heads, 63 sectors/track, 116280 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       60945    30716248+   7  HPFS/NTFS
/dev/hda2           60946      113970    26724127+  83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hda3          113970      116280     1164712+   5  Extended
Partition 3 does not end on cylinder boundary.
/dev/hda5          113970      116280     1164681   82  Linux swap / Solaris


```

You may need to modify a config file named fstab found in /etc which tells your system which partitions to mount (attach) to when the system boots. 

You will want to make sure that Windows is able to see this partition and actually use Windows to format it. Windows is sensitive about who touches the disk first, but that is another discussion in another thread.

---

