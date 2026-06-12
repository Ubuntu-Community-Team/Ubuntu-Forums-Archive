---
title: "Help Please!"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Juran on 2007-11-12
Okay. I know I made a statement earlier about wanting to install Ubuntu, but I'd like to partition my disk so I can have my cake and eat it (So to speak)!

So.. I'm at the install part, and its asking me to prepare partitions.. I have this

Device       type        Mount Point       Format?      Size        Used
/dev/hdc
 /dev/hdc1  ntfs        /media/hdc1                      160031MB unknown
free space                                                          8mb

.. And it's totally lost me.

Could I get some assistance?
(This is part 4 of 7 of the install part, by the way)

---

### Post by creeco on 2007-11-12
Do you want to keep windows?

---

### Post by Juran on 2007-11-12
Yes, I want to keep windows so I can play my few remaining PC games on it. :)

---

### Post by overdrank on 2007-11-12
> **Juran said:**
> Okay. I know I made a statement earlier about wanting to install Ubuntu, but I'd like to partition my disk so I can have my cake and eat it (So to speak)!

So.. I'm at the install part, and its asking me to prepare partitions.. I have this

Device       type        Mount Point       Format?      Size        Used
/dev/hdc
 /dev/hdc1  ntfs        /media/hdc1                      160031MB unknown
free space                                                          8mb

.. And it's totally lost me.

Could I get some assistance?
(This is part 4 of 7 of the install part, by the way)

HI maybe this link will help
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
You will have to create a root partition for ubuntu and a swap. You an also create a home partition also. If you want to keep windows then you will have to resize the windows partition to make room for Ubuntu. Good luck!

---

### Post by Juran on 2007-11-12
Sadly I don't think that'll work for me, because my disk is set down as NTFS, I was told I might need to have something done about that to help me create the said partitions?

---

### Post by overdrank on 2007-11-12
> **Juran said:**
> Sadly I don't think that'll work for me, because my disk is set down as NTFS, I was told I might need to have something done about that to help me create the said partitions?

Yes you will have to resize your windows (ntfs) partition to make room for Ubuntu partition.

---

### Post by Juran on 2007-11-12
Trying that, using GParted right now (Nifty little tool) but I can't seem to resize it to anything other than 8MB. I think that's due to NTFS?

---

### Post by overdrank on 2007-11-12
> **Juran said:**
> Trying that, using GParted right now (Nifty little tool) but I can't seem to resize it to anything other than 8MB. I think that's due to NTFS?

Ok is it windows xp or vista? I have heard that some users have to resize the vista partition form within vista. You may need to defrag the windows partition a couple of times for it to be resized.

---

### Post by Juran on 2007-11-12
XP Pro, that's what I use.

---

### Post by overdrank on 2007-11-12
> **Juran said:**
> XP Pro, that's what I use.

Ok in that link I posted earlier it speaks of defraging your partition in widows and also about BACKING UP your data. SO please research "how to " install without messing up you windows partition. Good luck! :KS

---

### Post by Maestro23 on 2007-11-12
> **overdrank said:**
> Ok in that link I posted earlier it speaks of defraging your partition in widows and also about BACKING UP your data. SO please research "how to " install without messing up you windows partition. Good luck! :KS

Yes.  And make sure you **defrag** the XP partition before you resize it.

---

### Post by CatKiller on 2007-11-12
> **Juran said:**
> Trying that, using GParted right now (Nifty little tool) but I can't seem to resize it to anything other than 8MB. I think that's due to NTFS?

Recent versions of GPartEd can quite happily resize an NTFS permission. It's been a while since I did it, and that wasn't using the latest version of Ubuntu, but I seem to recall that you have a sliding bar to determine how much you want to shrink the partition. Obviously you can't make it smaller than the data that's already on there, and you want to create enough (more than a few gigs) for Ubuntu.

You'll need to create at least two partitions - one to install Ubuntu on, and one to use as a swap partition - like virtual memory, to use Windows nomenclature. You can create more, if you wish and have the space. The psychocats guide already linked to has some information on possible partitioning strategies.

Defragmenting the partition in Windows will both speed the process up and help to guard against data loss during the resize operation. You should still back up your data in case of power loss or the like. The filesystems that you'll use in Linux do not need defragmenting.

---

