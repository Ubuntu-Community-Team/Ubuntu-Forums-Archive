---
title: "How do you recommend I setup my dual boot?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by pHEnomIC on 2007-05-01
My laptop is a hp dv6000 that came with xp pro. In addition it has a setup called Quickplay which allows you to play dvd's without loading the os.   I really don't care much for the quickplay but I suspect some of my drivers such as media buttons and stuff rely on it.  I also hear it is a pita to install.  I have a 120 gb hard drive with a 10gb recoery partition.  I plan on dual booting ubuntu.  Primarily will use ubuntu but I do have a few apps that I need to run in windows (Car tuning software).    In addition I would like to be able to view my windows files in linux and if possible vice versa.  I used linux a while ago regularly and to my knowledge there wasn't much read/write support for ntfs.   

How do you guys recommend I partition my 120 gb harddrive?

Im thinking 80 gb to Ubuntu and the remainder to xp.   Should I partition the windows and format it as NTFS or FAT 32?  Also, are there any good linux filesystems that windows can recognize?  Basically I am a bit confused where i should keep my music which i would like to be common to both oses.

Should I even bother trying to install quickplay on top of this?

---

### Post by MCGrunge on 2007-05-01
> **pHEnomIC said:**
> My laptop is a hp dv6000 that came with xp pro. In addition it has a setup called Quickplay which allows you to play dvd's without loading the os.   I really don't care much for the quickplay but I suspect some of my drivers such as media buttons and stuff rely on it.  I also hear it is a pita to install.  I have a 120 gb hard drive with a 10gb recoery partition.  I plan on dual booting ubuntu.  Primarily will use ubuntu but I do have a few apps that I need to run in windows (Car tuning software).    In addition I would like to be able to view my windows files in linux and if possible vice versa.  I used linux a while ago regularly and to my knowledge there wasn't much read/write support for ntfs.   

How do you guys recommend I partition my 120 gb harddrive?

Im thinking 80 gb to Ubuntu and the remainder to xp.   Should I partition the windows and format it as NTFS or FAT 32?  Also, are there any good linux filesystems that windows can recognize?  Basically I am a bit confused where i should keep my music which i would like to be common to both oses.

Should I even bother trying to install quickplay on top of this?

I might suggest trying a utility like Gparted.  You'll likely be able to keep both your Windows partition and Quickplay in tact by simply shrinking the NTFS partition.  Feisty reads my Windows partition quite well, but Windows won't read EXT3, so you'll need to make a FAT32 partition as well if you want Windows to be able to see your Ubuntu files.

---

### Post by Inxsible on 2007-05-01
> **pHEnomIC said:**
> My laptop is a hp dv6000 that came with xp pro. In addition it has a setup called Quickplay which allows you to play dvd's without loading the os.   I really don't care much for the quickplay but I suspect some of my drivers such as media buttons and stuff rely on it.  I also hear it is a pita to install.  I have a 120 gb hard drive with a 10gb recoery partition.  I plan on dual booting ubuntu.  Primarily will use ubuntu but I do have a few apps that I need to run in windows (Car tuning software).    In addition I would like to be able to view my windows files in linux and if possible vice versa.  I used linux a while ago regularly and to my knowledge there wasn't much read/write support for ntfs.   

How do you guys recommend I partition my 120 gb harddrive?

Im thinking 80 gb to Ubuntu and the remainder to xp.   Should I partition the windows and format it as NTFS or FAT 32?  Also, are there any good linux filesystems that windows can recognize?  Basically I am a bit confused where i should keep my music which i would like to be common to both oses.

Should I even bother trying to install quickplay on top of this?

I got the HP dv9000t recently and i dual booted with Vista. Still have to play around with the quickplay thingy.

For your partition questions :
I had a 160 GB HDD and i gave 50GB to windows  and 110 to Ubuntu

my partitions are:
C:  -- NTFS - 25GB -primary
D:  -- NTFS - 25GB-primary
/shared - EXT3 - 76GB - primary (This is where i plan to keep my music and movies and pics)
/ - EXT3 - 9GB - logical
/home - EXT3 - 20GB - logical
/swap  - ------ - 1GB - logical

Are you planning to keep the recovery partition? I created the recoverry discs and then backed up the recovery partition on an external HDD and got rid of the partition completely

and if you install [FS-Driver]("http://www.fs-driver.org/") you should be able to read / write to an EXT3 partition, with some limitations. But basic functionality is more than sufficient. Read all about it before installing it

It works for XP...although it gave me some trouble with Vista :( 

In Linux you can install ntfs-3g and you will be able to read/write to ntfs partitions. This worked for me instantly

hope that helps !!

Oh and in case,  you get your integrated camera working (if you have one)...do let me know !!

---

### Post by mejy on 2007-05-01
Linux can now read and write both ntfs and fat32, and ext2/3 are both supported by an open source windows driver - [http://www.fs-driver.org/]("http://www.fs-driver.org/").  It's also extremely unlikely that any drivers depend on this seperate partition, so you're almost certainly safe going ahead without worrying about it.  Still, remember to back up your important files before installing Linux the first time.

Edit:  beaten to it... twice :s

---

### Post by Dakiraun on 2007-05-01
You could keep Windows in it's native NTFS (if already installed) because Ubuntu will be able to mount the partition, though as **read only**.  You can also grab [Ext2IFS for Windows]("http://www.fs-driver.org/index.html") which allows windows to read/write to the Linux partitions provided you keep them ext2 or ext3.  Due to a screwup in how Microsoft did the Fat32 system, you won't be able to use a Windows install to format a drive any bigger then 32 gigs in Fat32, if you choose to redo Windows on a Fat32 partition.  You can use Ubuntu's partitioner to do that, or you can also get the [G-parted LiveCD]("http://gparted.sourceforge.net/livecd.php") to handle it.  The quickplay thing could be what's on the other partition on your drive, and chances are, you can leave that as is.

---

