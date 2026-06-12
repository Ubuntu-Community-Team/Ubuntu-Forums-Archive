---
title: "Dual booting w/Vista - Problems partitioning HD"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by DiasBora on 2007-06-21
Hi all, pretty new to this, so any help would be appreciated.
I'm following the DIY on dual-booting Vista with Ubuntu 7.04. I can't seem to create a partition in my C:/ using the disk managment window on Vista; whenever I do it simply states that there is "insuffecient disk space", yet my HD still has at least 68Gb left and I set the partition to a mere 8Gb (I can't seem to make it more either). 
Did I skip a step or do something wrong?

---

### Post by overdrank on 2007-06-21
> **DiasBora said:**
> Hi all, pretty new to this, so any help would be appreciated.
I'm following the DIY on dual-booting Vista with Ubuntu 7.04. I can't seem to create a partition in my C:/ using the disk managment window on Vista; whenever I do it simply states that there is "insuffecient disk space", yet my HD still has at least 68Gb left and I set the partition to a mere 8Gb (I can't seem to make it more either). 
Did I skip a step or do something wrong?

Hi I just installed Feisty with vista last week with the live cd with no problem. Could you just use the live cd and resize a partition and create one for ubuntu?

---

### Post by tbasherizer on 2007-06-21
The user could, but then Windows' registry might go crazy regarding the perceived hard drive size change.

---

### Post by DiasBora on 2007-06-21
so you're saying I can go ahead and use the live CD with the ISO image to boot up and install, all without partitioning my HD with Vista first?

---

### Post by overdrank on 2007-06-21
> **DiasBora said:**
> so you're saying I can go ahead and use the live CD with the ISO image to boot up and install, all without partitioning my HD with Vista first?

Well you will still have to resize the windows partition for room to install ubunbu but it should give you that option at the partitioning stage of the installation. Good luck:popcorn:

---

### Post by DiasBora on 2007-06-22
that's the problem; i can't create a partition on my C: with Vista. It keeps poping up an error message saying there insuffecient disk space. Is there any software I can use to make partitions with?

---

### Post by DiasBora on 2007-06-22
basically, im trying to create a partition on my C: before installing feisty, but can't because of some odd error message vista keeps poping up. 
i want to be able to dual boot Vista and Ubuntu. Can someone direct me to another method of HD partitioning?

---

### Post by DiasBora on 2007-06-22
I'm using the below DIY, but I'm stuck on the step "shrinking the hard disk"; i keep getting en error message saying theres insuffecient disk space, even though i have 60Gb left on my C: and i just defragmented the disk. 

Where can I find alternative partitioning software? or am I doing something wrong???


[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by silverglade00 on 2007-06-22
1. Right click Computer. Choose Manage. Go to Disk Management. Find your Vista partition (the big one) and right-click it. There is an option to shrink. Choose it.

2. In the resulting box, read the captions carefully. It's not asking how big do you want to make Vista's partition or the new partition, it's asking how much you want to shrink the Vista partition by. Enter the amount of **MB** you want to reserve for Linux. Click on OK. This uses a lot of time.

3. When it is done, reboot to your Ubuntu CD. Create your partitions in the free space and install with the installer.

4. Enjoy! This will also use a lot of time :)

---

### Post by DiasBora on 2007-06-22
> **silverglade00 said:**
> 1. Right click Computer. Choose Manage. Go to Disk Management. Find your Vista partition (the big one) and right-click it. There is an option to shrink. Choose it.

2. In the resulting box, read the captions carefully. It's not asking how big do you want to make Vista's partition or the new partition, it's asking how much you want to shrink the Vista partition by. Enter the amount of **MB** you want to reserve for Linux. Click on OK. This uses a lot of time.

3. When it is done, reboot to your Ubuntu CD. Create your partitions in the free space and install with the installer.

4. Enjoy! This will also use a lot of time :)

_Yes, I'm stuck on step 2_ thats what I've been trying to say this entire time
Vista won't LET me shrink my C: it keeps saying "insuffecient disk space"
I've tried defragmenting to no avail

---

### Post by DiasBora on 2007-06-22
i just tried using diskpart.exe on command prompt, and now I have two unallocated volumes in my HD that I can't merge into a single partition...
how can I 
a) merge the volumes into a single partition
b) shrink my primary C: more?

