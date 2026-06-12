---
title: "Is linux: ubuntu so hard to install?"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by Sterbik on 2006-09-25
how to install ubuntu on a partition without having to format it?

---

### Post by MrHorus on 2006-09-25
> **Sterbik said:**
> how to install ubuntu on a partition without having to format it?

Well why do you want to do that?

Reading between the lines, i'm guessing that you perhaps want to install it on a Windows partition but don't want to lose your data?

In that case it can't be done.

---

### Post by az on 2006-09-25
The installer will do all that for you.  You don't even have to create the partition yourself - the installer can find an existing windows partition and shrink it for you.

It is even easier if you juts have free space (unpartitioned)  By default the installer will pick that and install there (You will get several options, with that one being the default).

---

### Post by Brunellus on 2006-09-25
if your main concern is to try Linux without losing any data at all, you can always use the live cd.  Ubuntu's "DESKTOP" CD will boot into a linux system that runs entirely off the CD-ROM:  nothing on your hard drive will be changed unless you instruct it to install itself.

---

### Post by Sterbik on 2006-09-25
I finally started the installation!:) :) 
Everything wen't well.I choosed the partition, i also had free space.You said that if i choose the "RESIZE" option nothing will be formatted. But it read that it has to do with two partitions.I "exadently" pushed the ok button,but it was too late.I didn't know that if you abort the installation you get your other OS (windows xp) "go away". After aborting the installation i restarted my computer. There was no WINDOWS XP BOOT SCREEN, just only an error that my PC could not detect any OS on my HD. In this cases i always have "emergency". I have a copy of windows xp.There was nothing else to do then to format drive C: and reinstall the xp. Is this ubuntu too messed up with windows or i'm just too stupid for linux.:-?

---

### Post by xpod on 2006-09-25
> or i'm just too stupid for linux.

Ubunto is soooo easy that even us stupid gits can manage it mate.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by bulldog on 2006-09-25
> **Sterbik said:**
> I finally started the installation!:) :) 
Everything wen't well.I choosed the partition, i also had free space.You said that if i choose the "RESIZE" option nothing will be formatted. But it read that it has to do with two partitions.I "exadently" pushed the ok button,but it was too late.I didn't know that if you abort the installation you get your other OS (windows xp) "go away". After aborting the installation i restarted my computer. There was no WINDOWS XP BOOT SCREEN, just only an error that my PC could not detect any OS on my HD. In this cases i always have "emergency". I have a copy of windows xp.There was nothing else to do then to format drive C: and reinstall the xp. Is this ubuntu too messed up with windows or i'm just too stupid for linux.:-?

The easy way is to create a new partition in windows.
Free up space but do a couple of defrag's befor you create a new partition.
Then boot the live cd and let Ubuntu install in the new partition you created.

But never stop an install in progress!!!
You better had wait till ubuntu was installed,the chance your windows was unharmed was much bigger than abort an install.

---

### Post by Klaidas on 2006-09-25
Whatever you do - don't cancel the partitioning process :)

---

### Post by steve.horsley on 2006-09-25
When you install Ubuntu onto a drive that already has windows on it, the installer has to do 3 things:
1) resize the windows partition to make room for Ubuntu
2) Create partitions for Ubuntu (default is a system and a swap partition)
3) format the new partitions - put a filesystem on them.

This is all normal. It is not possible to put files on a partition until it is formatted.

After formatting the new partitions, files needed by the bootloader are written there. This is why you shouldn't interrupt the install.

---

