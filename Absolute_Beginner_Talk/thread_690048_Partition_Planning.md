---
title: "Partition Planning"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by leehach on 2008-02-07
I've read several interesting threads on partition planning.  I'm pretty sure I understand the benefit of a separate partition for the /home folder.  Some people have made remarks about preferring to keep a small /home for config files, and keeping their documents on a separate "data" or "media" partition, while some prefer to keep it all (config and documents) in /home.  What have your experiences been with these configurations?

Also, I see that each user has a folder under /home, but where are the usernames stored?  If I reinstall Linux the /[username] folders will still be there, but would I have to recreate the users?

Finally, what are your space recommendations for the partitions?  I just bought a new computer with a large (500GB) hard drive, so I'm thinking about ~50GB for each of the Windows partition and Linux partition and then 400GB for documents and data.

---

### Post by erfahren on 2008-02-07
> **leehach said:**
> I've read several interesting threads on partition planning.  I'm pretty sure I understand the benefit of a separate partition for the /home folder.  Some people have made remarks about preferring to keep a small /home for config files, and keeping their documents on a separate "data" or "media" partition, while some prefer to keep it all (config and documents) in /home.  What have your experiences been with these configurations?

Finally, what are your space recommendations for the partitions?  I just bought a new computer with a large (500GB) hard drive, so I'm thinking about ~50GB for each of the Windows partition and Linux partition and then 400GB for documents and data

I use a dual-boot setup with Windows. I have a small partition for /home ~3GB (which I really don't use much of) and then a seperate FAT32 partition for storage and to share files between the two OSs. (I made that partition awhile ago - Gutsy now supports read/write to NTFS by default.)

If you have a seperate /home all that's really needed for Ubuntu's root is about 10GB at the most.
> 
Also, I see that each user has a folder under /home, but where are the usernames stored?  If I reinstall Linux the /[username] folders will still be there, but would I have to recreate the users?

yes, you'd need to re-create the user *accounts*. The files with the settings are in /etc ( /etc/passwd , /etc/group ), but I'm not sure about backing them up and restoring them. It might be possible, but they are critical system files. Unless you have *many* user accounts, it would probably be easier to just recreate them.

Hermanzone's site has comprehensive information about dual-booting with Windows, as well as other stuff. The guide is for installing with the AlternateCD (text-based installer) but much of the info is still applicable. [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Since you are planning this well ahead of time it probably would be a good idea to set up the storage and Ubuntu partitions as an extended partition. That would make it easier to divide it up more later if you wanted to try out another distro or something. see hermanzone's [Help on Partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm)

good luck :)

---

### Post by louieb on 2008-02-07
> **erfahren said:**
> ... I have a small partition for /home ~3GB (which I really don't use much of) and then a separate FAT32 partition for storage and to share files between the two OSs. (I made that partition awhile ago - Gutsy now supports read/write to NTFS by default.)
If you have a seperate /home all that's really needed for Ubuntu's root is about 10GB at the most.

:guitar:+1 I've been using Linux for a couple of years.  Tried a lot of different setups . erfahren pretty much described how I do it now.  Really works well.

---

### Post by leehach on 2008-02-07
Thanks for the informative replies.  I notice that under /home there are Documents, Music, etc. folders, which are analogous to similarly named folders in Vista.  I know how to set up Vista so that the \[username]\Documents folder points to the data partition.  How would I do the same thing in Ubuntu?  The goal would be that when I save a file in, say, OpenOffice Writer that it defaults to saving it to a Documents folder on the data partition.  (I'm sure I can configure this in OpenOffice, but the point would be to have it work the same for all applications, for apps that use the Music folder by default to use /Music on the data partition, etc.)

---

### Post by erfahren on 2008-02-07
> **leehach said:**
> ...  (I'm sure I can configure this in OpenOffice, but the point would be to have it work the same for all applications, for apps that use the Music folder by default to use /Music on the data partition, etc.)
let's say you mounted the data partition as simply "/data"

a simple way to accomplish that would to make the "Music" directory in your home a symbolic link to the /data/Music directory - you could check into that.

if you did that, anytime the Music folder in your home directory is opened it would send you to the /data/Music directory. 

to create a symbolic link to do that it would be like (delete the Music folder in your home and create the /data/Music directory first):
```

sudo ln -s /home/leehach/Music /data/Music

```

-- just an idea

---

### Post by leehach on 2008-02-07
Thanks again, erfahren.  Last partition size question, which I forgot to include in the initial post.  I've seen various threads where people say the swap partition should be 1x or 1.5x or even 2x your RAM.  (My computer has 2GB RAM.)  Is there a performance gain with a larger swap, or is it just wasted space?  (And how much time should I spend thinking about it?)

---

### Post by erfahren on 2008-02-07
the guideline that swap should be twice the size of installed RAM is actually a little outdated - that was when PCs only had 256 to 512MB 

if you're going to use suspend you should make it equal to the installed RAM  - so 2GB for swap would be plenty

---

### Post by jken146 on 2008-02-07
I think 2 GB for swap is excessive.  I have never used more than half a gig, so I'd recommend 1 GB as a maximum.

---

### Post by freebeer on 2008-02-07
A 2 gig swap will be plenty... probably overkill since these days, with computers with such large memory capacities, swap is rarely used in my experience.  (Windows is an entirely different matter, of course.)  I have a gig of memory on my home machine and I don't think I've ever seen it use 400M.  :D

As for partitioning, maybe my experience might be of some value to you: my home machine was set up just as a "discover Linux" machine.  I had no idea how much room I needed for /.  I figured that I'd give it plenty as I was planning on adding scads of software and tinkering around a lot.  So I gave it 20 gigs (plus 1 gig /swap the rest /home).  After a year and a half the / partition is only using 3.5 gigs.  (Mind you, I do clean stuff off that I know I'm not going to use any longer, but I'm running quite a bit -- apache2, ftp, samba, etc.)

---

### Post by Monsuco on 2008-02-07
> **leehach said:**
>  Is there a performance gain with a larger swap, or is it just wasted space?
There only is if you need to use it for virtual memory. If you have 4 GB of ram then you probably don't need much swap.

As for partitioning. I personally have 4 primary partitions:
About 140 GB for Windows Vista
About 10 for Recovery (I might erase this since I have a disk)
About 99 for Linux
About 1 for Swap

I just keep it simple.  Since I have a lot of games installed on Windows I store my music and videos and of course my papers in a folder called documents in Linux. I put a shortcut on my desktop (you can make windows read and write to ext2/3 filesystems using [this driver](http://ext2fsd.sourceforge.net/), stuff that can read ext2 can read ext3 but usually it wont use the journal)

A consistent home is only good if you need it, but I would just keep it simple.

BTW, if you want to do hundreds of gigs for storage make sure you use either NTFS or ext2/3. FAT and FAT32 have strict limits on file size.

---

### Post by leehach on 2008-02-07
Thanks for all the excellent remarks, and the info that the swap = 1.5x-2x RAM advice is outdated.  Since space isn't an issue, I'll probably leave the Windows and Linux / partitions larger than necessary for now, and resize them later if they don't fill up.  (3.5GB, freebeer?  I can't believe Vista is taking up 16GB and I haven't even installed anything on it yet!)

---

### Post by freebeer on 2008-02-07
yep, just 3.5 gigs.  Of course, I don't have any games on it (other than those that come with the default install, and some of those I got rid of).  My web site doesn't have much data on it (I just put it up for practice).  If it did get anything sizable though, I'd just move it over to the /home partition anyways.

---

