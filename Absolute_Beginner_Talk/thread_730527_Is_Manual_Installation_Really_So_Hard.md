---
title: "Is Manual Installation Really So Hard?"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Andavane on 2008-03-21
Hello
As I have a machine (laptop) with a wiped disk I'd like to do a manual installation by partitioning the disc. Is there a guide which explains manual installation. The guides say it is for advanced but surely it can't be that 'hard'?
Any help much appreciated
Regard
John

---

### Post by ResumeMan on 2008-03-21
This worked well for me:
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by igknighted on 2008-03-21
Theres nothing "hard", all manual means is that instead of ubuntu deciding what partitions to make and just doing it, you click 2 or 3 buttons and make them yourself.  It's "hard" if you don't know what a partition is, but theres nothing intrinsically difficult about the manual setup.

If you want manual setup, go with LFS, Gentoo or Slack :P

---

### Post by Andavane on 2008-03-21
> **igknighted said:**
> Theres nothing "hard", all manual means is that instead of ubuntu deciding what partitions to make and just doing it, you click 2 or 3 buttons and make them yourself.  It's "hard" if you don't know what a partition is, but theres nothing intrinsically difficult about the manual setup.
Indeed.
I ask because it always seems to go wrong for me, i.e. "you haven't specified a mount point" or that I put two mount points in the same place.
 As well as an ext3 partition I wanted to create a FAT32 partition as  a place to put my work, to be shared between Windows and UBuntu.

> If you want manual setup, go with LFS, Gentoo or Slack :P
Sorry what are these and where do I get them?

Thanks for your help.

Regards

John

---

### Post by igknighted on 2008-03-21
I don't mean to be elitist about that... I guess when I say hard, I am referring to the risks involved and the "on the fly" thinking and problemsolving that may come up.  You certainly do need a decent working knowledge of what partitions are needed for a standard linux install, but this is all data that you could look up in a book or from a website (or even probably this forum).  Armed with that data, it's not a challenging task.  I'll run over some basics here for you, but there is far more to it if you really want to delve in.

First, if you are coming from a windows background, you may be familiar with the mounting scheme where each drive/partition/disk gets its own letter and forms its own tree (c:, d:, etc.).  In linux, everything is part of a hierarchical tree. 

Essentially, your system starts with the / file system.  / is the root partition, and for the default install it is the only data partition created (it is the only partition that you MUST create).  It's mount point is /, and its file system can be any of ext2, ext3, reiserfs, jfs or xfs.  Ext3 is the default, and it is recommended you leave that unless you have a reason (it doesn't perform the best or have the most features, but it is the hardest to actually break).

The only other partition that is really of any value to a desktop user is /home/.  Now, you will have a /home/ folder either way.  But by building a partition and setting its mount point as /home/, the data in that folder will remain on a separate partition.  This is useful because your personal settings for your desktop and applications are stored in /home/, along with your personal documents.  This way when (if) you reinstall, you don't have to worry about this data being lost.

Typically, between 5 and 10 gb (depending on how much you like to install stuff) is enough for / when using a /home/ partition.  /home/ is your personal file space, so leave that as big as desired.  Again, the mount point for this partition is /home/, and the file system should probably be ext3 unless you have a reason to use something else.

Any folder (well... almost) can be mounted as a separate partition, but there is usually little reason to do so.  Sometimes /var/www or /boot/ are separated, but this is only worth doing when you have a specific need.

Oh... almost forgot.  It's not required, but a swap partition should also be made.  It provides emergency memory for the system for times when RAM fills up.  Also, a swap partition bigger than the available RAM must be present for hibernate or suspend (i forget which... probably hibernate) to work properly.  This is a partition of file system swap, and it has no mount point.

Hope this helps... there are more comprehensive guides around, try the forum search, but it sucks 95% of the time, so google is probable a better bet.

---

### Post by articpenguin on 2008-03-21
id a avoid reiserfs and xfs as they corrupt easy.

Fragmentation can be a problem on jfs.

---

### Post by igknighted on 2008-03-21
> **articpenguin said:**
> id a avoid reiserfs and xfs as they corrupt easy.

Fragmentation can be a problem on jfs.

Yup... but each does some things far better than ext3 does too.  But ext3 is the safe choice, so unless you have a reason to use something else, then ext3 is the way to go.

XFS actually is pretty good on a laptop... it's big drawback is sudden loss of power can trash it, but since a laptop has a built-in battery backup, it's pretty safe.  Not to mention anything to improve disk performance on a 5400rpm drive is nice.

---

### Post by Mustard on 2008-03-21
At the moment you are working with a blank formatted disk, so the 'risks' are pretty minimal, since you don't have any data on the drives to lose!

