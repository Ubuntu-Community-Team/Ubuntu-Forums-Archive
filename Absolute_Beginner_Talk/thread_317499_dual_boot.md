---
title: "dual boot"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by sachincool on 2006-12-12
i ve winxp installed
i want to install ubuntu
can i install it without vmware....dual boot
if i install it on seperate partition
is this the dual booting that what we call

pls help

---

### Post by HokeyFry on 2006-12-12
yes. if you have XP installed first it makes life alot easier. the installer will allow you to change your partition table and whatnot as well. Just be sure to defragment your XP partition first to minimalize data loss.

---

### Post by bulldog on 2006-12-12
> **sachincool said:**
> i ve winxp installed
i want to install ubuntu
can i install it without vmware....dual boot
if i install it on seperate partition
is this the dual booting that what we call

pls help

Just defragment windows several times as suggested.
I advice to download the gparted live cd to re-partition your hard drive.
It's only 30MB,which you have to burn to a cd and boot from it
to get to gparted.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Make minimal 10GB free for ubuntu,more is better.
Create a swap file of about 1GB and format it as swap.
Make the rest of your space an ext3 file system partition which will be your / [root partition] when you install ubuntu.
If you have a lot of free space you can consider to make a / of about 10GB and if you have more space available you can make a separate /home partition,so when you have to do a reinstal for some reason,you can save your data and configuration settings.

---

### Post by sachincool on 2006-12-12
ok
after partitioning and installing ubuntu
can i have choice to boot from either OS
and can i access data from windows partition
pls help
i ll b very thankful

---

### Post by HokeyFry on 2006-12-12
in edgy during install it should configure other partitions for acces automatically. However, no matter what you do the informatio will remain read only, which means you can only look at the data, you cant change it.

---

### Post by AndyCooll on 2006-12-12
See the link in my signature for an excellent guide on how to dual boot. 

:cool:

---

### Post by bodhi.zazen on 2006-12-12
> **sachincool said:**
> ok
after partitioning and installing ubuntu
can i have choice to boot from either OS
and can i access data from windows partition
pls help
i ll b very thankful

Yes you will have choice. Welcome to Ubuntu. It's a whole new world....

---

### Post by bulldog on 2006-12-12
If your windows is on a NTFS partition you can only read [and copy] from this partition.
If it's a FAT32 partition you can read and write to it from within ubuntu.

When you install ubuntu,GRUB will be installed to the MBR of your hard disk.
This is a menu,which you can alter entirely to your likings,where you can choose which OS you will boot.
 You need this to be able to boot ubuntu,so you better not skip this part of the install :cool:

---

### Post by ron999 on 2006-12-12
Hi sachincool (and bulldog)

The GNOME partition editor GParted comes already on the Ubuntu live CD.
You access it from System > Administration
No need to download and burn another disc just for GParted.
:cool:

---

### Post by bodhi.zazen on 2006-12-12
> **ron999 said:**
> Hi sachincool (and bulldog)

The GNOME partition editor GParted comes already on the Ubuntu live CD.
You access it from System > Administration
No need to download and burn another disc just for GParted.
:cool:

Yes, but the gparted is so nice,
[indent]And it is Fluxbox :p[/indent]

---

### Post by bulldog on 2006-12-12
> **bodhi.zazen said:**
> Yes, but the gparted is so nice,
[indent]And it is Fluxbox :p[/indent]

Hi ron999,and bodhi,yep it's nice and much easier to use,in my opinion.
You can take a look and back out without to worry about your data,till you hit apply of course :D

Is it Fluxbox?

---

### Post by bodhi.zazen on 2006-12-12
> **bulldog said:**
> Is it Fluxbox?

Hi Bulldog ;)

Yep, that's Fluxbox :p. Cool isn't it 8) ? Nice example of mix an match with apps from xfce.

And I agree, I prefer gparted for partition management.

One "problem" is mounting partitions.

I solved this by mounting them in /tmp, ie:```
mkdir /tmp/hda1
mount /dev/hda1 /tmp/hda1
```

That also comes in handy to edit fstab and menu.lst (you can tune your partitions from gpartred).

---

### Post by sachincool on 2006-12-12
thanx everybody 
i am goin to do this now

if u want to suggest some more pls suggest it
thanx again

---

### Post by bodhi.zazen on 2006-12-12
> **sachincool said:**
> thanx everybody 
i am goin to do this now

if u want to suggest some more pls suggest it
thanx again

I suggest your next post is from Ubuntu, hard drive edition :twisted:

---

### Post by bulldog on 2006-12-12
As I read back,you must have enough information to complete the install.

Give it a shot,and welcome to Ubuntu.

---

