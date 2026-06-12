---
title: "dual boot (Ubuntu installed first then XP)"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by koji126 on 2006-07-25
I don't have a copy of XP Pro yet because I am waiting until school starts because I will be able to get a free copy there.  Is it possible to install Ubuntu on my laptop first then install XP later to dual boot?  I have searched for dual booting instructions for installing Ubuntu first then XP, but have only found instructions for installing XP then Ubuntu.  Are there no instructions because XP must be installed first then Ubuntu?  Thanks.

---

### Post by richbarna on 2006-07-25
Why not just run ubuntu live cd, then you can use it until you get Xp and then do an install the proper way.

---

### Post by koji126 on 2006-07-25
Using the live cd, will I be able to install other programs and update a few things or am I stuck using whatever they have available on that cd?

---

### Post by Indras on 2006-07-25
> **koji126 said:**
> I don't have a copy of XP Pro yet because I am waiting until school starts because I will be able to get a free copy there.  Is it possible to install Ubuntu on my laptop first then install XP later to dual boot?  I have searched for dual booting instructions for installing Ubuntu first then XP, but have only found instructions for installing XP then Ubuntu.  Are there no instructions because XP must be installed first then Ubuntu?  Thanks.

Yes, it is possible to install Ubuntu, then XP.  I've done it.  In order to make sure Windows didn't complain, I gave it a FAT32 primary partition at the beginning of the drive, around 10Gb.  Then, I set up my ext3 partition and swap partition for Ubuntu as logical drives in the Extended Partition.

Then, Grub installs in the Master Boot Record and has entries to boot Ubuntu's kernels.  It might put in the entry to boot the first (empty) partition, but I'm not really sure about that.

Later, when you install Windows XP, it's going to clear out the MBR for you, so you won't be able to boot Ubuntu any more.  How nice of Microsoft, heh?  Don't worry, it's easy to fix.

Pop in your Ubuntu Live CD, when you get to the desktop, go to Applications->Accessories->Terminal.  Put in the following commands.

```
sudo grub
```

This will show you a "grub>" prompt.

```
find /boot/grub/stage1
```

This searches the partitions on your drive for installations of grub, it should give you back something like "(hd0,4)"

```
root (hdx,y)
```

Replace x and y with the numbers that the find command gave you back.

```
setup (hdx)
```

Replace x with the command from above, don't put in the y part, or it will install into your linux partition, not the master boot record.

```
quit
```

Now, restart your computer, take out the live CD when it asks you to, and hopefully you should see grub boot up with your computer.  If there's a windows option, test it and make sure it works.  If it does, skip the rest of this guide, you're done!  If not, or the option isn't there, boot up into your normal Ubuntu install and start up the terminal again.

```
sudo gedit /boot/grub/menu.lst
```

Down near the bottom is the list of boot options for grub.  Now, paste this in at the very bottom:

```
title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

This assumes that Windows XP is the first partition on your hard drive, if it isn't, change the "root" option to point at your Windows install.  If you aren't sure what that is, start the Gnome Partition Editor (in Systems->Administration).  Click on the partition windows is in, and in the bottom box it should highlight the partition in the list box.  If it says /dev/hda3, that is equal to (hd0,2).  /dev/hda1 is (hd0,0) and so on.  Now, save the file and restart and test the windows option.

If it doesn't work, post a message on the boards and let us know what's wrong.

---

### Post by koji126 on 2006-07-25
Thanks for the help! I have just a few more questions I need answered.

In order to partition my hard drive would I need to use GParted?

I have an 80gb hard drive, how much of it should I set aside for XP and Ubuntu?  What happens to the unallocated part of my hard drive?  Would it be possible to store files in that part which can be used by both XP and Ubuntu or is that just not possible.

Thanks again!

---

### Post by BigRedJake on 2006-07-26
I'm not really sure how much you need for each OS, but you should be able to format whatever unallocated space as FAT32.  Both Windows and Linux can read and write to FAT32.

---

### Post by Sef on 2006-07-26
> Are there no instructions because XP must be installed first then Ubuntu? 

If you install Ubuntu before XP, read this: [Recovering Ubuntu After Installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstalling Windows").

>  the live cd, will I be able to install other programs and update a few things or am I stuck using whatever they have available on that cd?


You have to use the programs that are on the CD.


> In order to partition my hard drive would I need to use GParted?

A partitioner is on the install disk.  You can partition with GParted before hand, but it is not necessary.

> I have an 80gb hard drive, how much of it should I set aside for XP and Ubuntu?

I would set aside 10 GB each.  You can make it smaller, if you wanted, but I prefer to have lots of extra room.

> What happens to the unallocated part of my hard drive? 

It would sit there unused.


> Would it be possible to store files in that part which can be used by both XP and Ubuntu or is that just not possible.

Yes. You can use FAT32, ext2 or ext3 partitions.  Both XP and GNU/Linux can read and write to both.

---

### Post by Indras on 2006-07-26
Yes, I have to agree with the above posters.  I would partition like this:

Primary: 10Gb Fat32 or NTFS: Windows XP drive (save empty for later)
Extended:
10Gb ext3: Ubuntu install drive
256Mb+ linux-swap: Size of the swap should generally equal the amount of ram in your system.  Mine is 1Gb
rest fat32: Storage, to be accessable by both OSes

My partitioner of choice has always been Partition Magic, however, I've recently had a bad experience with it hosing my drive while trying to stretch my Ubuntu partition from 5Gb to 10Gb.  Acronis Disk Director is the prettiest partitioner I've ever seen, and I've heard good things about it.  However, both of those options cost $$.

In your shoes, I'd just boot up the live CD and use Gnome Partition Editor and set it all up manually from there.  GPartEd is very fast and effective at creating partitions.  I don't really have any experience using it resize or move partitions, so I can't really say for sure.

Oh, and when you go to install, it will ask you how you want to mount your drive.  Make sure that the ext3 partition gets mounted as /, your Windows XP gets mounted as something descriptive, like /winxp, and your storage partition gets mounted as something useful, like /storage.  That's how mine is set up right now.

---

### Post by Sef on 2006-07-26
> My partitioner of choice has always been Partition Magic, however, I've recently had a bad experience with it hosing my drive while trying to stretch my Ubuntu partition from 5Gb to 10Gb

PM and Linux do not get along.  It is best avoided.

> My partitioner of choice has always been Partition Magic, however, I've recently had a bad experience with it hosing my drive while trying to stretch my Ubuntu partition from 5Gb to 10Gb

The feedback on this one has been positive.

> However, both of those options cost $$.


True.  Your advice about using GParted is right on the money.

---

### Post by jurgenfauth on 2008-03-17
I have a similar problem -- installed Ubuntu first and discovered that I'll need a dual boot setup. I've got another computer that can access the hard drive through an external case, so if necessary, I could do some operations on this drive from another computer, if that makes sense. I do have Acronis. What's going to be the easiest way for me to get to the dual boot from here? If somebody could outline the steps for me I'd very much appreciate it.

---