### Post by MightyMe on 2007-11-12
I have done exactly the same thing as you are trying to do.

You can let the Ubuntu installer resize your NTFS partition for you automatically and create the ones needed for Ubuntu. I think think this is the default optionl.

In order to make this work you FIRST have to:
1. Defrag your NTFS partition, sometime more than once in order to collect all NTFS files "at one end" of the disk.
2. Note how much free space you have left on your NTFS partition 
3. Tell the Ubuntu installer how large you NTFS partition should be

---

### Post by Juran on 2007-11-12
Thanks! I'm defragmenting right now, and when it's done (Prolly a while, I'll go watch a movie) then I'll give you all a heads up on how it went. Thank you all for your help!

---

### Post by Juran on 2007-11-12
Hi! Update here,

I defragged the disk, but I still don't have a little slider or anything, if I tell it to install on free disk space (Approximately 30GB in size) then it states that there isn't enough free space, etc.

It states: Failed to partition the selected disk: This probably happened because the selected disk or free space is too small to be automatically partitioned.

Kind of stuck in a rut. Any help? :)

---

### Post by Juran on 2007-11-12
Just giving a little bump, hoping for a little more help!

---

### Post by CatKiller on 2007-11-12
I think you have to select the "Guided - resize" option rather than the "use largest free space" option. Since, having not resized the existing partition, you have no free space.

---

### Post by Duck2006 on 2007-11-12
> **overdrank said:**
> HI maybe this link will help
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
You will have to create a root partition for ubuntu and a swap. You an also create a home partition also. If you want to keep windows then you will have to resize the windows partition to make room for Ubuntu. Good luck!

Did you try the link in this post?

---

### Post by Juran on 2007-11-12
Yes, I'm trying that NTFS-Config, and it's telling me to..

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe

however the response to that is:

bash: deb: command not found

---

### Post by Juran on 2007-11-12
Any help, folks? :)

---

### Post by CatKiller on 2007-11-12
You shouldn't need to be messing with NTFS-Config during the installation process. Just make the existing partition smaller and let the installer create its own new partitions that will have the right characteristics.

Lines that start with **deb** aren't commands to be entered at the command line, they are configuration options for the software repositories that Ubuntu can use to install software. If you're interested in the different ways you can install software, then this page might be of use: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Juran on 2007-11-12
It doesn't let me make the existing partition smaller. The only space I can seem to wriggle out of it on the gpartition program is 8MB.

---

### Post by MightyMe on 2007-11-12
Ok, I take it you have one large NTFS partition with Windows on it and you want to dual boot...?

If so, boot into Windows and defrag it a couple of times (depending on how fragmented the disk is).
Then run the installer (presuming Ubuntu 7.10) and let the installer automatically resize your NTFS partition.

---

### Post by CatKiller on 2007-11-12
How full is that partition? Also, for [historical reasons]("http://en.wikipedia.org/wiki/Logical_drive#Extended") there are two types of partitions. If the partition is not "primary" (*ie*, the partition number is greater than 4) then you will need to resize the **logical drive** that is in the **extended partition** before you can resize the extended partition itself. It's difficult to describe without pictures, but if you imagine the partitions to be stretchable boxes, and the logical drive/extended partition to be a box within a box then it might make some sense.

---

### Post by spydon on 2007-11-12
This sounds just like when my harddrive had bad blocks...
Have you checked if your harddrive has badblocks?
You can do it with:
```
sudo badblocks /dev/hda
```
or something like that...

---

### Post by Juran on 2007-11-13
> **CatKiller said:**
> How full is that partition? Also, for [historical reasons]("http://en.wikipedia.org/wiki/Logical_drive#Extended") there are two types of partitions. If the partition is not "primary" (*ie*, the partition number is greater than 4) then you will need to resize the **logical drive** that is in the **extended partition** before you can resize the extended partition itself. It's difficult to describe without pictures, but if you imagine the partitions to be stretchable boxes, and the logical drive/extended partition to be a box within a box then it might make some sense.

How might I do that? I've defragged the PC about 5 times now, but still it's only the 8MB thing.

---

### Post by overdrank on 2007-11-13
> **Juran said:**
> How might I do that? I've defragged the PC about 5 times now, but still it's only the 8MB thing.

HI can you choose manual for the partition? If so post a screen shot of the manual window please.

---

