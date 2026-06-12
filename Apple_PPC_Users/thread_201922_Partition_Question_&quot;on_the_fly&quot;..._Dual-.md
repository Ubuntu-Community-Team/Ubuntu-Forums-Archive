---
title: "Partition Question &quot;on the fly&quot;... Dual-Boot G4 iBook w/ Ubuntu &amp; OS X"
date: 2006-06-22
forum: Apple PPC Users
---

### Post by zachws on 2006-06-22
Hello all,

I am brand new to ubuntu and haven't used linux since '01. Anywhoo, my question today is about setting up partitions on OS X, and I assume this is the place to ask.

I would like to partition my OS X hard drive without erasing my present operating system and files. I believe it's called 'on the fly'. The sort of thing you can do with PartitionMagic. Is this possible?

I can handle all the other aspects of installation and learning the ropes. I searched on macupdate and versiontracker for programs that partition and none of them seem to do the trick.

I downloaded the disc a couple of days ago and I am anxious to try Ubuntu out at full speed (not off the live cd).

Thanks,
Zach:-k

---

### Post by zachws on 2006-06-22
any positive experiences with micromat's diskstudio ? or ipartition ?
again this is for 'on the fly repartitioning of a 100gb disk that already has OS X on it. I already read elsewhere that VolumeWorks or whatever is a piece, so I will happily avoid that.

Thanks.

---

### Post by tidris on 2006-06-22
I have read that the parted linux command can resize hfs and hfsplus partitions without erasing them, but I haven't tried it myself.

---

### Post by zachws on 2006-06-22
thanks for the reply,
so with this 'parted': is it on the livecd?

can i run Ubuntu off the cd, use 'parted' to rearrange my HD and install Ubuntu?

---

### Post by tidris on 2006-06-22
[QUOTE=zachws]thanks for the reply,
so with this 'parted': is it on the livecd?

can i run Ubuntu off the cd, use 'parted' to rearrange my HD and install Ubuntu?[/QUOTE]
I just confirmed that parted is in the live desktop CD. so yes, in theory you could shrink the existing hfs partition while booted from ubuntu live CD, then install ubuntu in the free space you just created. 

If I remember what I read correctly,  you would need to turn journaling off in the hfs partition before parted can shrink it. Using the OSX diskutil command is a way to do that.

Read the man page for parted before using it, and do backup the hfs partition before trying to shrink it.

---

### Post by zachws on 2006-06-22
thanks for your help. i think i read the same thing you did and i was able to repartition. i made a 9gb space for ubutu and a 1gb swap file. I FINALLY got to the install screen and it told me i need a "newworld bootstrap". i installed anyway but it doesnt work. i want to scream. i was hoping this would be the linux to bring linux into the light. but it is buggy as hell. i need to partition 3 different sections now? this is ridiculous. please help.

---

