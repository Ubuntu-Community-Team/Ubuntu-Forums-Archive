---
title: "Partition for Dual Boot Questions"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by ARA10 on 2007-07-09
What's the point of having a 'shared data partition' as this ([http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)) site suggests?

Is it just to allow both operating systems to read and write to the same drive?  Can't that also be done on the ext3 partition that Ubuntu is to be installed on?  Ubuntu can read and write to it, and Windows can read and write to it with this software: [http://www.fs-driver.org/](http://www.fs-driver.org/).  So how about just having a Windows partition for Windows and a seperate partition for Ubuntu AND all shared data?

If creating a shared data partition, should it be located between the Windows and Ubuntu partitions?  Or does it not matter?  I know I've read that a primary partition shouldn't be placed between two logical partitions, but assuming that this is not the case, are there any differences in efficiency that depend on where you place a shared data partition?

What are the advantages of having a seperate /home partition?  I read that it's helpful when installing other versions of Ubuntu - one can have a 'clean' install rather than an 'upgrade'.  How useful is that?  It doesn't seem to matter to me.  That's why I want to know if there are other advantages.

Also, I read that Ubuntu can be installed on both, a primary or a logical partition, no?  So what's better?  The first website I gave the address for says: "A 'Primary' partition is a partition that will be listed in one of the four spaces in the partition table in the hard disk's Master Boot Record."  So what if it's in the hard disk's Master Boot Record?  What's the Master Boot Record for?

On this ([http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)) site again, when creating a 'mount point' for the shared data partition, the partition is mounted as /windows.  What is the significance of that name?  Does it matter what you call it?  Why does it make sense to call it /windows?

Sorry for asking so many questions.  Any information would be appreciated.  Thanks.

---

### Post by koshari on 2007-07-09
i think the shared data partition is a good idea and o n my notebook i have a 80g ext2 partition and use the windows ext drivers to access it, i did this rather than fat32 due to the 4g ceiling on f32.

---

### Post by dorath on 2007-07-09
While I can't answer all of your questions, I'll say this:

I've got a shared partition and it has been useful.  However, mine is merely FAT32.  In my case I'm not working with large files, and didn't care to configure XP.

---

### Post by ARA10 on 2007-07-09
> **koshari said:**
> i think the shared data partition is a good idea and o n my notebook i have a 80g ext2 partition and use the windows ext drivers to access it, i did this rather than fat32 due to the 4g ceiling on f32.

Hey thanks for the comment.  Is there a reason why you didn't use the Ubuntu partition as a shared data partition?  Can't Windows read and write to that drive as well?

---

### Post by davidjmayo on 2007-07-09
> What's the point of having a 'shared data partition' as this ([http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)) site suggests?

Is it just to allow both operating systems to read and write to the same drive? Can't that also be done on the ext3 partition that Ubuntu is to be installed on? Ubuntu can read and write to it, and Windows can read and write to it with this software: [http://www.fs-driver.org/](http://www.fs-driver.org/). So how about just having a Windows partition for Windows and a seperate partition for Ubuntu AND all shared data?

Yes you are right this will work but see below

> 
If creating a shared data partition, should it be located between the Windows and Ubuntu partitions? Or does it not matter? 
I know I've read that a primary partition shouldn't be placed between two logical partitions, but assuming that this is not the case, are there any differences in efficiency that depend on where you place a shared data partition? 

It's best located between (see here [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning))

> 
What are the advantages of having a seperate /home partition? I read that it's helpful when installing other versions of Ubuntu - one can have a 'clean' install rather than an 'upgrade'. How useful is that? It doesn't seem to matter to me. That's why I want to know if there are other advantages.