### Post by bulldog on 2007-11-13
Please post the output of```
sudo fdisk -l
``` to the forum.

---

### Post by CatKiller on 2007-11-13
> **Juran said:**
> How might I do that? I've defragged the PC about 5 times now, but still it's only the 8MB thing.

[Here's an image]("http://gparted.sourceforge.net/screens/gparted_1_big.jpg") to show you what I'm talking about. If you look at the picture, you'll see that hda4 (a "primary" partition, since it's one of the first four) is listed as an "extended" partition. That means that it can have other partitions inside it - "logical drives". In this case, all of the partition is taken up by another partition, hda5. You can see that hda5 is inside hda4 by the fact that hda5 is indented in the list beneath hda4, and also that the box marked /dev/hda5 is within a cyan box, which is the colour of hda4 in the list. There could be many different partitions inside hda4, but in this case there is only one.

Does that make sense?

Also, I'll third the request that you give some indication of how it's partitioned now, so that we can give you more definite answers.

---

### Post by Juran on 2007-11-13
> **bulldog said:**
> Please post the output of```
sudo fdisk -l
``` to the forum.

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01280128

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       19456   156280288+   7  HPFS/NTFS

---

### Post by Juran on 2007-11-13
[IMG]http://i2.photobucket.com/albums/y49/morvior/Screenshot.png[/IMG]

This help too?

---

### Post by overdrank on 2007-11-13
You could try and resize the partition there but I am not going to suggest that you do it because you could loose your data on the windows partition. It is a risk and you will have to decide.

---

### Post by Juran on 2007-11-13
That's the thing, it doesn't let me resize the partition at all.

---

### Post by ByteJuggler on 2007-11-13
OK, try this: 

1.) Boot off the live cd
2.) Open a terminal (Applications->Accessories->Terminal)
3.) Enter at the prompt the following command
```
sudo apt-get install ntfsprogs
```
4.) Enter the command (takes a while):
```
sudo ntfsresize -i /dev/hdc1 >resize.txt
```
5.) Enter the command (takes a while):
```
sudo gedit resize.txt
```

I'm not sure if step 3 is required or not (meaning I don't know offhand if ntfsprogs is installed on the liveCD or not), but it won't hurt if it isn't. 

Anyway, post back the output of the 4th command which is opened in an editor by step 5, so you can copy and paste easily. (You can strip out all the percentages if you want.)  This will tell us how much space you can in fact reclaim, then I'll give you a command to manually resize the partition, after which you can start the install process again.

---

### Post by Duck2006 on 2007-11-13
Have you tryed the live cd of gparted?

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by mysticrider92 on 2007-11-13
That warning symbol next to the partition could be the problem... Click on it, and see what the error is. If you could post it here, that would be very useful.

---

### Post by Juran on 2007-11-13
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name        : /dev/hdc1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 160031015424 bytes (160032 MB)
Current device size: 160031015424 bytes (160032 MB)
Checking filesystem consistency ...

<Percentages>

Accounting clusters ...
Cluster accounting failed at 51238 (0xc826): extra cluster in $Bitmap
Cluster accounting failed at 1950982 (0x1dc506): extra cluster in $Bitmap
Cluster accounting failed at 1950983 (0x1dc507): extra cluster in $Bitmap
Cluster accounting failed at 1950984 (0x1dc508): extra cluster in $Bitmap
Cluster accounting failed at 19130070 (0x123e6d6): missing cluster in $Bitmap
Cluster accounting failed at 19130071 (0x123e6d7): missing cluster in $Bitmap
Cluster accounting failed at 19130072 (0x123e6d8): missing cluster in $Bitmap
Cluster accounting failed at 19130073 (0x123e6d9): missing cluster in $Bitmap
Cluster accounting failed at 19130182 (0x123e746): extra cluster in $Bitmap
Cluster accounting failed at 19130183 (0x123e747): extra cluster in $Bitmap
Filesystem check failed! Totally 20 cluster accounting mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.

---

### Post by mysticrider92 on 2007-11-13
Your NTFS partition has a problem. You will need to reboot into Windows and run the program 'chkdsk /f' like that error says. Then be sure that your Windows shuts down properly, if it does not, the NTFS log file will give the same error.

---

