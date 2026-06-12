---
title: "How do I partion my hard disk for dual boot?"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by shenava on 2006-09-03
Hi, this is my first post and I appologise coz I realise what I am asking is probably very common and must annoy some people seeing the same questions asked. I have searched about to see what issues I may face and now I am looking for a simplistic "how to".

I would like to put Ubuntu onto my machine but retain Win XP. Normally I would just go for it and work out how to fix the problems as/when I come across them but I have too much on my hard disk that I cannot afford to lose so I don't want to take any foolish risks.

At this stage I have Windows XP Home running on a Athlon XP 2500 machine. I have 1 Hdd with 80 gb capacity. There are no partitions that I am aware of and everything it is NTFS. I have an Ubunutu 6.06 CD that I downloaded last night.

I would like to get to a stage that when I switch on my computer I will have a choice of XP or UBuntu. I would also like to be able to access files from either OS.I would like to do this without having to buy any more software if possible.

Can someone explain how I do this in _plain english _or post a link to somewhere it has been answered.

Muchly appreciated.

---

### Post by meng on 2006-09-03
Good question, I suggest this link:
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)
or this one:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Don't pre-partition with PartitionMagic or anything like that, the LiveCD installer is what you want. Dualbooting with Windows is pretty much the default install situation. If you install Ubuntu onto an ext3 partition, you can read it from Windows by installing a free ext3-reader.

---

### Post by baylorbear on 2006-09-03
I was in the same spot a month or so ago.  My situation was only slightly different -- I have two hard drives... drive 1 is windows, drive 2 was going to by my Ubuntu drive.

If you go ahead and pop the Ubuntu disk in, look for the icon to install Ubuntu to your computer.

The installer for Ubuntu (which will run from within Ubuntu) is actually quite good.  You will be prompted during the installation for your installation preferences.  One of those screens will allow you to re-configure your partitions.  If you follow the on-screen instructions, you should be fine.  

Just for kicks, you may wanna go ahead and run a defrag on the Windows drive before doing this and try to clean it up.  If you have any data stored on the end of your disk (where you will install Ubuntu) you'll want that moved to the front.

Tell the installer to create a second partition and select that one for where you will install Ubuntu.  You will actually be creating 2 or 3 partitions, depending on your preferences.  

Scenario 1:   Hard drive 1 has 4 partitions.  (1) Windows (2) Root (3) Home (4) Swap

Scenario 2:   Hard drive 1 has 3 partitions.  (1) Windows (2) Root & Home (3) Swap

For an 80 gig hard drive running Windows as dual-boot, I recomment scenario 2 as it will leave you more room to expand on Ubuntu if you decide you like it.

By default, the installer will install GRUB on your hard drive.  This will prompt you at each boot whether or not you want to load Windows XP or Linux.  And you can configure / tweak GRUB later on once you have everything up and running.

Hope this helps!! :D

---

### Post by steve.horsley on 2006-09-03
Probably the easiest approach is to use a windows product like Partition Magic to reduce the size of the windows partition, leaving the rest of the disk un-allocated / un-partitioned. The Ubuntu installer will then offer to install into the unused disk space. Do not try to use Partition Magic to creat a partition for Ubuntu - let the Ubuntu installer create its own partitions in the free space.

The Ubuntu installer has a facility to reduce the size of the windows partition - I only suggest PM because ig probably has a more familiar feel to you, and you can't blame Ubuntu if PM scrambles your disk.

---

### Post by Omnios on 2006-09-03
One inportant thing to do when setting up a dual boot partition is to defrag the hell out of the drive before the install. I would recoment defragging a couple times to get all the files nice onto the win partition section before the install. This will also help with the formatting for the new partition

---

### Post by shenava on 2006-09-03
I am running defrag as I type.

Have I understood what has been said coz I'm a little confused.

Once the defrag is complete I should just go ahead and install Ubuntu? Ubuntu will create a partion for itself automatically? Will it give me the option at that point to say I want it to be partioned as ext3 so that I can still access files in a windows environment?

At the moment the hard disk is 100% NTFS.

Partition magic is an alternative method for partitioning but not required??

---

### Post by steve.horsley on 2006-09-04
If the disk is fully used, the installer will offer to shrink the NTFS partition to make space. I forget if this option is still available if there is unallocated space or not.

If there is unallocated (unpartitioned space), you have the option to use that.

You always have the option of erasing the entire disk and using all of it (assuming the disk is not empty).

You always have the option of custom partitioning.

Partition magic is not required, but you may prefer to make space using that tool if you are already familiar with it. Just don't use PM to create partitions for Ubuntu because it seems to screw up the formatting sometimes. Also, people doing that often forget to also create a swap partition. Leave blank space and let the Ubuntu installer create the new partitions.

---

### Post by shenava on 2006-09-04
When I tried to install Ubuntu. At step 5 I picked the top option which was to partition and use the free space. Instead what I got was a message after a while saying it was unable to create enough space. 

I defragmented the hdd and there is 24gb (31%) of free space so I'm not sure why it is saying that. any ideas?

---

### Post by steve.horsley on 2006-09-04
Maybe the defrag didn't leave a big enough gap at the end to allow the partition end to be moved very far. The XP defrag doesn't seem very good to me. If the Ubuntu installer can't do it, I guess the next thing is to try Partition Magic - maybe that can do a better job. I'm sure the Ubuntu installer makes no attempt to move files to make a bigger space, but maybe PM does.

---

### Post by bakert on 2006-09-04
Can I be really boring and suggest you backup your data you mustn't lose before repartitioning your hard drive?  Even if you're NOT going to repartition your hard drive it would be a good idea - hard drives DO fail.

---

### Post by shenava on 2006-09-05
I noticed that when I did the defrag, there was a chunk of data sat near the end of the hard disk that was unmovable. Maybe thats what the problem is.

I have backed up all the really important stuff so if things go tits-up it won't be too big a disaster.

Partition magic is not free?

Anyone used Partition Logic? It's free and says it can shrink ntfs partitions. I have downloaded it but chickened out at the last stage coz I wanted some feedback first.

---