---

### Post by silverglade00 on 2007-06-22
Sorry, I didn't read your posts correctly before. That was a cut and paste from a howto I wrote a few months back that I thought might help.

Some things that will help us help you:
How big is your hard drive in total?
How big is your Vista partition currently?
How much room are you trying to free up for Ubuntu?
How many partitions are you trying to use for Ubuntu (/, /home, swap, etc.)?

Once you get the free space, you won't have to worry about merging partitions. You can fix all that with the Ubuntu disk. The hard part is to get Vista to let the space go. You probably want to leave a little room (at least a couple GB) on your Vista drive for it's own swap file and other operating files.

---

### Post by DiasBora on 2007-06-23
> **silverglade00 said:**
> Sorry, I didn't read your posts correctly before. That was a cut and paste from a howto I wrote a few months back that I thought might help.

Some things that will help us help you:
How big is your hard drive in total?
How big is your Vista partition currently?
How much room are you trying to free up for Ubuntu?
How many partitions are you trying to use for Ubuntu (/, /home, swap, etc.)?

Once you get the free space, you won't have to worry about merging partitions. You can fix all that with the Ubuntu disk. The hard part is to get Vista to let the space go. You probably want to leave a little room (at least a couple GB) on your Vista drive for it's own swap file and other operating files.

I'm running a HP DV2000 laptop
120Gb hard drive, of which is partitioned into C: (~110Gb) running Vista, and another ~10Gb partitioned into D: as a recovery drive, all from the factory. At this point in time, I have only used 40Gb of the C:, so theres another 60Gb of free space. Also to note is that I've ran the Windows defragmenter program 3 times already, just to be sure the disk is defragmented.

The only thing I've done so far is use Diskpart on DOS/command prompt, but can only free up a meager 2000Mb from the C: and another 700Mb from the D:/.
I just want to free up enough space on the HD, so I have the option to dual-boot either Vista or Ubuntu on startup. I'm just stuck on the partitioning part right now.... please help a newbie

---

### Post by DiasBora on 2007-06-25
the Disk Management on Vista won't let go of more than 2 gigs of HD space, is there soemthing I'm doing wrong?

---

### Post by DiasBora on 2007-06-25
bump?

---

### Post by overdrank on 2007-06-25
> **DiasBora said:**
> the Disk Management on Vista won't let go of more than 2 gigs of HD space, is there soemthing I'm doing wrong?

Have you tried to resize your partition with the live cd?

---

### Post by DiasBora on 2007-06-26
> **overdrank said:**
> Have you tried to resize your partition with the live cd?

so I partition the 2Gb now, use the install CD with the image, and use Ubuntu to resize the partition? then again i'll be installing Ubuntu on the new partitioned drive and its not big enough so how would things work???????????

---

### Post by jasonrandolph on 2007-06-26
Don't trust Windows to successfully partition your hard drive.  If you insist on doing it in Windows, it'll cost you.  Partition Magic is the easiest software to use.  But why not let Ubuntu do it for you?  It's so simple it's almost a joke.  There's a sliding bar that lets you choose the size of your Linux partitions.  

I did it on my Vista system, and it worked perfectly.  Just make sure to check the disc for errors and defrag before partitioning.

---

### Post by tgbrowning on 2007-07-01
I just bought a dv2000 for my daughter yesterday and repartitioned the drive while in Vista using Windows.  While it wasn't exactly a cake walk, it works well enough if you take your time.  I've always repartitioned my hard drive in the past, but used Partition Magic to do it. I wasn't able to locate my PM DVD last night so I went with Windows.