### Post by Juran on 2007-11-13
Okay. And.. Uhm, I have a teeny little problem, it appears my installer has crashed.. how do I uh, end the process?

---

### Post by Juran on 2007-11-13
Might I add, thank you, mysticrider92, you've helped! ( I think! ), since it's went through and told me that I can actually resize the partition!

---

### Post by Juran on 2007-11-14
although i feel a bit silly asking this question.. When I go onto Manual, and I edit my /dev/hdc1 partition, what I do, in **manual** is i click on my /dev/hdc1 and then click to edit it? My gparted shows

/dev/hdc1 124.04 GiB
unallocated 25.00 GiB

But the installer only detects 8mb of free space. Am i doing something wrong? ;)

---

### Post by ByteJuggler on 2007-11-14
**Do not mess with /dev/hdc1** as that's your Windows partition, except for allowing it to be resized as appropriate.  If you delete it/damage it, you're deleting/damaging your existing Windows installation/data! 

Will the installer not automatically resize the partition now?  If not, I'll post some more commands to manually resize it prior to installation.

---

### Post by Juran on 2007-11-14
All i've done is resize it to give myself some space. The installer won't automatically resize the partition and etc.

---

### Post by Juran on 2007-11-14
Bump? :)

---

### Post by bulldog on 2007-11-14
You see the free space in gparted?
If yes,select it and choose create new partition.
Create a 8GB partition ext3
Create a 1-2GB partition for swap
Create from the rest a partition ext3
Apply changes.

When you install choose manual on the partition part
select the 8GB partition,click next,mount it as  / format ext2 and set the bootflag enable
select the 1-2GB partition select next mount it as swap format as swap
select the last created partition select next mount as /home format ext3
Apply changes to disk and proceed with the install.

---

### Post by Juran on 2007-11-14
i got an error, it said..

ntsfresize -P -i -f -v /dev/hdc1

ntfsresize v1.31.1 (libntfs 9:0:0)
ERROR: Device '/dev/hdc1' is mounted read-write. You must 'unmount' it first.

---

### Post by Juran on 2007-11-14
Bump? :D

---

### Post by Juran on 2007-11-14
[IMG]http://i2.photobucket.com/albums/y49/morvior/Screenshot-1.png[/IMG]


Screenshot of what I'm at. :)

---

### Post by overdrank on 2007-11-14
HI and the windows partition is mounted so you will have to unmount either on the desktop by right clicking or in places, home. By that screen shot there is not much room left on the windows partition and I hope you **BACK UP** your data. Good luck!

---

### Post by Juran on 2007-11-14
> **overdrank said:**
> HI and the windows partition is mounted so you will have to unmount either on the desktop by right clicking or in places, home. By that screen shot there is not much room left on the windows partition and I hope you **BACK UP** your data. Good luck!

I'm sorry, I don't quite understand the instructions?

---

### Post by overdrank on 2007-11-14
> **Juran said:**
> I'm sorry, I don't quite understand the instructions?

In gparted right click (with the mouse) on the windows partition and unmount it.

---

### Post by ByteJuggler on 2007-11-14
The error means the partition is in use (mounted) and can't therefore be resized by GPartEd.  In a terminal window type:

```

sudo umount /dev/hdc1

```

That should unmount, or complain if indeed something else is actually using the partition.  After you've unomounted it, GParted should be able to apply the resizing operations.  

Edit: Or, you can just right click and umount as suggested by overdrank :)

---

### Post by Duck2006 on 2007-11-14
Have you tryed to partition the drive from the gparted live CD not the ubuntru live cd?
Also pmagic is quit a good partitioning tool.

---

### Post by Juran on 2007-11-14
Aha. I managed to unmount, went through the partioning thing and....

[IMG]http://i2.photobucket.com/albums/y49/morvior/Screenshot-2.png[/IMG]

Sorry that I'm being such a pain, guys & gals. :)

---

### Post by Duck2006 on 2007-11-14
I would try partitioning it from the gparted live cd.
Then when it is partitioned then install ubuntu.

---

### Post by ByteJuggler on 2007-11-14
> **Juran said:**
> Aha. I managed to unmount, went through the partioning thing and....
Sorry that I'm being such a pain, guys & gals. :)

Try to do what it suggests, free less space and see if that works.  You don't need such a massive partition for your Linux install (at least not initially).  10GB would be plenty.

---

