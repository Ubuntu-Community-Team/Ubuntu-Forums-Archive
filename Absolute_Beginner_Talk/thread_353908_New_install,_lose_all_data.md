---
title: "New install, lose all data?"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by F A B Scott on 2007-02-05
Hi,
 Being the complete n00b to linux, I need to know for **certain** whether I can install ubuntu on my XP computer without losing everything already installed.[data & programs]
I have read conflicting answers in various forums on the net.
I wanted to have Ubuntu on a separate partition to my current XP; I have got the disk from shipit so I'm just waiting for the word.

Thanks in advance.

---

### Post by taurus on 2007-02-05
If you only have partition, you need to use gparted from the LiveCD to resize your harddrive, creating an empty space to install Dapper on.  And of course, you should _always_ backup your important files just in case.  And also, defrag your harddrive a few times in XP first before you resize it.

Maybe this guide would help.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Ryan450 on 2007-02-05
yes you can, but tread lightly and carefully because it is soo easy to lose everything. I've been making these kind of installs all the time.

what you need to do is first defrag your windows xp partition, then you can use ubuntu's partitioner to resize the windows partition to make it smaller, thus allowing you enough freespace to install ubuntu by doing it manually. 

Like I said be carefull when you do this and be sure to double check everything.

---

### Post by philmiller on 2007-02-05
I just installed Ubuntu a week ago and was very worried about the same thing.  I backed up all my data and jumped in.  The only thing i did to my windows partition was make it smaller and I lost nothing.  the installation was simple.  From what i can tell, as long as you don't delete your windows partition everything will still be there.

good luck.

Phil

*update*
I also did defrag a few times too.  this was helpful as well: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by az on 2007-02-05
> **F A B Scott said:**
> Hi,
 Being the complete n00b to linux, I need to know for **certain** whether I can install ubuntu on my XP computer without losing everything already installed.[data & programs]
I have read conflicting answers in various forums on the net..

When you boot the installer and go through the steps to install, when you get to the partitioning part, you will be offered several options.  Do not pick the "Use entire disk" option since this will blow away everytyhing on your disk.  Instead pick the option that should be the default one - Resize a current partition and install Ubuntu on the freed space.

That is the easiest and safest way to partition and install.  I do not reccomend you partition manually, since that would introduce the posibility of you making a mistake.

That being said, you should always make backups of your important data.  Nothing is guaranteed.  There is no partitioner on the market that will guarantee than you will not have data loss - there will always be that possibility.

And you don't strictly need to defragment.  If the ubuntu installer cannot safely move that data out of the way, it will just refuse to try.  In that case, you should defreagment.


> **F A B Scott said:**
> 
I wanted to have Ubuntu on a separate partition to my current XP; 

There is no other way than that.

But the installer can automagically partition for you, as I said.

---

### Post by F A B Scott on 2007-02-05
Just to clarify - I should've said before. I have just the one partition at the moment with xp on it. [80gigs] Presumably I would follow the instructions on screen from the cd  for partitioning? I'm more concerned about having to reinstall programs but thanks to your replies I feel a bit reassured.
Thanks for the replies. :)

---

### Post by az on 2007-02-05
> **F A B Scott said:**
> Just to clarify - I should've said before. I have just the one partition at the moment with xp on it. [80gigs] Presumably I would follow the instructions on screen from the cd  for partitioning? 

You pick the option where it will resize an existing partition for you and you will decide the new size of your windows partition.  There will be a slider bar.  Slide it down to whatever you want, say 10 gigs or whatever your needs are, and then click next and you are done.  It will create the root and swap partitions for you after it shrinks the windows partition down.

---

### Post by CynAmun on 2007-11-16
I installed previous versions doing a partition. I don't remember any questions about this and don't see my XP data. OMG! Is there any way to find that stuff?

---

### Post by taurus on 2007-11-16
> **CynAmun said:**
> I installed previous versions doing a partition. I don't remember any questions about this and don't see my XP data. OMG! Is there any way to find that stuff?

What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- lower case letter l, not number 1
```

p.s.  I hope you didn't tell the installer to use the whole disk!  That would be real bad.

---

### Post by CynAmun on 2007-11-17
> **taurus said:**
> What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- lower case letter l, not number 1
```

p.s.  I hope you didn't tell the installer to use the whole disk!  That would be real bad.


Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4659    37423386   83  Linux
/dev/hda2            4660        4864     1646662+   5  Extended
/dev/hda5            4660        4864     1646631   82  Linux swap / Solaris


This is bad. Isn't it?

---

### Post by mellowd on 2007-11-17
Unfortunately nothing is for certain. 99.99% of the time it'll go without a hitch but anything could happen. Ive had a power blackout in the middle of a partition operation, ended up losing everything.

At the end of the day, if you simply cannot lose something, back it up first.

---

### Post by LinuxGuy1234 on 2007-11-17
> **CynAmun said:**
> Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4659    37423386   83  Linux
/dev/hda2            4660        4864     1646662+   5  Extended
/dev/hda5            4660        4864     1646631   82  Linux swap / Solaris


This is bad. Isn't it?

Yes. I think your NTFS volume seems steamed by Ubuntu. Please do these steps:
1. Reboot into Windows and run a:
chkdsk /r
2. Reboot into Ubuntu.
3. Install ntfs-config (in Edgy, but enable the universe repos). For Dapper install by clicking [here]("http://ubuntuforums.org/showthread.php?t=217009").

To add the Universe repos in Edgy run:
```
gksudo gedit /etc/apt/sources.list
```

Uncomment these lines:
```
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe
```

(you can leave the deb-src line commented if you like)

Saave it and run:
```
sudo apt-get update
```

Now install ntfs-config (either by: ```
sudo apt-get install ntfs-config
``` or the SPM).

Now see? I found LOADS of Lanuchpad bugs in Ubuntu that damage NTFS parts of the MBR and make them useless.

---

### Post by LinuxGuy1234 on 2007-11-17
> **F A B Scott said:**
> Hi,
 Being the complete n00b to linux, I need to know for **certain** whether I can install ubuntu on my XP computer without losing everything already installed.[data & programs]
I have read conflicting answers in various forums on the net.
I wanted to have Ubuntu on a separate partition to my current XP; I have got the disk from shipit so I'm just waiting for the word.

Thanks in advance.

One word: backup.

I found LOTS of Lanuchpad bugs about NTFS stuff.

---

### Post by bodhi.zazen on 2007-11-17
> **mellowd said:**
> Unfortunately nothing is for certain. 99.99% of the time it'll go without a hitch but anything could happen. Ive had a power blackout in the middle of a partition operation, ended up losing everything.

At the end of the day, if you simply cannot lose something, back it up first.

I agree 100 %

Resizing a partition and installing a new OS, although rare, can result in data loss and the first step is to perform a backup of your current OS and data.

Before you install, you should read the installation guides and understand the Linux partitioning terminology.

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

And here is an installation guide :

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Don't forget to defragment your windows  partition before you resize.

GParted:
	Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

---

