---
title: "Missing Space"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-09-01
I do not understand where my freshly formatted drive space has gone ......

HDD Seagate Barracuda ES ST375064  750GB.  Installed as external USB drive.

I formatted the drive to ext3 and the volume on format is about 698GB which is expected.  However, if I look at the drive properties from Nautilus the available space is 652.5GB.  The only directory present on the drive is Lost+Found and there is nothing there.  There are no other files or directories, not even hidden.

So where has the 45.5GB gone to?   Any ideas?

df -h

Filesystem            Size  Used Avail Use% Mounted on

/dev/sdd1             688G  198M  653G   1% /media/disk

which makes it even more confusing .....

---

### Post by ThrobbingBrain66 on 2007-09-01
I wish I could remember where I found this, but I can't so youll just have to trust me. :)  The ext3 filesystem automatically puts aside 5% of each partition/disk to help avoid running out of space on your / partition, even if the partition isn't /.  In your case 5% of 750 is about 37.5GB

Since your drive is just an external drive, you can safely disable this (set the percentage to 0) altogether with:
```
sudo tune2fs -m 0 /dev/sdd1
```

You shouldn't have to reboot to apply the changes (I didn't) but it can't hurt.

---

### Post by por100pre1 on 2007-09-01
Did you try checking with Baobab? If you don't have it get it:

```
sudo apt-get install gnome-utils
```

Then look for something like Disk Usage Analyzer in Accessories.

---

### Post by expatCM on 2007-09-01
Thanks for the help.

sure I trust you .....  :)

I seem to recall reading recently that tune2fs is a very useful command if you can get to grips with it ...  it can be used to manage the frequency that the file system on drives are checked ...

So ...  I ran the command and it has changed the output from df -h to the following

/dev/sdd1             688G  198M  688G   1% /media/disk

which looks good.  688GB is only a bit different from 698GB so perhaps I should not be picky and quit whilst I am ahead.

However .... I have just had a look with Baobab.  Here I am not sure what I am looking for but it seems to identify only the Lost+Found folder which is fine but it does not give any more information.

---

### Post by ThrobbingBrain66 on 2007-09-01
I should correct my previous post.  I just checked the man page for tune2fs and this is what it says about the 5% allocation

>  *-m reserved-blocks-percentage*
Set the percentage of the filesystem which may only be allocated
              by privileged processes.   Reserving some number  of  filesystem
              blocks for use by privileged processes is done to avoid filesys&#8208;
              tem fragmentation, and to allow system  daemons,  such  as  sys&#8208;
              logd,  to continue to function correctly after non-privileged
              processes are prevented from writing to  the  filesystem.   Nor&#8208;
              mally, the default percentage of reserved blocks is 5%.

---

### Post by expatCM on 2007-09-01
hmmm well that is "interesting".   Since I am only going to use the drive to store DVD's it sounds like I should not have any problems but ...  hey ....  if I understood what it says I may have a different view ....  :)

---

### Post by ThrobbingBrain66 on 2007-09-01
Yeah, I think really the only time it could present an issue is on the / partition.  Even then, if you're a bit paranoid, you could always set it to 1-2%.  I can't imagine that processes need gigabytes of space to do their thing.

---

