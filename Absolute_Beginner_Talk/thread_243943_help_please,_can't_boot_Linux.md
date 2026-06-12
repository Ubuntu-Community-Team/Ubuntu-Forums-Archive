---
title: "help please, can't boot Linux"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by worawutkk on 2006-08-25
Hi all,

I have a very big problem now. My Linux doesn't boot!! What happened is as follows, in step-wise manner.

1. I used Partition magic to creat partitions on my newly bought external harddrive.
2. I booted Linux(I have only one internal harddrive of 200GB, one portion is preserved for Linux: Ubuntu6.06). This time Linux doesn't boot up, with a message saying something like "can't find.... partitions"

Personally I think this is because the new partition in the External harddrive have taken the name formerly used by Linux, and obviously I didn't know that. Windows doesn't seem to see the existence of Linux, and vice versa!!

I tried changing the drive letters of my External harddrive to something like S, T, U which is far beyond D, E, F drive letters normally used, hoping that it might rescue the situation. To no avail, i didn't help.

Anybody help me please???? I would appreciate all the suggestions.


thanks a million
Worawutkk
Reply With Quote

---

### Post by bulldog on 2006-08-25
Well keep it simple and remove your external hdd.
Boot into Ubuntu and put the external drive back in.

It should be recogniced by your Ubuntu.

---

### Post by TFX360 on 2006-08-25
> **worawutkk said:**
> Hi all,

I have a very big problem now. My Linux doesn't boot!! What happened is as follows, in step-wise manner.

1. I used Partition magic to creat partitions on my newly bought external harddrive.
2. I booted Linux(I have only one internal harddrive of 200GB, one portion is preserved for Linux: Ubuntu6.06). This time Linux doesn't boot up, with a message saying something like "can't find.... partitions"

Personally I think this is because the new partition in the External harddrive have taken the name formerly used by Linux, and obviously I didn't know that. Windows doesn't seem to see the existence of Linux, and vice versa!!

I tried changing the drive letters of my External harddrive to something like S, T, U which is far beyond D, E, F drive letters normally used, hoping that it might rescue the situation. To no avail, i didn't help.

Anybody help me please???? I would appreciate all the suggestions.


thanks a million
Worawutkk
Reply With Quote


Dear Worawutkk,


Could you run a Live-CD and see what Gparted (System / Administration / Gparted) shows you?



**If** using the **Windows** as startup find a Windows installation cd and recovery mode and do 

```
fdisk /mbr
```

Or you should try ```
fixmbr
``` when you booted with the live-CD in the Terminal. Which wil result in the rewriting of the MBR to Windows like the above.


Kind regards,


TFX[LIST]
[/LIST]

---

### Post by gn2 on 2006-08-25
Have you tried Drive Mapper to re-name all your partitions?

What file system did you use for the partitions created on the external hardrive? ext3?

Are they all logical?

Have you tried unplugging external drive, booting Linux then plugging drive in after booted? 

Sorry no solutions, but hopefully some pointers...

---