The advantage of the separate /home partition is you can keep your settings for Ubuntu and also any data you want to save here (I save all my data in /home--but I don't use Windows so have no need for a shared partition). Now if for some reason you had to reinstall Ubuntu you keep all your previous settings and data as they are in a separate partition (/home) to the OS. You can do this in Windows too. Have the Win OS in one partition and make another for data. Same scenario - a reinstall and you don't lose your data. Seems like a good idea to me

> Also, I read that Ubuntu can be installed on both, a primary or a logical partition, no? **So what's better**? The first website I gave the address for says: "A 'Primary' partition is a partition that will be listed in one of the four spaces in the partition table in the hard disk's Master Boot Record." 

Not sure what's better

> So what if it's in the hard disk's Master Boot Record? What's the Master Boot Record for?


This tells the computer what OSes are installed and available to be booted. If you want dual boot the MBR needs to know where windows and ubuntu are (ie what partitions) so when choose one or the other it can find it.

> On this ([http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)) site again, when creating a 'mount point' for the shared data partition, the partition is mounted as /windows. What is the significance of that name? Does it matter what you call it? Why does it make sense to call it /windows?


call it what you like. I'd call it something meaningful like /data or /shared but it's up to you, call it (random typing here)  /dgrgergm if you want
It makes no sense to call a share partition /windows

Hope this helps. If anything is unclear post back
David

---

### Post by az on 2007-07-09
> **ARA10 said:**
>  So how about just having a Windows partition for Windows and a seperate partition for Ubuntu AND all shared data?.

Being that you don't know what windows really does under the hood, some people may be concerned that it will indroduce vulerabilities into your linux installation.

> **ARA10 said:**
> 
If creating a shared data partition, should it be located between the Windows and Ubuntu partitions?  Or does it not matter?  I know I've read that a primary partition shouldn't be placed between two logical partitions, but assuming that this is not the case, are there any differences in efficiency that depend on where you place a shared data partition?.

A partition is a partition.  Whether it is primary or extended/logical is pretty much irrelevant.  The only difference is how it is entered in the partitoin table.  This is only relevant to the disk controller.  Your partitoin software should not allow you to do something that cannot be done, so the question is irrelevant.  There is no performance difference in what kind of partiion it is or where it is on the disk.

> **ARA10 said:**
> 
What are the advantages of having a seperate /home partition?  I read that it's helpful when installing other versions of Ubuntu - one can have a 'clean' install rather than an 'upgrade'.  How useful is that?  It doesn't seem to matter to me.  That's why I want to know if there are other advantages..

A seperate /home partition is useful if you are desperate and have no other way opf backing up your data.  If your whole drive goes, all your data is gone.  It is not a substitute for backing up your data.

As well, your settings for one version of an application may not work so well with another - it is not recommended to share a home drive between two installations.  You will eventually have something bork.

> **ARA10 said:**
> 
 So what if it's in the hard disk's Master Boot Record?  What's the Master Boot Record for?


It's the index, the table of contents for all the partitions.

---

### Post by buuntuu! on 2007-07-09
> **ARA10 said:**
> 
Is it just to allow both operating systems to read and write to the same drive?  Can't that also be done on the ext3 partition that Ubuntu is to be installed on?  Ubuntu can read and write to it, and Windows can read and write to it with this software: [http://www.fs-driver.org/](http://www.fs-driver.org/).  So how about just having a Windows partition for Windows and a seperate partition for Ubuntu AND all shared data?


if your root-partition is accessible from windows then destruction is just a couple of clicks away! 
using fs-driver for windows has a big downside: file-permissions are not being respected. from windows you can access any file on your ubuntu-partition, those that are restricted to root as well. imagine your little sister sneaking into your room and fiddling with your pc, or you being  tired and not really thinking before you click... 

installing fs-driver you can decide which partition windows has access to, so having a separate /home partition will minimize the damage that can be done from windows. simply exclude / from the partitions you want to access. 
as not only data but also settings are being stored on your /home partition (open your filemanager with "show hidden files" enabled and have a look) it still is risky and i wouldn't recommend it if others have access to your box. 

take care

---

### Post by UnixAnt on 2007-07-09
Although a common partition of FAT32 or EXT2/3 for shared data is doable, I would advise against it on the basis of many of the reasons given above.

If you can afford it (and can be bothered) I would suggest installing Windows on one partition, Ubuntu on other partitions and having attached storage for your data sharing needs.  Personally, I am a fan of consumer-level NAS products, ideally in RAID5 configuration, but whatever suits your needs will do.  You can even get drive caddies which accept a single drive and present this out via the local network.  Because the files are network attached, they will be presented out as either NFS or CIF shares, meaning permissions will be kept in tact and there is less chance of cross OS corruption of your data.

That said, I used to have a common ext2 partition for a short time and had no issues with it.

---

