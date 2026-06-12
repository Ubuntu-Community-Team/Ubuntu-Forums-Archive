---
title: "Creating dual boot for XP and Ubuntu"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by HaydnRobinson on 2007-04-23
I've never used any flavour of Linux before so please be nice to me (lots of detail where possible).

I have a XP machine with 2 hard drives - one with XP on and one with data on.  There's plenty of space on the drive with data on, so I'd like to dual boot my machine and have Ubuntu installed on this drive.

Problem is, I don't know how to do this.  I don't want to waste money purchasing some Windows repartitioning software and I don't want to lose any data on any of my hard drives.

So, how do I repartition my data drive so that 1) I don't lose any data at all and 2) install Ubuntu to that partition and have a dual booting PC?

Thanks in advance.

Haydn

---

### Post by goldaryn on 2007-04-23
There's two options, both on the install CD.

Firstly, the install wizard itself ("Install" on the desktop) has a repartitioner built in. Follow the instructions and you should be able to resize your data partition, and you should then be able to to install ubuntu to the free space you create. It's pretty easy. Obviously, read the options carefully!

If you have used Partition Magic or similar before, you can have a go using the an Ubuntu equivalent (also on the CD) - 'gparted'. Open a Console, and type in 'sudo gparted'. This is with admin privileges, be careful.

g.

---

### Post by HaydnRobinson on 2007-04-23
Thanks.  Will give it a try.

---

### Post by HaydnRobinson on 2007-04-24
Well, the resizing of the partition worked.  I now have a 30GB chunk of free space for a partition.

I read the documentation and it recommended creating a 500MB partition for the page file and the remainder for the Ubuntu installation.

I sized the partitions and specified the largest partition as '/' which it told me I needed to do.  Problem is, it then complained bitterly about the partitions and refused to allow me to continue properly.

Can someone please tell me what kind of partitions I need and what options to set (file systems, the '/' or '/boot' , etc.  Having come from a Windows background, the folder conventions are a little strange to say the least (although they are probably more logical than Windows when you get used to them).

Cheers

Haydn

---

### Post by HaydnRobinson on 2007-04-25
Anyone any ideas?  Really need some help here.

Thanks.

---

### Post by Bumblebee_Peanut on 2007-04-25
Zup dude,
I'm having similar problems. I have a master drive with XP and want to stick Ubuntu on a secondary to run and store. I can get to the drive in install and want to dedicate the "entire" drive to this OS but it reads that Partitions 1 & 5 are f$%ked up. I know from Windows the drive is fine. Anyways, I read through some of the info from this link and worked through some of it:

[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059),

Thought I'd throw it out there to yah.

Peace, E

---

### Post by Mairi on 2007-04-25
Well, I am NO expert. I only had to partion one disk, but I referred to this a lot, it was pretty helpful to me.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Good luck, and hopefully someone who knows what they're talking about will answer. I hope I can say Welcome to Ubuntu, soon.

---

### Post by HaydnRobinson on 2007-04-25
I did manage to get it working in the end and have now installed it all fine (with the exception of my wireless adapter which just won't work ](*,) ](*,) ](*,)  )

Anyway, all I did was in Windows first backup my work on my second drive, then defrag the disk.

Rebooted with the Ubuntu CD in and followed all the way through to the partition manager and selected manual.  I picked my second drive and gave it its new size, around 30GB smaller than before.  In a blink of an eye I had a 30GB unused partition.  Not believing this I rebooted and Windows seemed happy still and my second drive had indeed been resized.

I rebooted again with the Ubuntu CD in and followed all the instructions going to manual mode for the partition manager.  I selected my unused partition and selected to create a new one of 500MB, specifying the type to be SWAP and being a logical partition.  I then edited this partition to give it the correct type (I think it whinged first up because it didn't know what it was).  I selected the remaining 29.5GB and created a primary partition of type EX3.  Then, edit the partition and select the type to be "/".

On moving forward the installer warned I have a FAT16 partition on one of my drives.  I ingored this because I needed it.  About 10 minutes later Ubuntu had installed and all was well.

Hope this helps.  It's a little fiddly and annoying that you can't specify all the options on a partition when creating a new one (having to edit after creating is really annoying).

Haydn

---

