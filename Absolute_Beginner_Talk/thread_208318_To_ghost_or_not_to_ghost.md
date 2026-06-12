---
title: "To ghost or not to ghost"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by mit on 2006-07-03
Hi,

Despite *having* to have XP Pro on my laptop for work purposes, i am determined to learn Linux and want Ubuntu on a partition. ;) 

I am worried about the partitions becoming *screwed* due to the difference in file systems.  What can i safely use to back up NTFS whilst using Linux on the other partition? Ghost? Image quest? 
While on the subject of disk maintenance, i understand the linux file system keeps itself in order so no real need of defragging. What are peoples opinion on Spinrite ([www.grc.com](www.grc.com))

Thanks in advance

mit

---

### Post by noynac on 2006-07-03
Mit

I used to use Norton Ghost but now use Acronis TrueImage to backup up my hard drive. I have used TrueImage on many occasions to restore an NTFS  (WinXP and Win2k) partition, and it has never failed me.  Also, *with the restore disk,* you can image a Linux partition and swap file to an external hard drive. I'm new to Linux and last night I imaged and restored my Linux partition as a test. All went well. :D 

BTW, I use TrueImage 8 but have not purchased and cannot comment on TrueImage 9, though I suspect it's a fine program. Also, I have no experience with SpinRite.

noynac

---

### Post by arsenic23 on 2006-07-03
Yes, I only Acronis myself.  9 is just as good as the previous versons.

---

### Post by T-Rexx on 2006-07-03
Fair warning, mit: There are almost no laptops in existence on which Ubuntu (or any other version of Linux) will install. You're probably stuck with Win XP on the laptop.

Try booting the "live" disk. Chances are, it won't boot.

---

### Post by keith whitehouse on 2006-07-03
hi t-rexx,

bloody hell I hope you are wrong (i am sure you are), as I am going to install Ubuntu on my nx8220 tomorrow.

best regards keith

---

### Post by Jagot on 2006-07-03
[QUOTE=T-Rexx]Fair warning, mit: There are almost no laptops in existence on which Ubuntu (or any other version of Linux) will install. You're probably stuck with Win XP on the laptop.[/QUOTE]

That's absolutely not true.

---

### Post by six on 2006-07-03
Your XP partition should be quite safe, I would have thought, unless you do something silly. The Linux partitions won't suddenly corrupt the NTFS partition XP sits on.

For backing up both Linux and NTFS partitions, have a look at these GPL sites:

[http://www.partimage.org/Main_Page]("http://www.partimage.org/Main_Page")

[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

Partimage works just as well as Norton Ghost 2003, if not better. (I've found out Ghost can't handle Linux partitions that well).

Here's a link from another thread I've just read:

[http://www.psychocats.net/ubuntu/partimage.html]("http://www.psychocats.net/ubuntu/partimage.html")

It has screenshots of how to use partimage within ubuntu.

The Rescue CD site is a real gem. It contains a bootable ISO image (with partimage on it) for burning to CDR or USB stick. I've been using it this afternoon for the first time. It's good! :D 

I posted a similar mesage in this thread too, btw:

[http://www.ubuntuforums.org/showthread.php?p=1209659]("http://www.ubuntuforums.org/showthread.php?p=1209659")

---

### Post by T-Rexx on 2006-07-03
I've tried to install Ubuntu on 5 laptops to date - no go on any of them.

The hardware in laptops tends to be proprietary. They therefore require proprietary drivers which are not included in the standard Ubuntu (or any other Linux) distributions. You may get lucky, but you can usually only get Linux running on a laptop if you have someone write the drivers for you. Occasionally, you may get it to install, but not be able to network or access the internet, etc.

---

### Post by Jagot on 2006-07-03
There are many people using Linux successfully on laptops.  Take a look here:

[http://www.linux-laptop.net/](http://www.linux-laptop.net/)

When talking about internet access, NIC's with ethernet are almost always picked up with no config necessary.  Most WLAN cards can be used with either drivers that have been created specifically for them by the Linux community or by using ndiswrapper.

It is true to say that setting up a laptop can involve more than installing on a desktop, but I have never had a problem.

---

### Post by coffeecat on 2006-07-03
[quote=T-Rexx]There are almost no laptops in existence on which Ubuntu (or any other version of Linux) will install.[/quote]

What complete and utter nonsense. Which parallel universe are you posting from?

Just to add, mit, that I've used Acronis Disk Image too and can heartily recommend it. Once I did so to image and restore my Windows partition on my Sony Vaio laptop so that I could completely reformat and repartition the hard disk for a quad boot. Which is what I've got now - Ubuntu Dapper, SuSE 10.1, Fedora 5 and Windows. I'm posting from Ubuntu - naturally. :wink:

Good heavens! Break out the champagne! A laptop on which you can install three flavours of Linux. Wonders will never cease! :shock: :roll: :wink:

---

### Post by bruenig on 2006-07-03
[QUOTE=T-Rexx]I've tried to install Ubuntu on 5 laptops to date - no go on any of them.

The hardware in laptops tends to be proprietary. They therefore require proprietary drivers which are not included in the standard Ubuntu (or any other Linux) distributions. You may get lucky, but you can usually only get Linux running on a laptop if you have someone write the drivers for you. Occasionally, you may get it to install, but not be able to network or access the internet, etc.[/QUOTE]
Fairly certain all hardware is proprietary or at least I have never been given free hardware. Maybe I am just unlucky

---

### Post by mit on 2006-07-03
Thanks for all your input, guys :) 

I have to say i have had 5.06 installed on the laptop before i needed to delete the Linux partition and everything worked straight off the CD. Even the wireless Centrino Chip.
Good work i say to all involved in k/ubuntu :KS 
Looking forward to coming back!....

---

### Post by dmann on 2006-07-03
Spinrite won't defrag your filesystem, it will check your drive for any potential media errors and try to recover any data from the damaged area.  It can also do fitness testing and benchmarking among other things as well.

It's boots from freedos.  Your bios needs to recognize the disk drive for spinrite to see it, which is one complaint people have with the product.

We (spinrite cusomters) are asking for an upgrade to get beyond this limitation, but steve (the developer) has been very busy with other projects.

I've used it several times to try and recover data, but so far it's only saved me once.  Typically though you can use it to test your drives and possibly predict a near term failure, which is nice.

Plus steve has a nice news/forum area with information about how drives work (below the host interfce level) and stuff like that.

Dan
> **mit]Hi,

Despite *having* to have XP Pro on my laptop for work purposes, i am determined to learn Linux and want Ubuntu on a partition.  said:**
> www.grc.com[/url])

Thanks in advance

mit

---

### Post by mit on 2006-07-03
[QUOTE=dmann]
It's boots from freedos.  Your bios needs to recognize the disk drive for spinrite to see it, which is one complaint people have with the product.
Dan[/QUOTE]

Hi Dan,

Thanks for the advice. 
When you say the BIOS recognizing the drive are you talking about older machines? Most machines within the last few years have a BIOS that will recognize and boot from CD. Have i got the wrong end of the stick?

Mit

---

