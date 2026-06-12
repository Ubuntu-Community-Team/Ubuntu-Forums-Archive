---
title: "Partitions &amp; Upgrading Ubuntu"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2006-04-17
When upgrading Ubuntu, say from Breezy to Dapper, I think I read somewhere in the forums it is best to have your files (user data) on a separate partition.  Is this true or can upgrading the OS be done without "losing" your already accumulated assortment of programs and files?  Some advice would be appreciated.  Can the re-partitioning be done post initial install when I only made one partition for Ubuntu?

---

### Post by xyz on 2006-04-17
Hi- I'm not certain this is what you're looking for but I'm looking into it myself! Not being sure, I suggest this link to you;
> read somewhere in the forums it is best to have your files (user data) on a separate partition.
[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)
I give you this link but ...did you know that everything can be searched on ubuntuforums?..just in case my link didn't satisfy?
Hi to Nova Sco...

---

### Post by jazzmuzik on 2006-04-17
[QUOTE=flyingsolo]When upgrading Ubuntu, say from Breezy to Dapper, I think I read somewhere in the forums it is best to have your files (user data) on a separate partition.  Is this true or can upgrading the OS be done without "losing" your already accumulated assortment of programs and files?[/QUOTE]

Generally speaking, I think it is best to keep your /home directory on a separate partition. It's more flexible that way. I don't think it will hurt to do an upgrade if you have everything on one partition, but I suggest you hear from others on this.

As far as a post install re-partition, I think this is possible with parted and gparted, a graphical interface, but I've never done it. My method is to backup everything to a tar.gz file, store it on a windows drive, install the new OS and unpack the backup to the /home directory. 

I ran into a big gotcha recently with this method. One of my backups was about 6 gig and I thought it was safely backed up to a windows partition, but when I tried to reinstall it later I found that the windows mount only stored..., if I recall correctly, only about 2 gigs! Where did the other 4 gigs go? I never looked into the answer, but I think it has to do with the max addressable space on a windows mount, and that seemed to be about 2^31, which is 2147483648 byes. That's only a guess since I never investigated it. So beware.

I was noticing the other day a Linux distribution devoted to partitioning: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) . Again I haven't tried it, but thought I might give it a whirl one of these days.

To be safe, have a method of backing up your valuable data in some way. If anything goes wrong you can always restore things. A second hard drive like those plug-in usb hard drives might be handy for this.

---

