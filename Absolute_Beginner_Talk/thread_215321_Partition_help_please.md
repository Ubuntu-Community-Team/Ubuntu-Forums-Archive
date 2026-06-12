---
title: "Partition help please"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by Hotwhlz85 on 2006-07-13
I asked this question the other day but I don't think I gave enough info to get a good answer.  I'm trying to install ubuntu.  When I get to the part about partitioning my hard drive the only option I am given is to reformat the whole thing.  I'm not ready to let go of M$ just yet so that isn't an option.  I've searched, researched, and read everything I could find but still am blocked at this point.  The two attached images will better show what I am talking about.  

This first image is from psychocats.net, a wonderfully written guide that I think will help me get around the rest of my install if I can get this hdd partitioned.

[IMG]http://www.carolinadreamin.net/KC/w2u260tf.png[/IMG]

This image is a screen shot of the options I am offered when I try to install.

[IMG]http://www.carolinadreamin.net/KC/Screenshot1.png[/IMG]

The first option that is said to be the best option for someone that wants to dual boot (which is me) is missing.  Has anyone seen this before and can you tell me why I don't have that option?  

I have also tried creating the partitions beforehand in XP using Partition Magic.  It gives me an error message saying it can't be done.  I'm stumped!!  ](*,)

---

### Post by aysiu on 2006-07-13
I don't know why you don't get that second option, but you can try to **Manually Edit the Partition Table**--it'll have the same effect, but you'll have to do a bit more manually... and you'll have more control over the partitioning process.

---

### Post by Hotwhlz85 on 2006-07-13
Thanks for the quick reply aysiu.  That's the other side of this problem.  Clicking manual edit takes me to the next window that shows the whole hdd as unallocated.  When I click on the hard drive to highlight it so that changes can be made to it I get a window with a message that says "before any changes can be made to this hard drive it must be given a new disklabel.  THIS WILL ERASE ALL DATA FROM SCA1".  I'm not ready to do that just yet.

All I can figure since I can't partition it with Partition Magic either is that there is something preventing me from changing this hard drive.  I just don't know what as I have never had that problem before.

---

### Post by indytim on 2006-07-13
I'm not clear on your last posting.  If you have partition magic running on your Windows intallation, you certainly can re-partition your hd to accomodate the Ubuntu install (instead of doing it at the time of your system install).  If this applies, just remember etc3 for Linux and FAT32 for any partitions you want to easily share between Windows and Linux.  If you don't have partiton magic, disregard the ramble :D .

IndyTim

---

### Post by Hotwhlz85 on 2006-07-13
You sorta understood IndyTim.  I do have Partition Magic running on XP.  When I try to partition the hard drive I get an error message:

[IMG]http://www.carolinadreamin.net/KC/Image2.png[/IMG]

This is on a less than one year old Sony Vaio desktop, 3.0 Ghz, 1Gb DDRAM, 250 Gb SCSI hard drive.

To make things more muddy...I just ran the ubuntu LiveCD on my new laptop and it worked perfectly.  Gave me all the options that aysiu said I should find.

---

### Post by moshuptrail on 2006-07-13
do a chkdsk on the drive and check for bad blocks
i realize it's a new machine and that would be unlikely,
but GParted will not do anything with a drive that has
bad blocks.  I bet P-Magic is skittish about bad blocks too.
All it would take is one bb and you might get very
strange behavior from those progs.

If it is, there are ways to to do it.

---

### Post by Hotwhlz85 on 2006-07-13
Finally figured out why Partition Magic wasn't doing as it should.  Resized the large partition in Windoze (there was a small partition at the start that contains the system restore files) and left the large portion of the hdd unallocated.  Booted back into the LiveCD and the installation went smooth as silk.

Ubuntu is now up and running and so far everything I have tested works!

Thanks to all for the suggestions.

Ron

---

