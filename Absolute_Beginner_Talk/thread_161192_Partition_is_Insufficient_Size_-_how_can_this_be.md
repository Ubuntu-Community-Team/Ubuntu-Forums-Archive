---
title: "Partition is Insufficient Size - how can this be?"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by babel on 2006-04-16
[FONT="Verdana"]I just attempted my first installation of Ubuntu. Unfortunately, I was stopped when setup told me that the partitions I was creating were of insufficient size. 

I am using the option to create a dual boot.  I am installing on an old machine I use to practice on**:**20 GB hard drive, of which <4 GB is in use.  Operating system is Windows 98.  256 MB RAM.  I ScanDisked (Windows did fix some errors) and defragmented first.  

I assigned a 10 GB partition to Windows 98, which would leave 10 GB for Ubuntu.  When I tried to create the partitions, Ubuntu setup told me I left insufficient space in the partition (I am not sure if it referring to the partition I left Windows 98 in or the new one for Ubuntu).  I tried 11 GB/9 GB and 9 GB/11GB but got the same error message all three times.

What have I done wrong?  What should I try next?
[/FONT]

---

### Post by gingermark on 2006-04-16
Ubuntu requires at least two partitions - one for the root and home directories (although you can have these on a partition each) and one known as the "swap" partition, which is usually 1.5 - 2 times your RAM (I think).

My advice would be to have your Windows partition at whatever size you like (say 10GB) and then leave the rest as a second unformatted partition. Then, when installing, select the option to install in the largest available free space, and let the installer take care of the details for you.

---

### Post by babel on 2006-04-16
Thank you, Gingermark.

I'm not sure I understand, however, because I received the error notice after I determined the resizing of the existing Windows 98 partition but before I had to specify any size for any additional partitions, such as the Ubuntu.  I'm not even sure if the dual-boot setup even asks for any additional partition sizes.

---

### Post by gingermark on 2006-04-16
I'm suggesting that you delete any non-Windows partitions you might have set up and commit that change. Then, go back to the main partitions menu, and tell the installer to install in the largest free space.

As far as resizing your Windows partition goes, I think I wrongly assumed you had already done that. Are you using the Ubuntu install CD to do that too? If so, I would do that, confirm that change, then make sure the remaining space is unformatted, confirm that change if necessary, and then exit the partitioner, and tell the installer to install ubuntu in the remaining space from the partitioning menu.

---

### Post by babel on 2006-04-16
I am using the Ubuntu CD to resize the Windows partition.  This is the step in installation that I cannot get past.  As far as I know I have only one partition on the harddrive (20 GB).

What I think I am going to have to do is use the manual partitioning option in the install CD.  However, given my pretty feeble knowledge in things like this, I am going to have to read up on partitioning, so I don't end up rendering my computer useless and have to reformat it.

I'm open to any advice.

---

### Post by gingermark on 2006-04-16
Obviously, back up any essential data / files.

You might want to have a look at this brief overview of resizing a partiton: [https://wiki.ubuntu.com/HowtoPartition](https://wiki.ubuntu.com/HowtoPartition)

It might be overkill just for this task, but you could also consider downloading a LiveCD such as Kanotix, which has a graphical partitioning program.

---

### Post by Mustard on 2006-04-16
You can get a slightly smaller live CD (but less user friendly) called System Rescue CD which can run qtparted, which is the same graphical partitioner as the one that Kanotix uses.  Kanotix would definitely be friendlier to use though.

If you have the Ubuntu live CD, and its able to access the internet, you could install gparted while running the Ubuntu live CD and then use gparted.

---

### Post by babel on 2006-04-17
[QUOTE=gingermark]Obviously, back up any essential data / files.

You might want to have a look at this brief overview of resizing a partiton: [https://wiki.ubuntu.com/HowtoPartition](https://wiki.ubuntu.com/HowtoPartition)

It might be overkill just for this task, but you could also consider downloading a LiveCD such as Kanotix, which has a graphical partitioning program.[/QUOTE]

I will read [https://wiki.ubuntu.com/HowtoPartition](https://wiki.ubuntu.com/HowtoPartition) then attempt a manual partition resize.  
My time for major tasks such as this is limited to weekends so I will try it then.

If this fails I will look into the Kanotix program.

Mustard**:** Is System Rescue CD a Ubuntu product or a different OS?  Where do I find it?

---

### Post by joshrobinson on 2006-04-17
[QUOTE=babel]I will read [https://wiki.ubuntu.com/HowtoPartition](https://wiki.ubuntu.com/HowtoPartition) then attempt a manual partition resize.  
My time for major tasks such as this is limited to weekends so I will try it then.

If this fails I will look into the Kanotix program.

Mustard**:** Is System Rescue CD a Ubuntu product or a different OS?  Where do I find it?[/QUOTE]

what do you have 256mb or ram on there?
do custom partitioning, resize windows down to 10 gigs, then delete the other partitions (keep the windows one)

now create one as swap thats 1 or 2 times your ram. if you have 256 make it 512.. 128 make it 256 or so on.. you could always make it a gig if you needed to

then make an ext3 with the mountpoint / as the rest of the leftover space
that should do it for you

---

### Post by babel on 2006-04-18
Thanks, Josh.

Over the weekend I will do a manual partition (& hope I don't screw itup!).  
Will make Windows 10 GB.
Yes, the RAM on this computer is 256.
Will the manual partition choice on the Ubuntu disk give me an option to make a partition for the swap file as well as making one for Ubuntu?

I'm not that knowledgable about computers, and have never done a partition before.  I do know that I want to be able to compute without Windows eventually.

---

