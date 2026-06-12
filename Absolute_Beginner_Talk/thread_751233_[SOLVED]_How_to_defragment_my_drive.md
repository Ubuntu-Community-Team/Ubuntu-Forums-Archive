---
title: "[SOLVED] How to defragment my drive?"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by GoCool on 2008-04-10
I know UBUNTU doesnt require any defragmentation. 

But my secondary hdd was an NTFS and now I made it into ubuntu and recently made it into my primary with all the data still intact (all my pictures and music were stored while it was WindowsXP).  

**_My four questions_**
1. Did it convert everything into ext?

2. Or is it still using the windows partition?

3. Then why is my hdd making so much noise?

4. Is there any way to fix it?

---

### Post by warbread on 2008-04-10
> **GoCool said:**
> 
1. Did it convert everything into ext?


This doesn't make any sense.  Are your files on an EXT3 formatted drive?

> 
2. Or is it still using the windows partition?

3. Then why is my hdd making so much noise?


The two problems are unrelated.

> 
4. Is there any way to fix it?

The noise?  Buy a new hard drive.

But in answer to the question in the title, you want to type in:

```
sudo fsck /dev/hd<X>
```

Where X is the hard drive you want to check.  If your drive is SATA, you'll want 

```
sudo fsck /dev/sd<X>
```

Does that help?

---

### Post by GoCool on 2008-04-10
Sorry for my dumb question, let me try to rephrase it.

1. How to find out what is my file system in my second hdd, is it NTFS or ext3?

2. Before loading ubuntu I did not defrag my disk (when it was WinXP), will it be a matter of concern, for now I don't have winXP its pure Ubuntu.

Is there a tool which apart from check will even fix the drive?

---

### Post by TeoBigusGeekus on 2008-04-10
1) 
```
sudo fdisk -l
```
edit:
That's L, not 1!

2)You can change your /etc/fstab file so that it checks your 2nd drive for errors automatically. You don't need to do anything else.
```
sudo gedit /etc/fstab
```
At the line of your 2nd hd, change the last 0 to 2. This way, every time Ubuntu checks your file system for errors, it will also check your other drive.

---

### Post by bodhi.zazen on 2008-04-10
> **GoCool said:**
> 2. Before loading ubuntu I did not defrag my disk (when it was WinXP), will it be a matter of concern, for now I don't have winXP its pure Ubuntu.

That is not a problem.

> **TeoBigusGeekus said:**
> 1) 
```
sudo fdisk -l
```
edit:
That's L, not 1!

2)You can change your /etc/fstab file so that it checks your 2nd drive for errors automatically. You don't need to do anything else.
```
sudo gedit /etc/fstab
```
At the line of your 2nd hd, change the last 0 to 1. This way, every time Ubuntu checks your file system for errors, it will also check your other drive.

Please use gksu (kdesu for KDE) for graphical applications.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Also, in fstab, use 1 for the root partition, 2 for other partitions.

1= check first at boot, used for root
2= check second, use for all others (I do not think there is a 3,4,5 ... just 0,1,and 2)

man fstab:

> The sixth field, (fs_passno), is used by the [noparse]fsck(8)[/noparse] program to determine the order in which filesystem checks are done at reboot time. The root filesystem should be specified with a fs_passno of 1, and other filesystems should have a fs_passno of 2. Filesystems within a drive will be checked sequentially, but filesystems on different drives will be checked at the same time to utilize parallelism available in the hardware. If the sixth field is not present or zero, a value of zero is returned and fsck will assume that the filesystem does not need to be checked.

---

### Post by TeoBigusGeekus on 2008-04-10
...Sorry for my last post... :oops:
I just editted it...
Misinformed I guess...
Sorry again!

---

### Post by bodhi.zazen on 2008-04-10
> **TeoBigusGeekus said:**
> ...Sorry for my last post... :oops:
I just editted it...
Misinformed I guess...
Sorry again!

LOL

Thank you for that, I was just trying to pass on some information is all.

:popcorn:

---

### Post by GoCool on 2008-04-10
Wow...you are all such wonderful people.

If this is the case then very soon the entire world will go Ubuntu...I think Microsoft might be already feeling the pinch.

---

