---
title: "please help on installation and disk format"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by hycnn on 2007-07-27
Hello, everyone,
I am new to ubuntu and considering to install it on my laptop, I have a very basic question, do I have to format my hard disk to install Ubuntu?
*I have:
Standard Compaq laptop with only one partition (30G disk, NTFS).

Thanks in advance for you good people's help :popcorn:

---

### Post by Mornedhel on 2007-07-27
Yes.

Linux is a real pain to run on NTFS (can be done, but definetely not at your level - nor on mine, for that matter). The Ubuntu installation process will take care of reformatting and will guide you through partitioning. Make sure to backup your data somewhere else before you format.

---

### Post by jingo811 on 2007-07-27
How much free disk space do you have, less or more than 50%?
Can you afford to not being able to use your laptop for the next 4 weeks?

I think that the best way to learn Linux is to wreck everything on your hard drive.  That's why during a period of some 5 days you should only concentrate on making a checklist over everything that needs to be backed up.
Then when you've secured all your personal data and won't flinch even if you drop your PC down the bottom of the Atlantic ocean.  That's when you know your're ready to embark on this journey :-)  It's the least painful way I think.  Learning by breaking.

---

### Post by tomcheng76 on 2007-07-27
you can use GPARTED LIVECD to shrink your NTFS XP partition and create a EXT3 for your Ubuntu
[Download]("http://gparted.sourceforge.net/download.php")
[Turtorial]("http://gparted.sourceforge.net/larry/resize/resizing.htm")

---

### Post by hycnn on 2007-07-27
Thanks very much for you guys' replies, very helpful.

To Mornedhel:
Yes, I will back up my files first, thx for the advice

To jingo811:
emm... I have more than half of free space on the disk. And this laptop is not my primary computer, therefore it can be used for experimental purpose. I will think about to give it a total format, but it is pretty painful, isn't it? I mean physically for the poor disk (as I had used the PQmagic for several times on it before...), anyhow, thx for the advice

To tomcheng76:
Yeah! I will try that sofeware to adjust the partion first, I think. Thank you!

Cheers guys, have a nice day!:)

---

### Post by coffeecat on 2007-07-27
> **tomcheng76 said:**
> you can use GPARTED LIVECD to shrink your NTFS XP partition and create a EXT3 for your Ubuntu
[Download]("http://gparted.sourceforge.net/download.php")
[Turtorial]("http://gparted.sourceforge.net/larry/resize/resizing.htm")

You don't need to download the Gparted live CD. Gparted is on the Ubuntu live Desktop CD. Once you've booted up go to System > Administration > GNOME Partition Editor. Saves you a download. :wink:

One thing I would add. Yes, shrink the NTFS partition to make room for Ubuntu, but leave the spare space as unformatted/unallocated. If you use all the space for an ext3 partition, you won't have a swap partition. Explanation - Linux uses a dedicated partition for swap, unlike Windows where you have a swap file.

When you start the installer, it will detect the unallocated space on the HD and format that for you with root and swap partitions. If you're new to Linux, that's the easiest way to go.

A couple more points. Defragment your NTFS partition before you attempt to shrink it. And if, by chance, you are running Vista, I believe there is a utility within Vista to shrink the C: partitiion. That's what I've read, anyway. Handy that, if true. Is Microsoft getting so absent-minded that they're making it easier for people to migrate to Linux? :)

---

### Post by tomcheng76 on 2007-07-27
yeah, just left the space as unformatted/unallocated is better
However, Ubuntu use GParted version 0.25 , which is pretty old and have some bug
Using Gparted LiveCD latest version makes sure all partition is not mounted to perform the resize operation

---

### Post by jingo811 on 2007-07-27
> I will think about to give it a total format, but it is pretty painful, isn't it? I mean physically for the poor disk (as I had used the PQmagic for several times on it before...), anyhow, thx for the advice

~15 Gig for experimental Linux is good enough for Dual Boot.
You can partition 1000 times and still retain the same physical health for the HD.  You're just setting up imagined fences for what parts (partitions) should do what.

---

### Post by hycnn on 2007-07-27
thanks, coffeecat, that is quite detailed!;)

I think it is much complicated, compare with the MS OSs (bad news for some people)

I  have to use the Kubuntu now, because I encountered an error when use the Ubuntu Live CD, I can see the desktop, but system just ceased to response (forever...), so I used the Kubunta Live CD, it worked and everything looked fine, but when I tried to install it, and relocate the partition in Step 4, it stopped working again!
I will try to adjust the partition first this time. Don't know what will come out this time, but will keep trying.

Will tell you what's going on later, thanks for you all to help the newbie :popcorn:

---

### Post by coffeecat on 2007-07-27
> **hycnn said:**
> I think it is much complicated, compare with the MS OSs

You have obviously never installed Windows from the Microsoft install disc (not the disc image that comes with most machines). :( :wink:

I have installed Windows 95, 98 and XP. Believe me; Ubuntu is much more straightforward.

---

