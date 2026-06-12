---
title: "hard drive issues"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by metalfanatic07 on 2007-04-07
I have an 80 Gb main drive (SATA if it matters) that I run Ubuntu 6.06 off of. I want to install a 2gb IDE drive to run Win 98/xp off of, but linux refuses to let me format the drive, or my computer won't recognise it at all. I've tried different jumper settings, plugging it into the other plug, and it won't solve my problem. Will this happen when i get my second SATA drive or will that one have the same problem and how do i fix it?

---

### Post by overdrank on 2007-04-07
> **metalfanatic07 said:**
> I have an 80 Gb main drive (SATA if it matters) that I run Ubuntu 6.06 off of. I want to install a 2gb IDE drive to run Win 98/xp off of, but linux refuses to let me format the drive, or my computer won't recognise it at all. I've tried different jumper settings, plugging it into the other plug, and it won't solve my problem. Will this happen when i get my second SATA drive or will that one have the same problem and how do i fix it?

I sure hope not! I have had the same problem with my new sata drive and I tried to install windose on a separate drive ide and had some much trouble I gave up on windose. I have now there partition on my new drive one for Kubuntu, dapper, and edgy and I am totally happy with that.But I will be installing another sata drive tomorrow and I hope I have no problems. :guitar:

---

### Post by cantormath on 2007-04-07
> **metalfanatic07 said:**
> I have an 80 Gb main drive (SATA if it matters) that I run Ubuntu 6.06 off of. I want to install a 2gb IDE drive to run Win 98/xp off of, but linux refuses to let me format the drive, or my computer won't recognise it at all. I've tried different jumper settings, plugging it into the other plug, and it won't solve my problem. Will this happen when i get my second SATA drive or will that one have the same problem and how do i fix it?

I am limited to dual booting, I have only done it with linux and linux.  But I think when you dual boot windows with linux, you need to install windows first.  I would recommend making a windows partition, then installing win98 on vmware.  You can use Qmu or something so you do not need to buy the vmware server and the vmware player is free.