I would get experimental at that stage and reinstall several times using different partition setups and just learn the ropes with regards to partitioning.  This should at least make you familiar with the process and give you confidence in the future when you have to do it with personal data on disk.

---

### Post by Andavane on 2008-03-21
> **Mustard said:**
> At the moment you are working with a blank formatted disk, so the 'risks' are pretty minimal, since you don't have any data on the drives to lose!

I would get experimental at that stage and reinstall several times using different partition setups and just learn the ropes with regards to partitioning.  This should at least make you familiar with the process and give you confidence in the future when you have to do it with personal data on disk.
Indeed. That was what I had in mind when making the thread. I always take a backup copy of my correspondence and so on with a portable hard drive, that in turn is "backed up" onto my mates laptop and for good measure when in Windows there's a free backup thing which takes a copy onto the net as well.
I do feel like being a bit experimental, after studying and absorbing igknighted's article.
Regards
John

---

### Post by Mustard on 2008-03-21
The one piece of sound advice I can give you with regards to partitioning is the you have your /home directory on a separate partition.  There are countless guides on setting up /home on a separate partition.  Basically the advantage is that if you break your install, especially when you are first stumbling around on your virgin linux install, you can reinstall the operating system again, without actually formating the /home partition (which contains all your personal data and personal configuration settings).

At some stage in the installation process, if you are using manually setup for partitioning, its going to ask you for the mount points.  You need a mount point for / which is the root directory system, a mount point for the swap drive, and a mount point for /home.

---

### Post by Andavane on 2008-03-21
> **igknighted said:**
> I don't mean to be elitist about that... I guess when I say hard, I am referring to the risks involved and the "on the fly" thinking and problem solving that may come up.  You certainly do need a decent working knowledge of what partitions are needed for a standard linux install, but this is all data that you could look up in a book or from a website (or even probably this forum).....  Also, a swap partition bigger than the available RAM must be present for hibernate or suspend (i forget which... probably hibernate) to work properly.  This is a partition of file system swap, and it has no mount point.

Hope this helps... there are more comprehensive guides around, try the forum search, but it sucks 95% of the time, so google is probable a better bet.
Thank you very much indeed for going to such inordinate length to explain this to me and to others. I'll print it on some paper and take a good time to study it. Your language is beautifully simple.

I can feel some more questions from your essay brewing in the basement, but will take time to go over it thoroughly first to get the whole picture.

I'd just like to add that I find this forum to be admirably managed, the moderators kind and patient, and the membership willing and helpful too.

I sometimes wish that posters took a little more effort to encapsulate their problem into the post heading, but I stray.

Thanks again, and hope to be back with my further queries

Kind regards

John

---

### Post by Andavane on 2008-03-21
> **Mustard said:**
> The one piece of sound advice I can give you with regards to partitioning is the you have your /home directory on a separate partition.  There are countless guides on setting up /home on a separate partition.  Basically the advantage is that if you break your install, especially when you are first stumbling around on your virgin linux install, you can reinstall the operating system again, without actually formating the /home partition (which contains all your personal data and personal configuration settings).

At some stage in the installation process, if you are using manually setup for partitioning, its going to ask you for the mount points.  You need a mount point for / which is the root directory system, a mount point for the swap drive, and a mount point for /home.
I was planning to get round to this in the hints to igknighted.
Much as I'd like to go on, sleep calls, so will resume later. Thanks for such lucid replies, both of you.
More in next
John

---

### Post by kenpogi on 2008-03-21
Hi I'm a new user of Ubuntu, I have made many mistakes while doing a manual install, I can't offer much technical assistance because of my inexperience but this site helped me a lot;
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Andavane on 2008-03-21
> **articpenguin said:**
> id a avoid reiserfs and xfs as they corrupt easy.

Fragmentation can be a problem on jfs.

and

> **igknighted said:**
> Yup... but each does some things far better than ext3 does too.  But ext3 is the safe choice, so unless you have a reason to use something else, then ext3 is the way to go.

XFS actually is pretty good on a laptop... it's big drawback is sudden loss of power can trash it, but since a laptop has a built-in battery backup, it's pretty safe.  Not to mention anything to improve disk performance on a 5400rpm drive is nice.

picking up on these points, I'd take on board the comment on XFS... as indeed a laptop has its own ups -- the battery. But if fragmentation can be a problem, how would one defrag it? 

I ask because this is the third installation on this laptop -- and so far it the best behaved, apart from the fact that when I shut it down with "sudo halt", you see the writing coming up and then sometimes the picture freezes, and I have to hold down the "on" button to force a shutdown: clearly this is not satisfactory.,

Is it likely that making an xfs partition could help a cleaner shutdown?
As another member suggested, I can experiment at this stage as there is not anything permanently set as yet.

Regards

John

Laptop: Sony Vaio VGN-S3

---

