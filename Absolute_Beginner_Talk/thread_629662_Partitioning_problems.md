---
title: "Partitioning problems"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Nike T on 2007-12-02
So now that 7.10 is out, I requested a cd and got it like yesterday.  I tried installing it again and again I'm having troubles with partitioning.  I used gparted to try to make a separate partition for swap and linux, but whenever I do that it would try to resize the windows partition, it says that it had a problem with resizing it.  I defragged before doing this.  Also after this happens I reboot and it brings up the chkdsk thing.

---

### Post by siciliancasanova on 2007-12-02
Yeah run chkdsk from Windows 2 or 3 times along with defragging before you try and partition.

There are ways around this but try running chkdsk a couple times.

---

### Post by wjp.reg on 2007-12-02
> **Nike T said:**
> So now that 7.10 is out, I requested a cd and got it like yesterday.  I tried installing it again and again I'm having troubles with partitioning.  I used gparted to try to make a separate partition for swap and linux, but whenever I do that it would try to resize the windows partition, it says that it had a problem with resizing it.  I defragged before doing this.  Also after this happens I reboot and it brings up the chkdsk thing.

That's  a toughie.

is there any free space on your HD for linux?

What version of Windows are you running?

When you say you tried gparted to resize the windows partition, how did you do it?  Did you use the gparted live CD or some other method?

If you have booted with a live CD of linux, can you post the output of the following command:

```
sudo fdisk -l
```

---

### Post by Nike T on 2007-12-02
but I didn't run chkdsk, I ran gparted and then when it said there was a problem I looked at the details and then it froze, I had to turn it off using the button and then when it booted it chkdsk ran.  do you know why?

---

### Post by Nike T on 2007-12-02
> **wjp.reg said:**
> That's  a toughie.

is there any free space on your HD for linux?

What version of Windows are you running?

When you say you tried gparted to resize the windows partition, how did you do it?  Did you use the gparted live CD or some other method?

If you have booted with a live CD of linux, can you post the output of the following command:

```
sudo fdisk -l
```

yea there's like 10gigs on the HD.  I'm running XP.  I used the gparted on the live cd, but I have used the live cd and that didn't work either.  I'm on windows right now, so I can't do that, but I'll try it when I boot up linux.  I might do it right now

---

### Post by wjp.reg on 2007-12-02
the ubuntu install partitioner normally tries to use whatever free space is available on your hard disk and you do not need to create a swap and root partition beforehand.

Maybe try deleting any partitions you created previously, not your windows though, ;-)

and re-run the installation to see what happens.  if there is free space there is no need to shrink the windows partition.

---

### Post by Nike T on 2007-12-02
I haven't made any partitions because I was having trouble with that.  When you say free space do you mean unallocated of space that isn't being used on the windows partition, because I can't resize the windows partition to get some unallocated space.

---

### Post by wjp.reg on 2007-12-02
> **Nike T said:**
> I haven't made any partitions because I was having trouble with that.  When you say free space do you mean unallocated of space that isn't being used on the windows partition, because I can't resize the windows partition to get some unallocated space.

Yes, "free" space means unallocated, not something already formatted by an OS; if you don't have any, that is the reason the linux partitioner is wanting to resize your windows partition.

You should be able to resize your windows partition with gparted, but you have ensure it hasn't been "mounted".  Normally there will be a padlock icon displayed if a partition is locked.

---

### Post by Nike T on 2007-12-02
ok, but I have been using gparted, I haven't been using the guided thing on the install list, I use gparted and then it tells me that it cannot be resized for some reason I don't know why, anyways I'm gonna try the live cd and then the code you told me to try

---

### Post by wjp.reg on 2007-12-02
gparted live is a good choice ;-).  If you do succeed in shrinking windows, chkdsk will run the first time you run windows again and that's normal.

---

### Post by Nike T on 2007-12-02
So I ran gparted live, and it didn't work, after it screwed up I saw that there was a sign next the the drive thing and it didn't say the amount on it or used.  Anyways I saw that it had a flag that said boot, does tha thave anything to do with it?  This is really frustrating :confused: :confused:

---

### Post by wjp.reg on 2007-12-02
Sorry Nike T; I don't have anymore suggestions or comments as to why you can't resize the windows partition :-(

---

### Post by Nike T on 2007-12-02
That's ok, thanks for all the help.  I have another question, I would be able to install this on an external hard drive right?

---

### Post by wjp.reg on 2007-12-02
For what it's worth, here is a snapshot of my hard disk as seen by gparted.

---

### Post by Nike T on 2007-12-02
O and also I don't know if this has anything to do with anything but I have this really weird partition in the beginning that's fat16 and it's really really small, do you know what it is?

---

### Post by wjp.reg on 2007-12-02
> **Nike T said:**
> O and also I don't know if this has anything to do with anything but I have this really weird partition in the beginning that's fat16 and it's really really small, do you know what it is?

Best would be if you could post a snapshot of gparted like I did.

---

### Post by Nike T on 2007-12-02
ok

---

### Post by wjp.reg on 2007-12-02
If you see the padlock next to the partition, you need to Select **Partition | unmount** before trying to resize.

---

### Post by Nike T on 2007-12-02
[[IMG]http://img62.imageshack.us/img62/4453/screenshot2fv7.th.png[/IMG]](http://img62.imageshack.us/my.php?image=screenshot2fv7.png)

---

### Post by wjp.reg on 2007-12-02
Wow, you don't have much room left; if you shrink the windows ntfs partition you could run out of room.

An external HD install may suit your situation better.  Don't know what the FAT32 parts are, most likely recovery partitions if you had one of those pre-loaded systems and no system CD.

---

### Post by wjp.reg on 2007-12-02
Here's a[ link for installing on an external HD]("http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/"); sounds like your situation :)

---

### Post by Nike T on 2007-12-02
Thanks a lot, I'll probably do that.

---

### Post by Nike T on 2007-12-02
Ok, I was looking at that, and would I be able to dual boot with it?  I was reading the comments on the site and it was talking about GRUB, that's the bootloader thingy isn't it?  Does anyone know what I would do with that?  And also I should backup everything before partitioning the drive right?

---

