---
title: "Unable to edit partitions for install"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by jambert-lb on 2006-08-19
I'm using an Acer Aspire 1690 notebook. After suffering a harddrive failure (likely my fault, I won't explain here), I sent it in under warranty and now it's come back with a new harddrive. So, I thought I'd take this opportunity to install a dual boot Ubuntu/Windows XP, which I have been looking into for a few weeks, and trying out various LiveCDs (I'm completely new to Linux).

So, I just got the computer back tonight and decided to take the plunge while the harddrive was still relatively clear and empty.

However, trouble arose when I went to install, during the partition editing part: when manually editing the partitions, the editor told me the maximum and minimum partition size were the same (both the full capacity of the disk).

The disk is formatted to Fat32, I'm unsure why, that was just how Acer did it, and I'm by no means a computer expert (just a *slightly* above average user).

What do I do? I still need Windows XP on this machine... do I just wait and pick up a used box later to do my Linuxing? Or is there some way to unlock the drive for editing?

---

### Post by hellfried on 2006-08-19
have u tried the livecd of gparted? i use it all the time to repartition my hd. google it and burn the iso to a cd like u would any linux distro. throw it into your cd drive and let it work its magic.

---

### Post by jambert-lb on 2006-08-19
I just spent a few minutes downloading and burning the gparted live disc, only to find that it's giving me the same thing:

Minimum size: 76317MiB
Maximum size: 76317MiB

I think I might just have to wait a couple months and buy a used system to install single boot.

EDIT:
Okay, I don't know what happened, I closed the editor, opened it back up, and it's actually working now, by the looks of it: Minimum size is 7734, which is the size of the data I've already got on there. I'm guessing this means those other times it, for one reason or another, didn't properly read what was on the disk...?

Anyways, it should be working now, and I can hopefully go ahead and install Linux... wish me luck! Thanks for your help!

---

### Post by Cryonic on 2006-08-19
It's unlikely you'll be able to resize the fat32 partition, even if you defragment with specialized tools like Perfect Disk (forget about the Windows defragmenter.
I had the same problem last week with my gf's PC, she wanted a dual boot Ubuntu/winXP, and the XP was on fat32, and there was no way I got it to be resizable.
What I did was convert the fat32 to ntfs. Open a DOS box and type:

```
CONVERT  C:  /fs:ntfs
```

where "C:" is of course the letter of your hard drive. You'll be asked two questions, answer both with "yes". Your machine will reboot and perform the conversion. Now your're set to resize partitions.

Btw, don't worry about NTFS not being writeable from Linux. Make the NTFS partition as big/small as you think you'll need for the Windows programs you will install, and use ext3 for the other partitions (except the swap of course). Your "My Documents" folder should go on an ext3 partition. Reason why is you can read/write on ext3 in WinXP with the help of this nifty tool: [http://fs-driver.org](http://fs-driver.org). 

When you partition, this makes a nice dual boot architecture (imo):

one NTFS for WinXP
one ext3 for linux, mount to "/home"
one ext3 for linux, mount to "/"
one swap

Finally, after all installations, I remap the "My Documents" folder from Windows to the <driveletter>:\home of my linux partitions, so that's one folder on ext3 for all user documents.

Keeping user documents on a seperate partition is a good idea if you ever want to upgrade one of your OS'es, since they will be isolated in partitions separate from your own files. I got the idea here: [http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html) (thank you aysiu, really an awesome site !).

---

