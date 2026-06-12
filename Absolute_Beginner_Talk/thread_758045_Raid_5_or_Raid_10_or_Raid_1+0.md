---
title: "Raid 5 or Raid 10 or Raid 1+0"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by rgotten on 2008-04-17
I have being tryaing to build a server and have play installing the Software Raid 5, and reading today found some people advising to yse Raid 10, siunce is faster and more secure:

Is Raid 10 the same as Raid 1+0
Can we do Raid 10 on Ubuntu server
Is there going to be a diferrence with the new version 8.04..Should i wait for it.

I have 3 500 gib har drive..I am newby and I am learning and help will be appreciated

Thanks

rgotten

---

### Post by seepage87 on 2008-04-17
Raid 10 (which is the same as 1+0) does have its benefits, as does RAID 5.  It depends on what you want, need, and what your resources are.

With 3 drives you don't have the option to do RAID 10 since you need at least 4 drives.  It is faster, but it will only be noticeable for writing large files or a large number of files.  Reads will be fast with a RAID 5 too.  10 is also slightly better for not losing your data, though if any 2 drives fail that are coupled, it's the same as 2 drives failing in a RAID 5.

I use RAID 5 because it's much cheaper.  You'll only have one drive lost to redundancy, where in RAID 10, half your drives will be lost.  This won't matter too much if you don't need a lot of space, but I have 7 500GB drives in my RAID 5.  If you're just looking for safety from data loss, RAID6 may do you better than 10 since there's less overhead, though performance isn't as good.

Don't worry about 8.04.  You'll probably be using mdadm for building your array, and I think it runs the same version.

If you let me know your goals I can give you more advice.

---

