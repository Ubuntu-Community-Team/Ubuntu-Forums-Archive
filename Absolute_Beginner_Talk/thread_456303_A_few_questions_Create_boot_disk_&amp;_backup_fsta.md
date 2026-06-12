---
title: "A few questions: Create boot disk &amp; backup fstab?"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-05-27
1) A. How does one create a "boot" or recovery disc (such as the type  used in windows) if you have boot problems, or is it even necessary? 

B. What would be included in a "linux toolkit" for emergency recovery?

2) A. How do I backup fstab before changes? 

B. How do I "restore fstab/system, in case the changes "goofed" things up?

TY :)

---

### Post by drs305 on 2007-05-27
Make a CD from this site. It most likely has the tool you would need if you have a bootup problem:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

SuperGrub Disk is also a great tool. I think the site is being rennovated but you can find the documentation here:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

and find an ISO of the disk on this mirror:

[http://sgd.howto-linux.de/](http://sgd.howto-linux.de/)

---

### Post by X-626 on 2007-05-27
For a recovery disc, you could just use the Ubuntu Live CD, or for better recovery, you could use SystemRescueCD at: [http://sysresccd.org]("http://sysresccd.org/")

SystemRescueCD has all sorts of things needed to recover a Linux system.  You can see the web site for information on it.

To back up fstab, you could just use the cp command:
```
cp /etc/fstab /destination/of/backup
```/destination/of/backup is the folder where you should store it.

To restore:
```
sudo cp /location/of/backup/file /etc/fstab
```Where /location/of/backup is where you placed the backup file.

It may be best to back it up to an external drive.

---

### Post by discmaster on 2007-05-27
> How do I backup fstab before changes?
Being a newb., maybe that isn't really the (only) question to ask;

Is that what I really need to backup before doing system changes, or are there other things as well? I mean, other than my personal data, etc. I guess I am looking at a way to quickly get back in business in the event that I delete or otherwise hose critical system/other files.

Thanks for the links, BTW, I am looking into that as well.

---

### Post by X-626 on 2007-05-28
If you don't feel comfortable enough making system changes, then I would recommend backing up anything you think could be affected by the change (which will *mostly* be the file you are editing).  However, most of the time system changes won't erase your personal files.  It may prevent you from booting into your system, but something like SystemRescueCD or something else (even the Ubuntu Live CD) like that can help you restore whatever you edited.

After a while, you should begin feeling comfortable editing config files, so you probably won't have to backup files then.  If you are only editing the fstab, that should be the only thing you need to backup, as I don't know of any way of editing it to erase your data (though it never hurts to be too careful).

It is a good idea to backup your personal files to some external source (CD, DVD, flash drive, etc.) every so often, though (no matter how little/often you make system-wide changes).  I usually do it every month.

I hope I answered your question right.

---

### Post by drs305 on 2007-05-28
The most complete backup would include making an image of the entire partition using partimage. This app is on the rescue CD. You boot the cd and at the command prompt/terminal type 'partimage' . Then you create an exact copy of the partition you choose. If the partition is 40GB but there is 20GB of data on it, you would need a different partition available to copy it to that had at least 20GB of free space. Of course you would probably then want to copy it to a DVD or CD or have the copied partition on a different hard drive in case of hard drive problems. The program can divide the image into separate pieces to allow the backup to fit on multiple CDs or DVDs. 

You can read more about partimage here:
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

