---
title: "Formatting a Hard Drive"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Cheese Roller on 2007-07-27
So, I just put a second HDD, and I want to format it to make it a shared drive between all the computers in my network.

How do I format the drive?

Also, when I format it, will Windows as well as OS X computers be able to access it?

Also, just on a random note... Can I rename the HDD that Ubuntu is installed on? It's not letting me.

---

### Post by Mornedhel on 2007-07-27
To format the drive, unmount it, call GParted to have a GUI for partitioning stuff, and voilà. I recommend FAT32 if it's going to be a multi-OS network.

You can rename the drive, but I don't remember how (and I like to call my drives /dev/sda1, gives more geek credit).

---

### Post by Cheese Roller on 2007-07-27
I should leave it Fat32?

That's what it already was I think...

Anyway though, I haven't formatted it yet since you told me to leave it that way.

It's not letting me rename any of the HDD...

Anybody know how I can do that?

Unlike the "Filesystem" drive, the 2nd one is showing on my desktop.

How can I get rid of it so it only shows when I go to "Computer" like the other one?

---

### Post by hyper_ch on 2007-07-27
I'd go for ext3 and install samba for sharing...

---

### Post by vanadium on 2007-07-27
Indeed, if it is for sharing over the network, better convert it to ext3, the default and robust Linux file system.

Here

[http://www.debuntu.org/device-partition-labeling](http://www.debuntu.org/device-partition-labeling)

I found an extensive howto label partitions. As you see, the procedure depends on the file system of the drive.

---

### Post by Cheese Roller on 2007-07-29
So all I do is type...

$ sudo e2label /dev/sdaX "my new label"

to rename "filesystem" to "Name"?

in that command do I use quotes?

---

### Post by indytim on 2007-07-29
1.  Get a copy of GParted Live
[http://gparted.sourceforge.net/index.php]("http://gparted.sourceforge.net/index.php")
2. Burn the iso image to a CD
3. Boot to the GParted Live
4.  Select your second h/d and do your partition editing as required.

Why GParted Live?  It's a really good utility that you should have in your arsenal of maintenance tools irregardless of the ops.  Also, by booting to it you get around all of the sudo stuffola associated with using it as part of the running ops.

My recommendation, as already suggested by another respondant, is to partition to ext3 and get Samba up and running if your need to share things in the Windows world.

Hope this is of some benefit.

IndyTim

---

### Post by jhvillegas2 on 2008-01-09
how do you unmount a drive?

I am trying to format my ext3 hard drive and swap drive and leave them blank so that I can hock my computer.  What are the to-do steps to accomplish this?

Thanks,
jhvillegas2

---

### Post by ugm6hr on 2008-01-09
> **jhvillegas2 said:**
> how do you unmount a drive?

I am trying to format my ext3 hard drive and swap drive and leave them blank so that I can hock my computer.  What are the to-do steps to accomplish this?

Thanks,
jhvillegas2

You want to erase your HD completely?  If so, there are a number of tools to do this securely.  There are a few on here:
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Either download that CD and choose, or follow one of the links under **Hard disk wiping tools**.

I have used Active KillDisk (which will work from a floppy if you want to save on a CDR!)

---

