---
title: "Just finished installation, now what?"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by Scintillement on 2006-07-22
Well I installed Ubuntu. I chose the second option when partitioning, the one to erase disk. Does that mean my Windows and everything that used to be there is gone for good? Please say it is ^_^.

Now I have this orange box next to the sound and clock icons. It says there are 41 updates available. Updates for what? Should I click it and see what happens? Are there any of them that I should not install?

Thanks.

---

### Post by taurus on 2006-07-22
First, welcome to Ubuntu.  If you told the installer to use the entire harddrive, than your Windows was bye-bye.  Now that you log in, you can click on the little blue sphere on top panel to fire up firefox and start surfing the web.  And if there is upgrade, do it since there are some security fixes for Dapper.  Now, everything you need should be in Applications so just play around to learn where everything is...

---

### Post by DSn0wMan on 2006-07-22
1- Yes, windows is not gone.

2- Just click the icon and get the updates. Most of them are security related. I haven't had any trouble with them.

---

### Post by Scintillement on 2006-07-22
> 1- Yes, windows is not gone.

So it's not? Even though I chose "erase disk"? If that's the case how do I get rid of it entirely?

> 2- Just click the icon and get the updates. Most of them are security related. I haven't had any trouble with them.

They all seemed to work as they should.

---

### Post by DSn0wMan on 2006-07-22
Oops I meant gone!

---

### Post by taurus on 2006-07-22
Open a terminal, Applications -> Accessories -> Terminal, and see if Ubuntu uses the whole entire disk, erasing Windows, or not!

```

sudo fdisk -l

```

---

### Post by Scintillement on 2006-07-22
> **taurus said:**
> Open a terminal, Applications -> Accessories -> Terminal, and see if Ubuntu uses the whole entire disk, erasing Windows, or not!

```

sudo fdisk -l

```

```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6996    56195338+  83  Linux
/dev/hda2            6997        7296     2409750    5  Extended
/dev/hda5            6997        7296     2409718+  82  Linux swap / Solaris
```

I have no idea what that means heh.

Also if I go to Places>Computer it shows 3 icons;

CD-RW/DVD-RAM Drive, 53.6GBVolume:Root Volume, Filesystem.

If I RightClick>Properties the 53.6GB one it says next to contents:
95065 Items, Totalling 3.0GB (Some Contents Unreadable).

What does that mean?

---

### Post by taurus on 2006-07-22
The output from "fdisk -l" show you the partition of your harddrive.  Looks like you have two partitions on your only one harddrive.  First partition, /dev/hda1, is the Ubuntu is while the first extended partiton, /dev/hda5, is your swap.  Clean and simple, I guess...  And if you want to know how much space Ubuntu uses up or how much space left, you can run this command at the prompt.

```

df -h

```

---

### Post by Scintillement on 2006-07-22
> **taurus said:**
> The output from "fdisk -l" show you the partition of your harddrive.  Looks like you have two partitions on your only one harddrive.  First partition, /dev/hda1, is the Ubuntu is while the first extended partiton, /dev/hda5, is your swap.  Clean and simple, I guess...  And if you want to know how much space Ubuntu uses up or how much space left, you can run this command at the prompt.

```

df -h

```

Thank you very much. So it's okay to have it set up the way it is?

---

### Post by taurus on 2006-07-22
Yes, it's the default.  There is nothing wrong with it although some people would do something like

/boot
/
/home
swap

---