### Post by rgotten on 2008-04-17
I am completely new to linux and ubuntu, I am a doctor who decided to make a small prohect, create a server and palce my patient data in it. The first step was to create the RAid, and i did with the fopllowing configuration: raid 1 100 mb for boot, raid 0 1 gib for swap and the rest 
for raid 5 that came up to 998 gb. It boot fine but when i disconected one disk to try a failure  it did not boot, and i heard researching that there is a bug on ubuntu and i have to install some commands, That is how i heard about RAID 109 and some people cpmplaining about RAID 5. I also read that the swap on RAID 0 if I have a crash will not work properly (Is this correct? isn't swap for temporary memory?), and i have one more question, I have read about some people doing LVM..Can you advice me on this and what is teh easy way of understanding the LVM

Thanks

rgotten

---

### Post by seepage87 on 2008-04-18
Well, welcome to the Ubuntu and linux communities.  I think this is probably what happened.  When you boot from RAID1, you really are booting from one of the disks in the array since it doesn't recognize arrays just yet.  It isn't until after the boot that your computer will start recognizing the array.  If you removed the disk it was trying to boot from, it won't, by default, know to boot from the second disk.  I know there is a way to get it to boot from the second disk automatically if the first is missing (then the third, etc), but I'm not sure how off the top of my head.  This is probably what you want.

As for the rest which is RAID 5, it boots correctly when all the disks are there?  And you installed ubuntu to the RAID 5?  The reason I ask is because, as I understand it, with a software RAID solution, in order to boot to any array besides 1 you need to customize your boot partition to load mdadm to recognize the array before it boots.  Or are you using a RAID card that came with drivers?

What you may want to do is have /boot be RAID 1 (you've done that), / be RAID 1 as well (set up so even if a disk is gone it will boot to the next, which is identical) with maybe 5GB or something of space, and /patientdata or whatever, as RAID 5 with the rest of the space.  That way you're system would be bootable without too difficult of a setup, with decent redundancy for your patient data.  Or you may want to use a small HDD for your boot and system and use the whole RAID 5 for /patientdata (or whatever you use).  I typically think of the server system as more or less expendable, so no redundancy doesn't bother me.  It's the data I don't want to lose, and if you're system HDD crashes, rebuilding the array on the new install takes almost no time.  Though maybe you need something more reliable than that.

Anyway, I guess what I need to know is, when you remove the disk, where does the boot fail?  Does Grub (the boot menu) start?  If it does, what error does it give trying to load Ubuntu?

As for RAID 0 swap, it's a bad idea.  It seems like a good idea because you would want your swap to be fast, but swap is a back up; if you need it to be fast, or need it much at all, you probably should buy more RAM instead.  That being said, if you have a swap partition on multiple drives, linux knows how to use them efficiently.  It won't do all the writes and reads from one disk when it's got 3 to work with, so RAID 0 won't make it much better.  It is dangerous though, because it makes the data much less reliable; if one drive fails, you're whole swap is broken.  My understanding is that this can corrupt your whole file system if certain things get loaded into swap when it crashes.  It's a small chance, but why take the risk for no gain?

As for LVM, maybe the best way to explain it is via analogy.  It's basically a way to do things on paper instead of committing your physical resources.  Think of your set of hard drives as blocks of wood and partitions as cutting them to size.  Typically you want to take these block of wood and cut them up and structure them to create something functional, e.g. a table.  In practice this table might be a system with a big redundant block for your patient data, a fast block for your operating system, and yet another block for your personal stuff.  

Because you aren't exactly sure how you want this table to look and be shaped and everything, you'd probably draw it out on paper, so that if you wanted you could adjust the length of the legs, or the size and shape of the top, etc, just by changing your drawing.  It's a lot easier to make those changes on paper than first building the table and then deciding you want to cut off some of the legs, or nail on extensions if it's too short, etc.  LVM is sorta the same idea.  Why commit to all these physical specifications when you can just work on paper so if you want to make any changes, it can be done a lot easier.  But since this is a computer and pretending something is real is about as good as it being real, the software helps you pretend that what you drew on paper is real, even though you may just have one big block of wood, or a bunch of small pieces that on paper you've fused seamlessly together better than you could do in real life.  Basically LVM offers flexibility by letting you pretend you made a real partition (or volume), when you really just made one up.  The down side is that, while a table is a table once you make it, and everyone recognizes it as one, if you just draw a sketch of a table, your big chunks of wood are not going to make a whole lot of sense if you lose the diagram.  The same goes for your whole logical volume structure. All the data is still there if something goes wrong, but you won't know which blocks go with each other.  This is generally recoverable though.

With all that in mind, you probably don't need LVM.  RAID lets you do some of it in a sense anyway.   I could use LVM to make my 7 HDDs act like one BIG partition, so I don't have to split all my files into different places.  With RAID I did the same thing.  If you later decide you want to take 200GB of your RAID5 and mount it somewhere else as a new partition, LVM would be useful for that.  It also does a bunch of other stuff, though you may want to make sure you need to do that stuff before you mess around with it.

I hope this has been helpful.  Let me know the exact symptoms of your boot problem, though you might want to

---

### Post by rgotten on 2008-04-18
> **seepage87 said:**
> Well, welcome to the Ubuntu and linux communities.  I think this is probably what happened.  When you boot from RAID1, you really are booting from one of the disks in the array since it doesn't recognize arrays just yet.  It isn't until after the boot that your computer will start recognizing the array.  If you removed the disk it was trying to boot from, it won't, by default, know to boot from the second disk.  I know there is a way to get it to boot from the second disk automatically if the first is missing (then the third, etc), but I'm not sure how off the top of my head.  This is probably what you want.

Thanks for the wellcome, i am trying hard to learn all this, Yes, there is a way to make each disk bootable, and that is what i am working on rigth now, there is also a know bug with some commands to fix, and i will see if i can do that command to fix the bug. Will let you know if this works

> **seepage87 said:**
> As for the rest which is RAID 5, it boots correctly when all the disks are there?  And you installed ubuntu to the RAID 5?  The reason I ask is because, as I understand it, with a software RAID solution, in order to boot to any array besides 1 you need to customize your boot partition to load mdadm to recognize the array before it boots.  Or are you using a RAID card that came with drivers?

Yes, Raid 5 it boot wihotu any problem. No oi am not using cards, just the software...I configure raid 1 / raid 0 swap raid 5 /home..Will you agree with this or will you change anything?

> **seepage87 said:**
> What you may want to do is have /boot be RAID 1 (you've done that), / be RAID 1 as well (set up so even if a disk is gone it will boot to the next, which is identical) with maybe 5GB or something of space, and /patientdata or whatever, as RAID 5 with the rest of the space.  That way you're system would be bootable without too difficult of a setup, with decent redundancy for your patient data.  Or you may want to use a small HDD for your boot and system and use the whole RAID 5 for /patientdata (or whatever you use).  I typically think of the server system as more or less expendable, so no redundancy doesn't bother me.  It's the data I don't want to lose, and if you're system HDD crashes, rebuilding the array on the new install takes almost no time.  Though maybe you need something more reliable than that.

Should i have raid 1 as / or as /boot, or if it is a combination, how do you do it. Somebody in this forum recomended me to use 100mb from each har drive...should i do it 5gb?, the last past i agree, i do not want to lose the data...

> **seepage87 said:**
> Anyway, I guess what I need to know is, when you remove the disk, where does the boot fail?  Does Grub (the boot menu) start?  If it does, what error does it give trying to load Ubuntu?
 
it boots and stops at initrams...

> **seepage87 said:**
> As for RAID 0 swap, it's a bad idea.  It seems like a good idea because you would want your swap to be fast, but swap is a back up; if you need it to be fast, or need it much at all, you probably should buy more RAM instead.  That being said, if you have a swap partition on multiple drives, linux knows how to use them efficiently.  It won't do all the writes and reads from one disk when it's got 3 to work with, so RAID 0 won't make it much better.  It is dangerous though, because it makes the data much less reliable; if one drive fails, you're whole swap is broken.  My understanding is that this can corrupt your whole file system if certain things get loaded into swap when it crashes.  It's a small chance, but why take the risk for no gain?

I have good RAM, is just that following the forum, i read that it should be RAID 0, I belive i also read that i can do the RAID 5 and when i parition it i can do a small slice for swap..No if it is only for virtual memory, and you have a Raid 0, will this be important since is temporary memory..I do not know if i am confuing you, but if you have a good answer will be appreciated

> **seepage87 said:**
> As for LVM, maybe the best way to explain it is via analogy.  It's basically a way to do things on paper instead of committing your physical resources.  Think of your set of hard drives as blocks of wood and partitions as cutting them to size.  Typically you want to take these block of wood and cut them up and structure them to create something functional, e.g. a table.  In practice this table might be a system with a big redundant block for your patient data, a fast block for your operating system, and yet another block for your personal stuff.  

Because you aren't exactly sure how you want this table to look and be shaped and everything, you'd probably draw it out on paper, so that if you wanted you could adjust the length of the legs, or the size and shape of the top, etc, just by changing your drawing.  It's a lot easier to make those changes on paper than first building the table and then deciding you want to cut off some of the legs, or nail on extensions if it's too short, etc.  LVM is sorta the same idea.  Why commit to all these physical specifications when you can just work on paper so if you want to make any changes, it can be done a lot easier.  But since this is a computer and pretending something is real is about as good as it being real, the software helps you pretend that what you drew on paper is real, even though you may just have one big block of wood, or a bunch of small pieces that on paper you've fused seamlessly together better than you could do in real life.  Basically LVM offers flexibility by letting you pretend you made a real partition (or volume), when you really just made one up.  The down side is that, while a table is a table once you make it, and everyone recognizes it as one, if you just draw a sketch of a table, your big chunks of wood are not going to make a whole lot of sense if you lose the diagram.  The same goes for your whole logical volume structure. All the data is still there if something goes wrong, but you won't know which blocks go with each other.  This is generally recoverable though.

With all that in mind, you probably don't need LVM.  RAID lets you do some of it in a sense anyway.   I could use LVM to make my 7 HDDs act like one BIG partition, so I don't have to split all my files into different places.  With RAID I did the same thing.  If you later decide you want to take 200GB of your RAID5 and mount it somewhere else as a new partition, LVM would be useful for that.  It also does a bunch of other stuff, though you may want to make sure you need to do that stuff before you mess around with it.

I hope this has been helpful.  Let me know the exact symptoms of your boot problem, though you might want to

Well i need the option in the future to expand the data storage area...will raid 5 let me expand....

---

### Post by seepage87 on 2008-04-18
As for your setup, I meant to suggest 100MB RAID 1 for /boot, 5GB RAID 1 for /, shave off a little of each drive (maybe 500MB) for swaps but don't RAID them, and put the rest in RAID 5 for /home.

You can expand the array later with RAID 5.  This is the guide I followed to do it:

[http://scotgate.org/?p=107](http://scotgate.org/?p=107)

It's very easy but the process takes a while.  When you want to add your new drive, just format it so there is a partition the same size as the others in the RAID 5.  You can do whatever you want with the rest of the disk, but add that partition to the RAID 5.

Just a note, if you think your array will grow beyond 2TB eventually, you probably should start planning for it now.  Linux won't work with filesystems over 2TB without you doing a little something.  You'll need your RAID 5 to use a GPT partition table, which can handle big partitions.  You can't accomplish this using parted.
```

sudo parted /dev/md0 mklabel gpt

```

For your current boot problem I'm not really sure, since I don't boot from RAID, though your initram probably isn't able to initialize the array properly.  What did you do to get it to boot from the RAID 5 in the first place?  Is there a guide you followed you could post a link to?

---

### Post by rgotten on 2008-04-18
The way i did it came from this two links:
[https://help.ubuntu.com/community/Installation/FileServerWithRAID](https://help.ubuntu.com/community/Installation/FileServerWithRAID)
[http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)

This is also some information i got 
Quote:
a) how big should the boot partition be for the raid 1?  

It only needs to be about 100 Mb (megabytes) because it contains only the boot configuration files and the kernel(s).
Quote:
Since i have the 3 hard drive, should i have the same boot partition areas on each of this 3 hd?  

Yes, I would make a 3-disk array for the RAID1, to be mounted on /boot.
Quote:
c) can i have raid 1 in this 3 equal size partitions, and then do the rest of the partition for each one of the hd for the raid 5 so evrything is on equal sizes?  

Yes, make the rest of the disks into a RAID5, mounted on '/'. You might also want to make a swap partition on the RAID5.
and also got this info:
RAID-5 needs at least 3 disks. The bootable RAID-1 partition is so small, you can just make it a thin slice of your other disks, it won't take up very much space. With software RAID, you can take partitions from the same disks, and make a RAID-1 out of some, and a RAID-5 out of the rest. The operating system software will maintain both RAIDs.

Once you make a RAID, the software treats it just like a single disk, and you can carve up the RAID into different partitions. So, when you install, create a small RAID-1 out of 100 Mb partitions (one from each disk), and then on that RAID-1 device create a single partition, formatted ext3, and assign it the mount point /boot.

Out of the rest of the space on the three disks, make a RAID-5. Once you have created your RAID-5 device, make a 1 GB partition to use as swap, which is a virtual memory space that the operating system uses. From the rest make an ext3 partition to use as your root file system, with the mount point / (called "root"). After you have created these partitions, the installer will automatically put the boot images into the /boot partition, and the rest of the software into /. It will also activate and use the swap partition too.

So as you can see is confusing with so many different opinions; 

Also please expalin the diference between the /boot and the /  cound't the / be on the raid 5 as well as the swap on teh raid 5

Thanks

---

### Post by seepage87 on 2008-04-24
Sorry for the delay.  If you can boot directly to RAID 5, it's fine to make / RAID 5, but you should partition off /home into another RAID 5 so you can reformat your system without losing your patient data.  You may want to make / RAID 1, though.  Keep in mind you don't need much space for / at all, unless you have some plans I don't know about.  Almost everything will be saved to /home.

You could, in principal, put swap on RAID 5, but swap always needs to be on a separate partition, so how you structure it is up to you.  Again, I strongly recommend not making it RAID 0 because you won't see any real benefit to it; linux already knows how to use multiple swap partitions efficiently and it could cause problems.

The boot partition can't be on RAID 5 because you're computer's bios doesn't know how to read that.  When it's RAID 1, it reads the first disk and doesn't even know it's an array.  RAID 5 can't do this because each file is stored across multiple disks.

In summary, I would suggest boot=RAID 1 (100MB is fine), /=RAID 5 or 1 (5GB is probably plenty), /home=RAID 5 or 6 (uses the rest of the space).

---

### Post by seepage87 on 2008-04-24
Sorry for the delay.  If you can boot directly to RAID 5, it's fine to make / RAID 5, but you should partition off /home into another RAID 5 so you can reformat your system without losing your patient data.  You may want to make / RAID 1, though.  Keep in mind you don't need much space for / at all, unless you have some plans I don't know about.  Almost everything will be saved to /home.

You could, in principal, put swap on RAID 5, but swap always needs to be on a separate partition, so how you structure it is up to you.  Again, I strongly recommend not making it RAID 0 because you won't see any real benefit to it; linux already knows how to use multiple swap partitions efficiently and it could cause problems.

The boot partition can't be on RAID 5 because you're computer's bios doesn't know how to read that.  When it's RAID 1, it reads the first disk and doesn't even know it's an array.  RAID 5 can't do this because each file is stored across multiple disks.

In summary, I would suggest boot=RAID 1 (100MB is fine), /=RAID 5 or 1 (5GB is probably plenty), /home=RAID 5 or 6 (uses the rest of the space).

---

### Post by rgotten on 2008-04-25
how can you mount / into one raid 5 and /home into another raid during installation

---

### Post by seepage87 on 2008-04-28
Well, I don't set up my array during installation, but you can do it easy enough after.  Just set up your system with / on RAID 5 normally, and put /home on the leftover space of partition of one disk.  Then use mdadm to add the disks and create a RAID 5 from the /home.  Then resize the /home RAID 5 to take up all the available space of the new MD device.

---

