---
title: "More HDD space to Ubuntu after installation ?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by waytorun on 2007-04-19
Hi, how is everybody?


I installed Ubuntu on my XP running laptop using GRUB.

I've assigned 20GB of harddrive to Ubuntu and I'm not sure if that's

enough. I do have some extra space in my HDD.


I was wondering if it is possible to allocate more HDD space to Ubuntu

after the installation. 


Ubuntu seems to be running quite smoothely, but it wouldn't hurt to

have more HDD spac, right? Especially, I do enjoy movies with my laptop

often taking up lots of HDD space.


Advice would be greatly appreciated.

---

### Post by DeeTee on 2007-04-19
There are some utilities out there that you can use to resize/manage partitions. I would look for one that does all this standalone (e.g. before booting into your O.S.)

The only one I can think of off-hand is Paragon Suite of products but that costs money.

A more suitable solution would be to create a new partition of whatever size you wish and mount that in a place where you can store your movies/music etc.. 

If you let me know which solution would be better for you I can expand a bit further on either topic.

---

### Post by Sef on 2007-04-19
> I was wondering if it is possible to allocate more HDD space to Ubuntu

after the installation. 

Yes, it is possible.   I would recommend using [GParted]("http://gparted.sourceforge.net/").

---

### Post by theDaveTheRave on 2007-06-29
I have a similar but different problem.

Basic setup:

ubuntu (6,5GB) on dual boot with XP (3.5) on a primaru HDD of total 10gb (I know it is tiny!)

Secondary HDD of 20GB size - being used as general file storage.

Not surprisingly the Ubuntu updates have gradually taken up more of my primary HDD space (any downloaded software I put onto the second HDD).

What I would like to do is 2 fold.

1 - get Ubuntu to load any extra updates onto a "partition" of the second HDD ( I recon an extra 5GB - or should I try for more??) - particularly get it to default the home folders there also.

2 - use some of the space on HDD to give the system a greater SWAP partition.

I am running a fairly old PC, and AMD760 with 256MB Ram (and it actually runs rather well for my requirements - I'm not a gamer and I generally use it for office / programming work etc.

Plans for future.

I would like to keep hold of the XP partition - just in case!
but would also like to set the box up as a DHCP / FileServer / password protection / filewall / print server etc. for local home network -  but that is a little way down the line - I will probably go over to a Deb Server for this and use a new laptop as my everyday pc. I may add remote logon just for some fun

If anyone could point me in the direction of a howto or thread that may be more suitable with "idiot" style instructions I would be greately appreciative

I've got GParted on my system for playing with the partitions, and cleared a load of "old junk" from the second HDD - so I am basically ready to rock and roll.

thanks in advance.

Dave

---

### Post by molly_001 on 2007-06-29
> **theDaveTheRave said:**
> theDaveTheRave wrote ...

I have a similar but different problem.

  ... Ubuntu updates have gradually taken up more of my primary HDD space 

 I would like to ...

1 - get Ubuntu to load any extra updates onto a "partition" of the second HDD ( I recon an extra 5GB - or should I try for more??) - particularly get it to default the home folders there also.

2 - use some of the space on HDD to give the system a greater SWAP partition.



.
.

One thought before we start: You are always much better off to use the Alternate Install CD of any flavor & version of Ubuntu because it gives you full control over where and how you mount partitions such as /home (in particular /home -- but also /usr and /boot, and others, and actually any mount point you want).

As to your issue ... I do not believe it is possible for you to ask Ubuntu to download and store new updates and packages in a partition different from the one mounted as /(root).

If you can do so, there is probably an option for it in the Synaptic Package Manager, so explore the selections there.

However, see below on how to clean out garbage from your /(root) folder, related to remnants of package upgrades and installations.

As for /home I believe you should have full control over where it mounts.  Explore the Properties of that folder, after of course making an ext3 partition for it on the 20GB drive.  I think that should easily be changed.  You could also make that partition on the 20GB drive and then simply copy over /home material to it, freeing lots of space on your current root.

Finally, to tidy up /(root) and make it more lean, you can [do some cleaning]("http://ubuntuforums.org/showthread.php?t=140920").  Link is at:
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by skymera on 2007-06-29
i have 160gb HD.
i have 40GB widnows
i have 80GB Linux /
i have 40GB Linux /Home

i ave defragged windows from 5gb free sapce to 20gb

---