This is the kinda of tutorial I mean
[http://ubuntuforums.org/showthread.php?t=342631&highlight=vmware+on+dapper](http://ubuntuforums.org/showthread.php?t=342631&highlight=vmware+on+dapper)

---

### Post by e_james on 2007-04-07
There are 2 separate issues here. 

First to get the drive working. Three questions.
1. Is the drive hardware functioning? A 2GB dive is old enough to have died of old age while sitting on the shelf. Even if it spins, it might still have failed.

2. Does the BIOS recognise the drive?

3. Will the relevant OS software recognise the drive? If the first 2 answers are 'yes' then I would expect this one to be 'yes' too but it's not 100% certain.

When I have had these sorts of problems in the past I have tried various ways of testing the drive such as single drive or master or slave. I have also tried installing the drive in one or more external usb cases.

Second to set up one or two drives for multi booting.

If I was planning to install Windows 98, Windows XP and Linux on a drive of about 60GB, this is roughly what I would do.

Using Partition Magic or Gparted I would create 3 primary partitions.
1 - about 100MB for Linux '/boot' if I want to use it that way.
2 - about 500MB for Windows 98. W98 only needs about 250MB for installation. If more room is needed for additional applications, they can be installed on other drives.
3 - about 5 to 10 GB for Windows XP. Windows XP needs at least 2GB for installation. I have done it in 2GB but it was very tight.

To minimise complications I would only format the XP partition and install it first. XP is aware of other partitions and will attempt to integrate 98 into the installation if it is present. It will ignore linux ext2, ext3 and swap partitions as unknown formats.

Next to install Windows 98. Format the 98 partition (FAT32) and set it active. W98 installer won't notice any other partitions.

Note: I rely on independent boot managers such as Boot Magic or Grub to select the OS to boot.

Next, to finish partitoning, I would create an extended partition in the remaining space and then further logical partitions within this space. There are various opinions on the size and allocation of linux partitions but 500MB to 1GB for 'swap', 5 to 10 GB for '/' and the same for '/home' is workable. The remaining space would be formatted (probably in one piece), as FAT32 for easy exchange of files between the different OSes.

Finally I would install Ubuntu and Grub would be configured to boot whatever OS I want.

In the case of 2 drives. (I can't speak for virtual PCs). I believe that W98 must boot from the first drive. XP also expects to boot from the first drive but I think there are ways around this. I haven't tried it, but Grub might be able to boot Windows from the second drive.

I know Ubuntu will boot from a second drive, but the boot sequence starts with the MBR of the first drive.

Please feel free to interpret any of the above suggestions according to your own requirements.

Note: I have 4 PCs set up for multi booting, 2 of them configured pretty much as described above, and another running 1 windows and 2 linux.

---

### Post by LaurelLynn on 2007-04-08
Dear metalfanatic07,

My experience with trying to add an SATA drive and an ATA drive to the same system, is that the controllers on the motherboard seem to use the same resources. That makes it a bios issue. Your motherboard manufacturer might have an update with a workaround for the problem.  It is probably simply that by the time all the components are plugged in, there aren´t enough resources left to go around.

Laurel Lynn

---

### Post by metalfanatic07 on 2007-04-08
I would really rather not re-format the 80gig drive as i already have my entire music collection on it (waiting to order the 250 untill i get the money) so dual booting is out of the question. plus i have another computer set up dual booting with two seperate drives and it works just fine, which is what I want to do with my custom i built. problem is, the BIOS recognises the 2 gig drive and i know it works because i tested it in an older computer and wiped it clean. the issue is Ubuntu won't let me mount the drive and somehow my CD drive interferes with the hard drive. I plan on replacing the cd drive (again when i get the money) but I can't afford to go without one because i am in the process of transferring some important stuff from my dad's computer that i can't lose (which is why I can't re-format the main drive) And if space is an issue, I can yank a 14 gig drive out of the other computer (once i figure out how to remove grub so it will boot without the linux drive, which is what i wanted to do in the first place.

---

### Post by e_james on 2007-04-08
I have 2 PCs with ubuntu in dual boot which are capable of running sata drives but currently they have no sata drives installed. A third PC has 3 pata (ide) hard drives + 1 pata dvd writer + 2 sata drives all running happily but this one only has windows XP. Therefore I can't speak for ubuntu and sata. I am trying to think this through but, in the meantime, I have a suggestion. Try searching ubuntu and other linux forums (e.g. [www.linuxformat.co.uk](www.linuxformat.co.uk)) for the keyword 'sata' (probably you already have). You should be able to find out if ubuntu / linux has special requirements for sata drives.

I also have a question. What do you want to achieve by using the 2GB drive? I might be able to suggest an alternative configuration.

I just thought of something. First there was 'ide', then there was 'eide' and then there was '(p)ata'. They are all basically the same idea but, along with the name changes, there were enhancements in the technology. Your 2GB drive should be around 5 or 6 years old. Maybe the mix of old and new is part of the problem.

---

### Post by metalfanatic07 on 2007-04-09
> **e_james said:**
> 

I also have a question. What do you want to achieve by using the 2GB drive? I might be able to suggest an alternative configuration.

Maybe the mix of old and new is part of the problem.


I wanted to have a drive on there that i can put windows on to play games and stuff on. and to alleviate the linux and windows drives from not recognising each other, I am getting a 250 gig drive (sata) just for storage purposes. that way if it works like i think it should, both systems will be able to read and write to the "slave" drive (i know it's really not a slave)

as for the mix of old and new, I never thought about that causing a problem. I've done similar things with hard drives before mixing old and newer parts and never had a problem, but both of the drives have always been IDE.

---

### Post by metalfanatic07 on 2007-04-09
threw the hail mary and updated the BIOS, workd like a dream. installing XP as we speak

---

### Post by e_james on 2007-04-09
I don't know how much difference my comments actually made, but I am pleased to hear that you've got things sorted

---

