---
title: "Installation - Partitions"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by Sarka on 2006-10-10
Hello all,

I got Ubuntu today and I'm currently using it. Once I attempt to install, however, I don't do overly well.

I get to the Partion stage and I get confused and lost. I still want to keep 80GB for Windows and have the other 70 for Ubuntu (If something like that is impossible or just complete rubbish please say so). Once I get here I have no idea at all what to do and everything I do try doesn't work.

So, what do I do now?

[img]http://img174.imageshack.us/img174/6869/confusedbm8.png[/img]

Please help.

Thanks.

---

### Post by bulldog on 2006-10-10
Select the ext3 and create a 10GB / partition,then a 1GB swap and the rest make a /home partition.

This should work.

Try to delete the empty sda4 partition,it's of no use apparently.

Hmmm on a closer look there's something not right.

Where's your windows install??

You should have a 80GB NTFS or something like that and all I see is some strange fat16 and fat32 partitions.

Go back and try again this is not good don't apply!!!

---

### Post by Sarka on 2006-10-10
> **bulldog said:**
> Select the ext3 and create a 10GB / partition,then a 1GB swap and the rest make a /home partition.

This should work.

Try to delete the empty sda4 partition,it's of no use apparently.

Cool, thanks. But if I make the ext3 thingy 10GB big, then will that delete any of the stuff from my hard drive that Windows is on?

And, uh, what is a 1GB swap? And where do I make a /home partition... I am very sorry for my lack of any knowledge. :icon_frown:

EDIT: I thought that the ext3 was my Windows thing. So I have no idea where it is.

EDIT2: Indeed, I see it now.

---

### Post by bulldog on 2006-10-10
See my edit's on the previous post!!

Choose manual partitioning and create the ones I described before.

But be sure your windows is in the list which is not the case I think.

You have a large ext3 partition which you not want.

---

### Post by hyby on 2006-10-10
I envy you. Cause i dont even see that screen!

---

### Post by bulldog on 2006-10-10
> **hyby said:**
> I envy you. Cause i dont even see that screen!

Try the alternate cd if you're PC has not that much RAM.

You shouldn't even try the live cd when you have less then 256MB of RAM.

---

### Post by bulldog on 2006-10-10
> **Sarka said:**
> Cool, thanks. But if I make the ext3 thingy 10GB big, then will that delete any of the stuff from my hard drive that Windows is on?

And, uh, what is a 1GB swap? And where do I make a /home partition... I am very sorry for my lack of any knowledge. :icon_frown:

EDIT: I thought that the ext3 was my Windows thing. So I have no idea where it is.

EDIT2: Indeed, I see it now.

Did you format it this way?

If yes your windows is gone I'm afraid.

You should make free space in windows or gparted **but** you have to defrag windows several times first.

Then you can make a partition for your Ubuntu at your liking.

Then you create in that partition a / ,a swap and a /home.

Swap is used when you ran out of fysical memory.

---

### Post by equal on 2006-10-10
Ok, right now, your Fat16 partition is where Windows is installed.

Ext3 is formatted for Linux, but right now is nothing. What you should do is this:

Delete that Ext3 partition. Then create 3 separate partitions:
1- 8GB Primary partition at the start of the free space, file format Ext3.
2- 512MB Linux-swap partition at the end of the free space. The file format is automatically Swap.
3- Format whatever is left as a Primary partition, Ext3 file format.

After that, it will ask you how to mount each partition. Mount the first one I listed as /, the Swap partition as Swap, and the large partition as /home. The advantage there is, whenever you reformat, you just leave the large partition alone, tell it to mount as /home, and you won't lose all your personal files. /home is where you're going to save your documents/downloads/media files.

Hope this works out for you!

---

### Post by Sarka on 2006-10-10
Oh cool, thanks equal.

Umm, but I have a feeling that I have infact uninstalled Windows from my computer as Windows no longer boots... oops. I shall follow your instructions now.

---

### Post by Sarka on 2006-10-10
Oh wait, it says I can only create 4 partitions.

My fat16 one
My fat32 one
My 512MB Swap one
My 8GB ext3 one

What do I do with all the other stuff? Was I meant to put it in another ext3 partition or something? Or have I done something wrong?

---

### Post by bulldog on 2006-10-10
Windows will **not** be on a fat16 partition!!

Unless you use Win95 or older.

---

### Post by usrtom1 on 2006-10-10
Sarka: you are ahead of me.  The 'live' ubuntu' runs very badly on my laptop. I would like to install on my HD (dedicate it to ubumtu) and can't get started on what to dowload, etc. I have submitted same question before w/ no response. At least, say hi.
usrtom1:( :confused:

---

### Post by bulldog on 2006-10-10
> **usrtom1 said:**
> Sarka: you are ahead of me.  The 'live' ubuntu' runs very badly on my laptop. I would like to install on my HD (dedicate it to ubumtu) and can't get started on what to dowload, etc. I have submitted same question before w/ no response. At least, say hi.
usrtom1:( :confused:

If your spec's are too low you can't use the live cd,use the alternate cd instead.

This is a textbased install,easy to do but no nice GUI to save your RAM.

You must have at least 256MB of RAM to use the live cd and even so I should say,use the alternate cd.

---

### Post by Sarka on 2006-10-10
Oh, hi usrtom1! Uhh, unlucky thar with your installation.

So, umm, what do I do to install Ubuntu - I need to get some OS installed on this computer! How do I format the other 140GB of data? Or where do I put it?

---

### Post by Sarka on 2006-10-10
Righty,

I installed Ubuntu but I just kinda left the other 140GB on it's own. Now I only have 5GB spare space... oops. Is there anything I can do about that?

---

### Post by dannyboy79 on 2006-10-10
> **Sarka said:**
> Righty,

I installed Ubuntu but I just kinda left the other 140GB on it's own. Now I only have 5GB spare space... oops. Is there anything I can do about that?

you are moving a little to fast. please post the output of sudo fdisk -l from a terminal. are you keeping windows? you created a 10gb parition and installed ubuntu on that? what do you mean that you have 5gb of spare space?

---

### Post by Sarka on 2006-10-10
```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1027     8193150   83  Linux
/dev/sda3           19094       19452     2883667+   b  W95 FAT32
/dev/sda4            1028        1092      522112+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

Those are the results.

I mean that in sda3 I only have 5GB of free space even though I have a 160GB hard drive. Is there anyway I can get more space in there?

---

### Post by dannyboy79 on 2006-10-11
> **Sarka said:**
> ```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1027     8193150   83  Linux
/dev/sda3           19094       19452     2883667+   b  W95 FAT32
/dev/sda4            1028        1092      522112+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

Those are the results.

I mean that in sda3 I only have 5GB of free space even though I have a 160GB hard drive. Is there anyway I can get more space in there?

Well, you didn't answer, are you going to be doing a dual boot? If not that everything looks to be ok but we need to resize your ubuntu partition which from the looks of it is sda2. I can't understand what you mean when you state that you installed ubuntu and left 140gb on it's own? that's not what it looks like to me? it looks like you have a dell partition which is probably some kind of restoration partition to return your system back to normal (maybe?) then you have a partition that is formatted for linux, then you have a fat32 partition and then you have a swap partition. i can't tell what each of the sizes are. if you want to resize you linux partition you can just install gparted, then simply open that tool and resize your ubuntu partition to be around 10 or 15 gb and then whatever is left add it to the fat32 partition.

---

