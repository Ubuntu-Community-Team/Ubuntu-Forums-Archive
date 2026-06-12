---
title: "Installing ubuntu on a hard drive with Windows already on it."
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by Sydney Losstarot on 2006-05-27
My goal is to install ubuntu on the same hard drive that my Windows installation is currently on.  Is this inherently difficult in some way?  Because I've tried installing other distributions of linux on the same hard drive as Windows, but I never succeeded.  I got it installed and it would boot up, but I couldn't boot into Windows anymore.

My hard drive is set up like this: I have about a 10GB NTFS partition where Windows is currently installed, then about a 60GB NTFS partition where I keep all my stuff, and a spare 10GB of unpartitioned space, where I plan to install some distribution of linux.

---

### Post by aysiu on 2006-05-27
Hm. With that setup, it's going to be... interesting.

It's good to have a Windows partition, a data partition, and a Ubuntu partition, but unfortunately your data partition is NTFS, which can be read by Linux but not written to (there are programs that allow you to write to NTFS, but these are experimental and could corrupt your data).

These two links may help you out, but I think your #1 problem will be somehow converting that NTFS partition to FAT32 or Ext3 without losing your data. Can you back it up somehow--on an external hard drive, DVDs, an iPod? It's a good idea to back up your stuff anyway...

[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by Sydney Losstarot on 2006-05-27
I'm looking over those pages you linked to now ...

The reason I left so little space for another operating system, as well as using NTFS for my data partition, was because I didn't plan on using linux very much.    I figured I could install some distribution of linux in that 10GB, and have a couple GB left to store a small amount of linux stuff.

Basically, I just want to learn how linux works, but I don't plan on using it much.  That may change in the future, though.

By the way, it is possible to install ubuntu in a 10GB partition, and still have a small amount of room left over, isn't it?  That's my plan, right now ...

---

### Post by aysiu on 2006-05-27
10 GB is plenty for Linux. My only concern is that you'll be able to access your data partition as read-only.

You may want to take a look at this link as well:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by Sydney Losstarot on 2006-05-27
Would it be possible to make a small FAT32 or ext3 partition to fill up what space is left after ubuntu is installed, and use that as a data partition for ubuntu?

---

### Post by aysiu on 2006-05-27
[QUOTE=Sydney Losstarot]Would it be possible to make a small FAT32 or ext3 partition to fill up what space is left after ubuntu is installed, and use that as a data partition for ubuntu?[/QUOTE] You mean use that as some kind of transfer station? You want to modify a file, so you copy it to the transfer station partition, modify it, and then from Windows copy it back to the data partition...? Seems a lot of trouble.

I should have mentioned earlier--Have you tried the live CD already? I mean, you know whether your hardware will play nice with Ubuntu or not? You're familiar with Ubuntu's interface and such? If not, then I would use the live CD for a couple of weeks first to get used to Ubuntu. It runs completely off the CD and your computer's RAM and doesn't affect your hard drive.

If you're sure you want to install Ubuntu, I would do this:

1. Back up your data any way you can. Yes, I realize it's 60 GB, but it probably wouldn't be a bad idea to have backups anyway, but *especially* since you're installing a new operating system you're not familiar with, it's a *really* good idea--just on the off-chance that you accidentally delete that partition instead of the 10 GB one (it could happen).

If it has to be 60 CDs you burn or 300 floppy disks or two iPods... whatever you've got to do. Back it all up.

2. Install Ubuntu to the 10 GB partition. Make sure it works. Play around with it a bit.

3. When you're pretty comfortable with Ubuntu and you want it to stay for good, reformat the data partition as Ext3 and then copy all the data back to it from your CDs, floppies, iPods, whatever.

4. Install [http://www.fs-driver.org](http://www.fs-driver.org) on to Windows so it can read/write the new Ext3 data partition.

---

### Post by Sydney Losstarot on 2006-05-27
Hm, that's good advice.  I'll try the live CD for a while instead.

Backing up my stuff isn't a problem.  I have another hard drive that I usually use solely to back up my data partition.

---

### Post by aysiu on 2006-05-27
You're going to be in good shape, I think.

Just remember to keep asking questions. It's always better to ask what you think is a dumb question *before* you do something than to try to troubleshoot problems *after* you do something you didn't ask about.

---

### Post by skippy81 on 2006-05-27
My first ubuntu install was not dissimilar to yours:

40gb windows partition

20gb ubuntu partition

100gb shared data partition

Now you have 2 solutions for the shared data partiton - EXT2 and FAT32.  FAT32 can be read and written to by linux.  Ext2 can be be read/written by windows using [http://sourceforge.net/projects/ext2fsd]("http://sourceforge.net/projects/ext2fsd").

Since you current data partition is in NTFS format, you will have to do something about that:- 

Option 1) BACKUP ALL THE DATA ON IT, and use partition magic to convert it to FAT32.  It can then be happily shared by linux and windows.  Partition magic costs $$$, I dont know if there is a free program which can convert NTFS back to FAT32.  Even if you own partition magic the process is risky [http://faq.arstechnica.com/link.php?i=1820]("http://faq.arstechnica.com/link.php?i=1820")

OR

Option 2) BACKUP ALL THE DATA ON IT, and reformat it as either FAT32 or EXT2.  I recommend you use FAT32, while it is arguably not as fast as EXT2, it is simple and does the job for storing media files. 

p.s. my current ubuntu setup is different. I now have 

windows 10gb
ubuntu boot 500mb
ubuntu root 15gb
ubuntu home 134gb

I cant say I have noticed any sort of performance increase by having my media on a linux XFS partiton, my movies played just as quick of a FAT32 drive.  

Whatever you decide to do, backing up is the key.

---

