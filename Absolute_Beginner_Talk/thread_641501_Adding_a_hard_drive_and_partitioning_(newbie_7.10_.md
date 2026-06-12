---
title: "Adding a hard drive and partitioning (newbie 7.10 question)"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by Prodromoi on 2007-12-15
Hi,

I've been using Ubuntu 7.04/7.10 for a few weeks now, and I plan to migrate over to it and replace WindowsXP (which I'm becoming more ticked-off with every day!).  I have a question about multiple hard drives and partitions...

I won't be running a dual boot system; I'll keep a separate PC for the few Windows necessities.  I've done a standard Ubuntu install on a single hard drive - a large ext3 boot partition and a small linux-swap within an extended partition.

Now... I'll be wanting to add a second hard drive for data and stuff.  On my Windows boxes I use partitions a lot to keep this safe and compartmentalised.  (I get the impression that partitions are less necessary in Linux.)

But what do I format the partition/s on the second hard drive as?  Do I make an extended partition for the whole drive and put one or more ext3 partitions inside it, or is it more complicated than that?  And will I need to do any drive mounting to use them, or will Ubuntu pick it all up and run with it?

I plan to use PartEd for this - unless anyone has better suggestions.

All help appreciated - thanks in advance.

Al

---

### Post by ajgreeny on 2007-12-15
If you 're sure you won't need to use the partitions in windows, ext3 is probably the best format type to use for the disk, but if you may need to read it sometime in the future with windows then ntfs would be the way to go, ubuntu now being able to read and write to ntfs partitions.
> I've done a standard Ubuntu install on a single hard drive - a large ext3 boot partition and a small linux-swap within an extended partition.When you say boot partition I think you mean root, not boot.  How large is that?  I have so far in 2years of ubuntu never had any other partitions, though many users make a separate /home partition to ease the version upgrade when it is needed.  I just back up all my home folder on a second drive, which I have on the same machine as an experimental disk, to try things out which might break my working system.  So far it has all been easy.

You don't have to work with separate partitions, as you've already found and I wouldn't get too uptight about what is right or wrong, what works for you is right!  If you do want to look at other ways of dealing with partitions, however, I would consider having a separate /home partition, which you can do though it is not absolutely straightforward.  Have a look at [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) which may help you.

---

### Post by Prodromoi on 2007-12-15
Thanks for that... the guide looks like a great help.  Having a separate /home partition seems like a really good move - I have to wonder why it's not a standard thing to do; even an install option.

My current root/boot partition (I called it that because it's where the OS is and thus as a primary partition, it's what I think of as the boot partition) is 36.6GB with the swap partition at 1.6GB on the machine I'm tinkering with.  (I'm only using a small HDD for this, since it's still largely an experiment.)

I'll go with ext3 partition/s on the Linux box, since I definitely want to avoid dual-booting.  The whole point of dumping Windows as much as possible is to get a more reliable network of PCs!  I will very likely - in time - sort out Samba so the Linux machines can see the Windows PC's data partitions.  If the reverse seems true I may make a separate file server with some NTFS partitions on it.  Do I have to mount the NTFS partitions on a Linux box, or will they work as normal from the boot-up?

---

### Post by ajgreeny on 2007-12-15
You will need to mount the partition with an extra line in your /etc/fstab file like this, changing the dev name to suit your machine.

/dev/hdb1       /home/username/linux   ext3    defaults  0  1

You may also need to change the word **defaults** to **rw,auto,user**  to give you user write permission but I'm afraid I am not quite as au-fait with that as others, and you will need to wait for other info on how to do that if needed.  Have a quick look at [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) which gives a lot of info on fstab files and may help you more.  Good luck.

---

