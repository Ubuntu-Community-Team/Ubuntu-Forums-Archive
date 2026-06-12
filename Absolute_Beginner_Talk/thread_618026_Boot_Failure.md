---
title: "Boot Failure"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by edge900rr on 2007-11-19
When I finish the install and remove the cd, I get the DISK BOOT FAILURE, PLEASE INSERT SYSTEM DISK.  I am on my third install with the same result.  I have my cd drive set to the first boot item and then the hd0 as the second.  any thoughts.  I have version 7.10

thanks
dave

---

### Post by Haluci on 2007-11-19
It could be that your install was corrupted due to a bad cd burn.  Reinstall ubuntu, trying these steps:

[LIST]
[*]md5 hash your downloaded iso file and compare it to the official [ubuntu md5 hashes]("https://help.ubuntu.com/community/UbuntuHashes") and be sure they match.
[*]when you burn to CD, choose "Check CD for defects" before you install
[*]try using the alternate CD image if the liveCD doesn't work
[/LIST]

---

### Post by edge900rr on 2007-11-20
what is the alternate cd?

---

### Post by edge900rr on 2007-11-20
I did do the md5 & the check cd for defects.  both were good.

---

### Post by siciliancasanova on 2007-11-20
The second half of [this page]("http://users.bigpond.net.au/hermanzone/") should explain the alternate cd for you.

---

### Post by edge900rr on 2007-11-20
those are only for version 7.04 and I have version 7.10.  is there a tutorial for 7.10?

---

### Post by popch on 2007-11-20
Judging by the error message, I would suspect that there is no operating system (or at least no boot record) on your fixed disk. Hence, the installation of Ubuntu Linux appears to have failed.

What did you do to install Ubuntu? How far have you proceeded? Were there any messages indicating that Ubuntu was successfully installed, or that Ubuntu failed installing?

Not knowing your level of experience it is quite hard to judge what went wrong. Please excuse if I suggest things you are perfectly aware of.

Installing Ubuntu using the liveCD takes the following steps (rough outline done from off the top of my head):
[LIST]
[*]insert the liveCD
[*]turn on the PC
[*]wait until an menu is shown
[*](depending on location, select keyboard and language)
[*]select 'Start or Install Ubuntu Linux' from the menu (or wait until the timer expires and Ubuntu starts of its own)
[*]Wait until Ubuntu Linux has completely loaded and displays the desktop
[*](***at this point in time, you are using Ubuntu Linux without having installed anything***)
[*]double click on install on your desk top (I suspect that you might not have done this)
[*]answer the questions (about Language, Time Zone, Partitions and such)
[*]Ubuntu now installs itself. Wait until it says that the installation is complete[/LIST]

---

### Post by edge900rr on 2007-11-21
I have used both the liveCD & the alternateCD.  everything appears to install properly.  The whole install finishes and I reboot (removing the install cd).  and I get the disk boot failure message.  I told Ubuntu to use the whole drive.  do I need to install something into the master boot record on the HD?  I am installing on a 10gb drive, pent III 900 with 373 ram.

---

### Post by popch on 2007-11-21
... falling back to guessing mode.

It appears that you did install Ubuntu, and that the BIOS can not detect or read it.

How many disk drives are in your Machine, and how many partitions to each?

What drive and partition did you install Ubuntu on? The correct answer looks something likethis:***  /dev/hda3.***
In case you are wondering why I ask those things: Linux 'names' and 'numbers' disk drives and partitions in your PC. The numbering and naming can be a little less than straight forward for people not familiar with the concepts involved.

---

### Post by edge900rr on 2007-11-21
I have one HD and a CD drive in the system.  I am not at home but I believe it puts it on /dev/hda0.  I tell it to use the whole drive.

---

### Post by monte48lowes on 2007-11-21
Just for fun, change the boot order in BIOS. 

Mike

---

### Post by monte48lowes on 2007-11-21
I am thinking something along the lines of this:

The BIOS is trying to send to the first disc. If the first disc is your CD-rom, with no CD loaded, the drive will report back to the BIOS that no disk is there. How are the IDE cables connected to the back of each drive (hdd and cd-rom)? Is there more than one IDE channel? Are the drives setup properly using jumpers on the back (master/slave/cable select)? Was there another OS installed on the computer prior?


Just some thoughts... don't know if they will help.

Mike

---

### Post by edge900rr on 2007-11-21
yes there was another os on the computer and it did work fine.  the hd is on ide1 and the cd is on ide2.  they are both set as masters.  bios is set to boot from the cd first and then the hd.  I have tried swapping that and it didn't help.

---

### Post by monte48lowes on 2007-11-21
There might be an issue with the MBR of the drive. Have you tried the [SuperGrubDisk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")?

Mike

---

### Post by edge900rr on 2007-11-21
no I haven't tried that one yet...I will when I get home and let you know.  thanks for the help

---

### Post by edge900rr on 2007-11-21
well, at first the grub disk wouldn't work.  I changed the hd jumper my my drive from master to cable select and that fixed it right away.  ubuntu boots right up.  weird...but thanks everybody for all the help

---

