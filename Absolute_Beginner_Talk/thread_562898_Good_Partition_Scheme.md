---
title: "Good Partition Scheme"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-09-29
Well, I'm going to try setting up a duel Boot with Windows XP Professional and Ubuntu 7.10
when it's released and I am looking for a Good Partition Scheme.

I've been told it's good to give Ubuntu 3 partitions.
/ , Swap , Home

As far as how much to give them, I'm unsure.
I have a 120 Gig HD  and  1 Gig of Ram

When I set up Windows, I always set up C: and D: partitions
C: ( OS Drive ) this is where the Operations System Lives
and D: ( Program Drive ) this is where I place all my Programs, Photos,
Music, ect. 

So if I decided to do something like this, how much space would I need to
give each partition?

**Windows:**
C:
D:

**Ubuntu:**
/
Swap
Home

Thanks guys this board is a great help.

---

### Post by mivo on 2007-09-29
I would (and did) go with 10 GB for /, 1-2 GB for swap, and everything else for /home. I know that 10 GB for / seems small, but I run KDE, have the entire KDE office installed, all KDE games, OpenOffice, all KDE PIM apps including Knode and basket), Wine, Firefox, Java and quite a number of other applications and libs, and I still only use 38% of the 10 GB. It is very different from Windows where your Program Files folder may well be 30 or 40 GB. I wouldn't go under 10 GB, but anything over 10 GB would feel like a waste to me. (With GParted you can always resize partitions, so whatever you decide is not really totally final -- though resizing is never without risk).

Edit: 1-2 GB swap for Linux will be enough. I have 1 GB RAM also, and 1.5 GB swap, and it is almost never used. Windows doesn't need a swap partition. As for how much to give C and D, well, that depends on what data you have and what programs you use. With Windows that is a unpredictable and highly depends on what exactly you use/do. How large is your Program Files folder right now? Also, you can make a shared partition for data files that both Windows and Linux can use/see. FAT32 would be the easiest, though you can install NTFS drivers for Linux and ext3 drivers for Windows.

---

### Post by dptxp on 2007-09-29
Suggest make an additional 6 GB to 10 GB ext3 data partition.
Shall be very handy if you try any other Linux or version.
Else it can be used to store data.

---

### Post by Golyadkin on 2007-09-29
For me I keep it simple: 

1. One 15GB root partition, ext3, mounted on /
2. One 2GB swap partition, swap, because I have 2GB of RAM.
3. One big home partition for all data, ext3, mounted on /home

The home partition stays safe during reinstalls, and I can read/write ext3 in Windows XP as well.

Oh by the way, I sometimes had a separate partition for /opt, but I don't install that much programs there to justify a separate partition.

---

### Post by Orbital75 on 2007-09-29
> **mivo said:**
> How large is your Program Files folder right now? Also, you can make a shared partition for data files that both Windows and Linux can use/see. FAT32 would be the easiest, though you can install NTFS drivers for Linux and ext3 drivers for Windows.

Well, When I 1st set up Windows, I made ( C: 8 Gigs ) and D: ( 112 Gigs )

Just a note:
I have another Hard Drive that I run as a slave.
I use the slave for back up and to hold my Virtual Box Ubuntu install.
I also use this as a scratch drive for Home Video Editing.

I do have yet another Hard Drive that I place most my Media
on Music and Video

So, How would you guys recommend me setting this up?

What about the two other drives ( Mount them in Media ? )
Their NTFS.....

**Windows:**
C:
D:

**Ubuntu:**
/
Swap
Home

**Other Hard Drives:**
Mount them in Media with fstab?

What is /opt  ?  I'm not sure what that holds.... 
Also, I've heard there is a rule to Swap.
Something about you double the amount you have and thats the number you need.
Sorry, I'm new to Linux but learning.

---

### Post by Golyadkin on 2007-09-29
The swap rule used to be twice the amount of RAM, but nowadays people have so much RAM that 1:1 is good too. So if you have more than 1GB of RAM, you can suffice with a swap partition as small as the size of your ram. But diskspace being dirt cheap, a few MB more won't hurt.

In /opt I install everything that is not installed by .deb files, so optional software I install from .tar.gz files.

---

### Post by Orbital75 on 2007-09-29
Sounds like I'm on the right track as far as my setup.

I have another quick question.  I see that the default file system is ext3.
Is this the best one to use or is the Xfs better?

---

### Post by Golyadkin on 2007-09-29
I would go with ext3 because of the better journalling features. Xfs can be faster if you have advanced RAID setups and run database servers or do some really have video editing.

---

### Post by Orbital75 on 2007-09-30
Well, I think I'm going to just stick with ext3 then. I don't have any database severs or Raid configurations so looks as if xfs wouldn't be much use in my particular situation. 

Thanks for the help.... :KS

---

### Post by Golyadkin on 2007-09-30
You are welcome, good luck!

---

