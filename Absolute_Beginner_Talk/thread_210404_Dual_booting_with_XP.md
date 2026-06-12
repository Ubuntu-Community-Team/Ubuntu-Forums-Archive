---
title: "Dual booting with XP"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by Jeff_From_Hell on 2006-07-06
does anyone have a walk though on how to dual boot windows xp and ubuntu? and is there a way to install ubuntu without reinstalling windows? i just reinstalled it and dont want to do it again, but i will if i must.

---

### Post by Silver Streak on 2006-07-06
[Here]("https://help.ubuntu.com/community/WindowsDualBoot") is the Official Wiki Walkthrough.

Basically, as Ubuntu is installing, it detects that Windows is there, and asks if you'd like to install GRUB, which is the tool that lets you boot either Windows or Ubuntu.

\/ \/ \/ BTW, some of those walkthroughs are outdated; 6.06 has a pretty graphical installer. :p

SS

---

### Post by dbmata on 2006-07-06
here is a link I found for one walkthrough:
[Here]("http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html")

and here is another link I found:
[Here]("http://jaeger.morpheus.net/linux/ntldr.php")

Looks like I may have problems, all my disks are in ntfs due to size. Damn.

---

### Post by Jagot on 2006-07-06
Here's another couple of guides - with pictures:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)

---

### Post by Jagot on 2006-07-06
[QUOTE=dbmata]
Looks like I may have problems, all my disks are in ntfs due to size. Damn.[/QUOTE]

NTFS poses no problems unless you want to share files between it and your Ubuntu partition.

---

### Post by catlett on 2006-07-06
ntfs is not a problem for installation. the installer will resize one of your ntfs partitions and convert it to ext3 before installing ubuntu.
the only issue , as already mentioned, is after installation. Ubuntu can safely read ntfs (meaning you can view all your windows data) but it cannot safely write to ntfs (microsoft owns the code for ntfs and hasn't made it public so any ntfs driver for linux has been created through reverse engineering.)
The 2 links jagot posted are the best how tos for ubuntu out there. The first one deals with the alternate install cd which does a text based install. The second one deals with the desktop live cd installer which does an install from a live cd session.

---

### Post by dbmata on 2006-07-06
[QUOTE=Jagot]NTFS poses no problems unless you want to share files between it and your Ubuntu partition.[/QUOTE]
I would... I'm thinking of putting Ubuntu on a 250gb scratch drive...
I use it for video, graphics, etc. I would like to have access to this drive and my 80gb backup drive while in ubuntu... both are ntfs.

---

### Post by dbmata on 2006-07-06
[QUOTE=catlett]ntfs is not a problem for installation. the installer will resize one of your ntfs partitions and convert it to ext3 before installing ubuntu.
the only issue , as already mentioned, is after installation. Ubuntu can safely read ntfs (meaning you can view all your windows data) but it cannot safely write to ntfs (microsoft owns the code for ntfs and hasn't made it public so any ntfs driver for linux has been created through reverse engineering.)
The 2 links jagot posted are the best how tos for ubuntu out there. The first one deals with the alternate install cd which does a text based install. The second one deals with the desktop live cd installer which does an install from a live cd session.[/QUOTE]
damn, can windows read ext3? Is there a way to share files between ubuntu and windows?

(Hey OP, sorry for hijacking.)

---

### Post by Jagot on 2006-07-06
[QUOTE=dbmata]damn, can windows read ext3? Is there a way to share files between ubuntu and windows?[/QUOTE]

[http://fs-driver.org/](http://fs-driver.org/)

---

### Post by catlett on 2006-07-06
[http://www.fs-driver.org/](http://www.fs-driver.org/) This is an ext2 driver for windows. This will give windows read/write access to your ubuntu partition.
There are 2 ways to get access between windows and ubuntu.
1. create a fat32 partition. windows and linux have full read/write capabilities for fat32. Then keep data you want both OSs to use in it, or use it as a "swapping" spot to place files in and then copy them over when you reboot.
2. install the ext2 driver. This way windows has full access to your linux partition. Ubuntu will be able to read your ntfs files but if you wanted to alter the files, you would have to copy the files from the ntfs partition to your linux partition and then alter them  after they were moved to an ext3 partition. Then windows would have to copy them over from the ext3 partition back to ntfs after you rebooted. It's a bit of a pain but not intolerable.

---

### Post by Jeff_From_Hell on 2006-07-06
can i install without the cd?
and when i get that far, hwo big should i make the partitions? i have about a 30 gig hd. might be getting a bigger one

---

### Post by Jagot on 2006-07-06
[QUOTE=Jeff_From_Hell]can i install without the cd?
and when i get that far, hwo big should i make the partitions? i have about a 30 gig hd. might be getting a bigger one[/QUOTE]

No, you will need the CD

You may want to read this guide with reference to partitioning:

[http://psychocats.net/ubuntu/partitioning.html](http://psychocats.net/ubuntu/partitioning.html)

---

### Post by eightball1989 on 2006-07-06
I don't want to hijack the thread, but I'm also looking into dual booting with XP...

I have a slightly different situation though...

All I have at the moment is a laptop.
(Hoping to have a desktop by the end of the summer...)
I need it daily for my job, and I need it to run windows in the fall.

So far, I love ubuntu (been using the Live CD off and on for a few weeks now), and I'd like to install it, but, because I have a laptop, I'm limited to one HD.

I guess my question is:
Will following the instructions on [http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html) install ubuntu as a 2nd OS on my existing HD with minimal risk of data loss, or is there a better/safer way?
(I assume I should select the option to resize the partition)

Will I be able to access my current data from Ubuntu (and will I be able to ask data written from Ubuntu while running Windows)? (I assume the answer to both is yes, but thought I would double check)

Thanks,
Zach

---

### Post by crystal on 2006-07-07
> Will I be able to access my current data from Ubuntu (and will I be able to ask data written from Ubuntu while running Windows)? (I assume the answer to both is yes, but thought I would double check)
Yes, yes. For the former you can only read but not write from Ubuntu if the Windows partition is NTFS. For the latter you would need the ext2 driver for Windows that catlett mentioned (and of course your Linux shared data partition should be ext3).

---

### Post by Jeff_From_Hell on 2006-07-13
Are any of those walkthroughs for computers that have ubuntu on them, and want to install Windows?

---

### Post by Uncle Spellbinder on 2006-07-13
Don't know if this helps or not, but here's my experience with installing Dapper/XP dual boot (using Live CD):

I deleted two no-longer-used partitions and added the unallocated space to the C:Windows partition. I then installed Dapper via the "install" icon on the live cd desktop. The necessary partitions were created automatically (with the exception of the overall "new" partition size, I chose 25Gb). All went very smoothly. Sound and web connection were detected perfectly. Updated Dapper - Done.

A very pleasant install experience that took about 20 minutes.

---

### Post by Linuturk on 2006-07-13
I had a tough experience installing Dapper on a friend's machine.

I started with an OS-less machine. I proceeded to install Windows XP on an 80 GB partition, processed all the updates and such, and made sure it would boot up correctly.
On the other 40 GB, I setup 3 partitions. 1 gig for swap; 10 gig Ubuntu; 30 gig /home

After the install of Ubuntu, I tried to boot back to Windows (XP Pro SP2) via GRUB.

The XP splash screen would appear briefly, then the system would reboot.

I repeated the process using the Alternate Text Mode install, with the same results. The media i used for the Ubuntu install has been used many times since then w/o a hitch.

I have yet to get up the courage to try another dual-boot install.

---

