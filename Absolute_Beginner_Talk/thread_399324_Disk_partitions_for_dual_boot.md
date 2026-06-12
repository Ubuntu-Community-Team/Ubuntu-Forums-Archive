---
title: "Disk partitions for dual boot"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-04-02
Hello, I'm newbie member here and this is my first post. I'm considering to install ubuntu linux. My lap specs are Toshiba tecra A2, Pentium M-1,5GHZ, 496MB RAM, 36GB HD. I have no partitions on my HD, I want to format it, make partitions, reinstall Windows XP and also install Ubuntu Linux. In how many parts should I divide my HD and how can I do it? Usually there's C Disk, where windows runs and D disk, where documents and other personal files are stored -movies, music, etc.. are stored. But now, considering the fact that I'm installint Ubuntu, I don't know anymore how to divide my HD.

Any suggestions?

---

### Post by miggols99 on 2007-04-02
You should install windows xp first, then Ubuntu. It will save you some trouble.

---

### Post by bullgr on 2007-04-02
-first boot from the winblows instalation cd and in the partition screen leave at least 5gb disk space for ubuntu (maybe more but this depents on your need's).

-leave the empty disk space for ubuntu as it is, unallocated.

-install winblows in the other partition you create (ntfs)

-after finishing installing winblows, boot now with the ubuntu install cd

-in the partitioning screen use the unallocated disk space and create two partitions: ext3 for the "/" (there ubuntu install's) and swap (memory swapspace). for the swapspace use the double of the memory you pc have (for example if you have 512mb memory use 1024mb for swapspace).

---

### Post by mikeyphi on 2007-04-02
> **O-pos said:**
> Hello, I'm newbie member here and this is my first post. I'm considering to install ubuntu linux. My lap specs are Toshiba tecra A2, Pentium M-1,5GHZ, 496MB RAM, 36GB HD. I have no partitions on my HD, I want to format it, make partitions, reinstall Windows XP and also install Ubuntu Linux. In how many parts should I divide my HD and how can I do it? Usually there's C Disk, where windows runs and D disk, where documents and other personal files are stored -movies, music, etc.. are stored. But now, considering the fact that I'm installint Ubuntu, I don't know anymore how to divide my HD.

Any suggestions?

As mentioned - If your HD is clean install windows then install Ubuntu - letting the Ubuntu installer allocate the partitions.

If you already have windows installed - just go ahead and install Ubuntu, again accepting the partitions suggested by the installer

---

### Post by O-pos on 2007-04-02
OK. my HD is not clean yet. I have old windows XP. I want to format HD, create partitions, install XP and the nInstall Ubuntu.

So, for Windows  I want the drive C, for documents I'm creating drive D. But How should I leave an unallocated empty disk space for ubuntu? should I create another drive, like E? Can I access with linux my documents on drive D?

For Linux I was thinking to make 3 partitions: one for the "root", one for the "home", and one for Swap - ie Virtual Memory. Can I have all these partitions in drive E? Or should each of these partitions have it's own letter?

And how does one make partitions? in bios?

---

### Post by mikeyphi on 2007-04-02
> **O-pos said:**
> OK. my HD is not clean yet. I have old windows XP. I want to format HD, create partitions, install XP and the nInstall Ubuntu.

So, for Windows  I want the drive C, for documents I'm creating drive D. But How should I leave an unallocated empty disk space for ubuntu? should I create another drive, like E? Can I access with linux my documents on drive D?

For Linux I was thinking to make 3 partitions: one for the "root", one for the "home", and one for Swap - ie Virtual Memory. Can I have all these partitions in drive E? Or should each of these partitions have it's own letter?

And how does one make partitions? in bios?

OK if you really want to start from scratch you can install windows as C: and make D: as fat32 so that ubuntu can 'see' it. Then install Ubuntu and use manual settings of your choice during the partition process of the install (you will be asked for your choice). By the by the 'Swap' partition won't be seen as a drive but all your Ubuntu partitions can be under one drive.

---

### Post by Sabar on 2007-04-02
I want to stress the fact that I know nothing! I am also a new user

From what I have read so far, what you are thinking of as Drive C is where windows will be. that should be in ntfs format, dont make that too overly big. 

Leave the rest of the Hard drive empty, the Ubuntu install disk can format the rest with, GParted? I believe its called.

for all you're shared files you're going to make what your calling drive D, but instead of ntfs format make it Fat 32. that way you can share it with both windows and Ubuntu.

Then I think all you need is 2 Gigs for Ubuntu to live in that would be EXT3 I believe 

and then a Linux swap file file that should be equal to the amount of Ram you have x2

One thing you should know though, Ubuntu doesn't use the letter designations for drives. I haven't figured that much out yet but I don't think your going to see Ubuntu calling drives C,D,E, 

Maybe what I have is screwed up but it doesn't look like Microsoft even Recignizes the drives that Ubuntu is on. 

Good luck hope things go well for you. see if some one who actually knows what they are talking about confirms what i said.

Sabar

---

### Post by O-pos on 2007-04-02
Will it work if I'll do loke this?:

C: Windows 10GB
D: 6-7GB free allocated space (for Ubuntu to be installed later)
E: fat32, Documents, music, movies, pictures. both for Ubuntu & Windows 20 GB

Then I can start to boot Ubuntu.

But If I'll have all documents on E, then do I need "home" partition for linux on D? root and swap only should be ok, right?

---

### Post by indytim on 2007-04-02
O-pos,

I've gone through this scenerio several times of late.  Variations to the attached are abundant :) .

1.  If you're somewhat paranoid about a really clean install on your hard drive, you could do a low-level format.  It consumes gobs of time, but you will be insured of having a "pristine HD" as in original mfgr condition.  A less agressive approach would be to delete all of your partitions via something like GParted Live [[URL="http://gparted.sourceforge.net/index.php"GParted Live]("http://gparted.sourceforge.net/index.php").

2.  My recommendation is to pre-configure your partitions before you start to load your ops.  Windows likes to be in the primary boot partition so I would create a partition as
NTFS <size for your Windows ops>.

3.  Next I'd recommend creating an extended partition.  This is sort of like a pseudo partition.  After this partition has been created, I'd recommend the following:

a.  Create a FAT32 partition for sharing files between Linux and your Windows ops.  Remember FAT32 only works with file sizes <=~4G.
b.  Create a swap partition =~ 2x RAM
c.  Create an ext3 partition of 5-15G this will hold your Linux ops
> variations if you elect to create a seperate partition for your /home, create this (you may want to reduce the size in "c" above.

4.  Re-boot with your Windows install disc.  When it comes time for you to identify the partition for Windows, use the partition created in #2.

5.  Painfully go through all of the stuffola associated with a Windows install.
6.  Boot to you Linux install CD.  Go through your "happy" install of Linux.  When you come to the part about where to install your Linux ops, select the manual method.  Identify the applicable partitions you created above.

Should be good-to-go from there.

Hope this helps,

IndyTim

---

### Post by antoz on 2007-04-02
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Have a look at the above link to get an idea, what you planned looks OK I would give Ubuntu about 8 GIG though.

---

### Post by Bartender on 2007-04-02
> **O-pos said:**
> Will it work if I'll do loke this?:

C: Windows 10GB
D: 6-7GB free allocated space (for Ubuntu to be installed later)
E: fat32, Documents, music, movies, pictures. both for Ubuntu & Windows 20 GB

Then I can start to boot Ubuntu.

But If I'll have all documents on E, then do I need "home" partition for linux on D? root and swap only should be ok, right?

It'd sure be easier to just borrow a friend who's done this a coupla times...

I like bullgr's suggestion...use the Windows CD to make a Windows partition.  That's how I did mine.  I think I left the rest of the disc unformatted.  Ubuntu recognized the blank space.  My drive was blank.  In your case you might want to let Windows format the entire drive, then partition before installing.  I don't remember the exact steps to do this.

Another option would be to toss the Ubuntu CD in, start thru the steps, then when you get to step 5 of 6 let Ubuntu wipe the entire drive.  Then you can abort the Ubuntu install, put in the Windows CD, and proceed.  If it were me doing that, I'd do it with a [GParted]("http://gparted.sourceforge.net/livecd.php") CD.  You download the latest version and make a bootable CD, just like you would do for an Ubuntu installer CD.  GParted is just a partitioner, and most find it works better than the truncated version of the same partitioner that you'll find on your Ubuntu install CD.  If I were to use GParted, I'd probly also use it to set up the partitions.  Or you could just wipe the drive, put in the Windows CD, and do as bullgr suggested.  Do you have a genuine Windows CD or a "Recovery CD"?  If all you have is a Recovery CD then I don't think you can partition with it.

You can only build 3 primary partitions.  The rest have to be logical partitions within an extended partition.  The Windows partition will have to be primary.  Then, since you're thinking of at least 3 more partitions (/, swap. and fat32) you'll have to make some or all of those logical.

I gotta get ready to go to work.  You'll have to do some searching; there are hundreds of threads.

---

### Post by O-pos on 2007-04-02
> **antoz said:**
> [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Have a look at the above link to get an idea, what you planned looks OK I would give Ubuntu about 8 GIG though.

Wow, that's GREAT link! I understood everything so clear. I'd choose 5th one: Windows with NTFS, Shared data+Ubuntu home: Ext3, Ubuntu: Ext3 & Swap. (if this FS-Drive really works)

---

