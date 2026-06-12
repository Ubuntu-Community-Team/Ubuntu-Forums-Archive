---
title: "Resizing partitions on a Windows Dynamic Disk"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by KiwiPete on 2007-02-22
Hi there

On the 6.10 Live CD, GParted refuses to resize partitions on my second hard drive, saying it is "unable to resize partitions managed by Windows Dynamic Disk"

Can anyone tell me if it is possible to resize / create new partitions on such a disk - and if so, how I do it?

Thanks

Kiwi Pete

---

### Post by xyz on 2007-02-22
I don't really have an answer but this may help:
[Restrictions on Extending or Spanning Simple Volumes on Dynamic Disks]("http://support.microsoft.com/?id=225551")

---

### Post by KiwiPete on 2007-03-05
Thanks for the reference but I can't see anything there to help me.

Can anyone else out there help me with this "unable to partition" problem?

KP

---

### Post by KiwiPete on 2007-03-05
Bump.

---

### Post by KiwiPete on 2007-03-07
Bump again!
Does anyone else have any knowledge about this?

---

### Post by KiwiPete on 2007-03-19
Bump yet again.

I'm almost despairing on this.
Every attempt I have made with Parted and Gparted results in the error as stated in my first post.

I'm now considering two options...

1. Buy copy of Partition Magic in the hope that it will allow me to resize existing XP partition and then create new partitions for Ubuntu.

OR

2. Adding another unformatted hard drive and booting into Ubuntu from the live CD and creating partitions on the new drive using GParted.

Any comments or suggestions??

Thanks...

---

### Post by buuntuu! on 2007-03-19
on the livecd you do not have the latest version of gparted. get it [here]("http://gparted.sourceforge.net/") it may or may not help but ut's certainly worth a try using the latest...

---

### Post by KiwiPete on 2007-03-19
Thanks ubuuntuu
I have tried GParted version 0.3.4 and it still doesn't work.
Does anyone have other suggestions?
Thanks

---

### Post by edu65 on 2007-03-19
I once tried Partition Magic 8.0 on a dynamic disk without success. It seems currently only the MS Disk Management application is able to cope with dynamic disks.

You can convert dynamic disks to standard disks, but this will destroy all your data (so make sure you back up all your stuff first).

Have a look at the following link:

How To Convert to Basic and Dynamic Disks in Windows XP Professional:
  [http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)

Further info about dynamic disks:

Understand the differences between basic disks and dynamic disks:
  [http://articles.techrepublic.com.com/5100-10879-5797060.html](http://articles.techrepublic.com.com/5100-10879-5797060.html)

Linux support for Microsoft dynamic disks?:
  [http://uwsg.iu.edu/hypermail/linux/kernel/0105.1/0811.html](http://uwsg.iu.edu/hypermail/linux/kernel/0105.1/0811.html)

The Pain of Dynamic Disks:
  [http://www.serverwatch.com/tutorials/article.php/2190201](http://www.serverwatch.com/tutorials/article.php/2190201)

dynamic disk (glossary):
  [http://mindprod.com/bgloss/dynamicdisk.html](http://mindprod.com/bgloss/dynamicdisk.html)

Good luck



> **KiwiPete said:**
> Thanks ubuuntuu
I have tried GParted version 0.3.4 and it still doesn't work.
Does anyone have other suggestions?
Thanks

---

### Post by KiwiPete on 2007-03-19
Thanks for the reading links.
It looks like I'm stuffed - can effectively reformat the disk or get another hard drive.
Hhmm...

---

### Post by Bhaal on 2007-04-06
Actually there is now a way to resize dynamic disks:
Windows Vista has the ability built-in to the disk-management console.

Although it is said to be less full-featured than some third-party programs like PQ,
it seems to have support for dynamic disks (I have not tried it myself though).

[http://www.vistamania.org/index.php?option=com_content&task=view&id=518&Itemid=34](http://www.vistamania.org/index.php?option=com_content&task=view&id=518&Itemid=34)

Of course it may require actually installing Vista, so it may or may not be usefull to you.
I don't know if Vista has any advanced partition options like that before/during install.
Should be easy to test though.
It's probably even legal to download a pirated Vista, if you only run the setup, use the partition-options during setup, then abort the setup without installing Vista. :-D
Only thing is - I think it requires a CD-KEY early during setup - which you'd have to circumvent - which is probably illegal in itself :confused: 

Hope you find a solution!

---

### Post by KiwiPete on 2007-05-17
It's been a while since my original post on this - and I am still stumped.

The problem in a nutshell is that if WinXP is installed with just ONE partition (taking up the whole drive), and the disk is a Dynamic one, then none of the common partition applications seem to be able to re-partition it. I have tried GParted, Qparted and others with no luck.

Maybe Windows Vista will alow that partition to be altered, but I have no intention to pay $$ for an OS I actuallyu want to get rid of.

Does anyone have any suggestions, other than exporting data and re-formatting the whole drive?

KiwiPete

---

