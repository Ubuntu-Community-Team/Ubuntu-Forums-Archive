---
title: "LiveCD install auto partition HELP"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Shakedown on 2007-04-18
So lets make sure I got the process correct: I download an .iso image from a torrent client, burn it to a DVD, restart comp, load up Ubuntu as my OS, then I can browse around and see what its like.  If I want to install it, then I click the "Install" button and it gives my 3 options: have Ubuntu auto-partition and install on remaining HD free space, or wipe my HD clean and install, or manually partition. 

As of now, I have Windows XP on a 51.9 GB hard drive, with 15.8 GB free space.  If I choose auto-partition, will Ubuntu use all 15.8 GB?  Won't that make XP terribly slow when I load it if there's no free space left?  I could delete several large programs from XP and get about 25-30 GB free space if I need to.  How many GB free space should Ubuntu need to operate at 100%?  And I have 1GB ram, so Im covered for ram.  And my processor is 1.6GHz Pentium M (I'm on a laptop)

---

### Post by Shakedown on 2007-04-18
BUmP

---

### Post by apunc1 on 2007-04-18
hi shakedown,

i think this guide will answer your questions about partitions.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

but yes, you have the general procedure correct. you can burn the iso onto a cd-r. take a look at this as well. [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Shakedown on 2007-04-18
Yeah I've read both of those prior to my post.  I wasn't able to find the detailed answers to my questions, haha so thank you for your reply but I still dont know the answers to my questions.  Ha thank you though

---

### Post by dalziel_86 on 2007-04-18
For starters, I think you're confusing hard drive space with RAM. The amount of free space you have on your hard drive (generally) has no effect on the speed of your computer.

To be honest, I would recommend you install Edgy rather than Feisty. Then you can upgrade to Feisty if you really want to, though you don't have to. The partitioner in the Edgy installer is much easier to use, and gives you a bit more choice about how to handle partitions. I would also recommend you read [this piece]("http://www.psychocats.net/ubuntu/partitioning") on partitioning for a dual-boot setup, to help you figure out what partitions you're gonna want.

It might help to clear out some hard drive space too, even if only temporarily, so you have more flexibility when re-partitioning.

---

### Post by Shakedown on 2007-04-18
No I understand HD and Ram, I was just letting you know the specs in case somebody asked about them.  From what I've read on psychocats links is that if I choose the first of the 3 options, the auto-partition option, that I don't have to do anything?  Does it then ask me how much space I want to give to Ubuntu?  Like I said, how much space should I devote to Ubuntu for it to operate flawlessly?

---

### Post by Shakedown on 2007-04-18
Oh and I would wait until tomorrow to get the newest version.

---

### Post by antoz on 2007-04-18
I would do the partition tables manually because if you select the automatic install it just might shrink your windows partition rather then using the free space.
As you have about 16 GIG to play with you could give root "/" about 6-7 gig "swap" 2 gig and use the rest for a separate "home" partition that way if you reintall you keep all your files and settings intact.

---

### Post by Shakedown on 2007-04-18
If it shrunk my windows partition I would lose a whole bunch of data wouldn't I?  Is 16GB enough to have Linux and everything I do with it work great?

---

### Post by Shakedown on 2007-04-18
So I'm thinking of skipping out on the /home partition for now.  If I have 16GB free space, I was thinking of leaving 6GB for XP and use the remaining 8.5GB for "/" and 1.5GB for "swap."  Is 8.5GB enough to have a fully-operational and seamless Ubuntu?

---

### Post by starcraft.man on 2007-04-18
Hi there Shakedown, I see your trying to do a dual boot xp and windows. 16 GB is more than enough, I would advise you manually make a 2 GB swap-file, and a 14 GB (or remainder) for Root (/). You may want a bit more swap-file if you render, or encode things or do other intensive things.

I also suggest using the Alternate installer, I found the manual partition maker in the text screens was very straightforward... especially for dual booting. (Link to Alternate [Here]("http://releases.ubuntu.com/"))

As for shrinking your windows partition, there are certain programs that will maintain the integrity of your files through a resize (I have used Arconis for a while and its good, though it is a pay program) I am pretty sure that the Ubuntu partitioner can do it too though, not certain... someone else know?

---

### Post by antoz on 2007-04-18
It all depends what you want to put on there like music or photos that takes a lot of space, but 16 GIG is more then enough for a ubuntu install.
You could shrink your windows partition with Gparted from the live CD and you should not loose any data but it pays to back up everything before doing this and also defrag a couple of times so there is no scattered data all over the place.
The links below are usefull before you install. 

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) 
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

PS: you could create a fat 32 partition to share between Ubuntu and Windows

---

### Post by Shakedown on 2007-04-18
I do plan on writing and altering code to answer that.  Doesn't creating a FAT32 to share files require that I reformat or do something with my NTFS?

---

### Post by antoz on 2007-04-18
If you shrink your Widows partition first and create a Fat 32 Partition with the free space your NTFS will stay intact. Just to give you an idea here is a screen shot of my partitions. Originally there were just 2 NTFS partitions,

As you can see from the screen shot sda8 is my home partition, sda3 is where Ubuntu is installed with about 1GIG and 2.5GIG respectively of used space. That is only a total of 3.5 GIG + 2.5 for swap

---