I would strongly suggest that, unless your machine is relatively clean -- within a few days of a factory restore condition, that you first defrag the hard drive and get everything more or less pushed up to the front of the partition.  That could have been the reason you've been having troubles, though it is unlikely. 

Second, I would strongly recommend that not mess with the Recovery partition (D Drive I think).  It might be a good idea, if you have the reovery DVDs made, to pull off all your data and *do* a factory restore to original condition. That would also ensure that the Windows directories and files are shoved to the beginning of the hard drive as well.

[Incidently, the reason I think you should NOT mess with the recovery partition is this:  The partition will probably require extra space when you do a restore, for temp files and what not. If you've watched a Windows upgrade (or for that matter, an Ubuntu install), you should have seen a notice near the end of the process saying words to the effect that temp files are being deleted.]

I assume you've been able to locate the partition program under Disk Management. 

You should have two partitions showing, the Windows partition to the left and the recovery partition to the right.  Both will be listed on two lines below the partition "picture". Click on the C partition.

Now, right click on it and you should generate a context menu, which should have only a few things available. Most should be inactive (grayed out). One of them is Shrink or Change Size. Something like that. Take that option and you'll get a dialog with three text line/spin buttons.  Ignore the top one since you need to have all of the front part of the drive to stay the same -- it's holding Windows.  The middle  portion will be something like a 120000 meg.

The one below that will be a 0. 

Here's where you might get the error message.  If you click on the third one and put in how much you want for your new partition -- the partition program can get confused because [COLOR="Red"]the second line doesn't automatically change[/COLOR]. I noticed that when I repartitioned mine and I did get an error dialog at that point.  Crappy software that it is, the programmer didn't allow for somebody to go to the third line and change it. He only allowed for somebody to do the second line and change it first. 

I would suggest you try changng  your partition size to, oh, about 80000 and then click on the third line, to make sure that it changed correctly. Play around with it a bit because the changes don't occur until you actually tell the program to go ahead and make them.

Once the upper diagram changes to reflect your changes, you will see an undifferentiated block between the C drive and the D drive. You have to go through the entire process again with that partition highlighted so you can have a swap partition for Ubuntu. I put my swap partition to 5 gig, since I had so much space. Way more than you need. 

You're done with the Windows portion of the partitioning. I didn't format the two new partitions since I don't trust windows to do it correctly for a different OS. 

You will need to do the Ubuntu install and when you get past setting your location and language, you'll have the option to repartition the hard drive -- again.  You won't actually need to change the partition sizes at that point. But you do have to tell the program what you want to use the new partitions for.

Take the manual method and then set up the two new partitions they way you want. One of this must be set as "/" and the second as a swap partition. Use the ext3 format for your new Ubuntu partion.

If you run into trouble, let me know and maybe I can walk you through it via Yahoo Messenger.  

Good luck.

Browning>>>

---

### Post by theDaveTheRave on 2007-07-04
DiasBora.


i must admit I have been having a similar problem with new Laptop running VistaHomeBasic and Feisty.

Luckily however the HDD had allready been partitioned by the manufacturer, so I could just throw ubuntu onto the second partition.

I then found that I could access the Vista files but not write to the disk, which is what i really wanted for "transportation" of files etc.

I don't know if you could run the live CD and then "install" the  ntfs-3g 

see the howto [http://ubuntuforum.org/showthread.php=217009]("http://ubuntuforum.org/showthread.php=217009")
 to make the disk read / writable.

Otherwise there is allways fdisk!

Or just go off the rails and get an official copy of XPpro - IMHO it is miles better than homeBasic, and easier to partition stuff with the management tool!

In fact thinking about it... I may have to do this anyway, as i am allready fed up with Vista, and it has only been about 3 weeks - although it does look preety!

Dave

---

