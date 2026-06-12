---
title: "dual boot install prep - make partition before ubuntu install?"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by will m. on 2007-01-24
Hello!

I am doing my pre-installation homework and have found a particularly good resource (so far) at [http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm")

However, I have one question that I can't find the answer to there.  I want to create a dual-boot XP/Ubuntu drive.  To accomplish this I plan to reinstall XP to my laptop first.  During the XP installation process I was going to partition the drive (~80GB for XP and ~12 for Ubuntu).  Afterwards, I was going to use the 6.10 live CD to install Ubuntu on the remaining partition.  During the Ubuntu install process I would make the necessary additional partition for swap.

However, I can't see any examples of how that would work.   Am I better off just installing XP on the drive sans partitions and then letting the Ubuntu installer guide me through the partition decisions?

I am really new to Linux but am trying to be responsible and do my homework.  Any advice you have would be appreciated.

Regards,

Will M.

---

### Post by mikewhatever on 2007-01-24
You can either manually create swap partition of the size you want, or choose the 'Automatically partition the free space' option.

---

### Post by will m. on 2007-01-24
Thanks for responding!

So if I understand correctly, during the Ubuntu install selecting the "largest continuous space option" would by default select the 12GB partition I made during my XP install?

Will M.

---

### Post by mikewhatever on 2007-01-24
Sorry, the free space option is from liveCD. For automatic partitioning, try choosing Guided partitioning. Personally, I think the manual option is the best. Make it something like 1GB, or 1.5-2 the size of RAM, if your RAM is 512MB or less.

---

### Post by will m. on 2007-01-24
Ok.  It sounds as if Guided Partitioning is the way to go for me since I want Ubuntu to take up only 12GB or so on my laptop's HD at this point.  I assume you mean 1GB for the swap partition, correct?

So it sounds as if I don't need to partition the drive prior to my Ubuntu install after all.  Manually establishing the partitions during the Live CD install process will work.

Thanks for clearing this up.  I was under the impression that there was really a lot of risk of corruption if you didn't establish the partitions pre-Ubunutu.  That said I have backed up EVERYTHING.

Thanks again,

Will M.

---

### Post by geep on 2007-01-24
First you did do your homework just fine.

example on a 60GB disk

install XP first 30GB leave the rest alone.

Then place the ubuntu live cd in the drive reboot and follow the instructions on screen. If you let ubuntu create the partitions then the swap wil be set for you 30GB ( / + swap ).

Just to be on the safe side install XP basic don't spend hours on configuration just basic installation then install ubuntu. When that is finished and you reboot the system you should see GRUB the default boot loader of ubuntu and get the option to boot windows or ubuntu.

easy easy easy


good luck

---

### Post by mikewhatever on 2007-01-24
Will, the guide you've been reading deals with Alternate CD installation, and not LiveCD. For a LiveCD guide see this page [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
It does not matter if you partition your HD during Windows installation. If you do, skip the resizing steps in Herman's guide. One way or the other, you'll have about 12GB of unallocated space, on which you need to create the partition for Ubuntu, and the partition for swap. If it looks complicated, your best move is to follow the guide.(my case exactly!)
Good Luck:)

---

### Post by will m. on 2007-01-25
Geep, Mike,

Just wanted to thank you for your assistance yesterday.

Was able to install Ubunto 6.10 successfully last night using the Live CD.  I actually opted for the first partition choice during the install process which allowed me to resize my NTFS partition.  The installer made all the additional / and swap partition choices for me after that.

So far, so good!

Looking forward to adapting Ubuntu to my life as a grad student.

Regards,

Will

---

### Post by mikewhatever on 2007-01-25
Congratulations, and welcome to the club! By the way, what program have you used to backup the Windows partition?

---

### Post by will m. on 2007-01-25
Mike,

I actually didn't back up the partition so much as all my relevant information.  Just copied them over to an external.

Have you any good recommendations for a program to back up a NTFS partition?

Will

---

### Post by mikewhatever on 2007-01-25
No I don't. We've talked about it [http://ubuntuforums.org/showthread.php?t=344400](http://ubuntuforums.org/showthread.php?t=344400)
so I thought you might have tried one.

---

### Post by jwxie on 2008-02-27
hey guys, if you guys don't mind i just want to get something clear here

if i want to do dual boot
first i reinstall my xp, like how he would do 
let say 80GB

and after the XP, I am going to install my 7.1 Ub and ready to parition
i want to try manaual, here are a several cases

1. ram 128mb , if so, how many mb / gb do i need for swap? In general, how much space is 7.1 going to take beside the swap...

2. ram 1GB, if so, how mnay mb / gb do i need for swap?

---

