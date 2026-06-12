---
title: "Synching between OSX and Ubuntu"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by synecdoche on 2006-06-05
Hi,

I'm new to Ubuntu.  I've used Linux before, but it was several years ago now.  I was looking for a replacement to Windows, but didn't have the time to learn how to use Linux properly to give it its proper due, so I went back to Windows.

However, now that I have an iBook and basically all my Windows machine does is sit there, I figure now might be a good time to give Linux another whirl, because, honestly, the more I use just about anything else, the less I like Windows. :)

Anyhoo, I am planning to dual boot initially, at least until I am comfortable with Linux again, but was hoping to do some advance research about a few things I want to do. 

Well, one thing I want to do, anyway.

I'd like to have the files on my home folder (primarily documents and pictures) on each computer be a mirror.  Obviously there will be some differences, but I mean the documents and whatnot, primarily.  My iBook currently backs things up each night to my portable hard drive, but the more back-ups the better.  Plus, I'd like to be able to access some of the files from either computer.  I don't think this should be too complicated, should it?  

I'd also like Ubuntu to do a back up whereby it writes the folder to an archived file that is named something based on the date fo the backup, so I can burn things to a CD or DVD (it doesn't need to to do this as often).

Also, is it possible to do remote desktop access from my Mac to Ubuntu, and vice versa?  I ran the Live CD on my Mac, and I noticed a remote desktop tool, but as i didn't have anything set up to use it with, I sort of just left it.

Thanks for helping with my newb questions. :)

---

### Post by jpkotta on 2006-06-05
I've never used OS X, but I hear there is a Linux compatibility layer.  So I'm guessing a lot of Linux tools will be available for OS X, or at least will play nicely with it.  I would look at unison.  It runs on Windows and Linux for sure, probably OS X too.  I use it to sync my desktop and laptop.  

Backups of a specific directory are easy:
```
#!/bin/bash
cd $HOME/foo
date=`date +%Y%m%d`
tar zcvf backup-${date}.tar.gz bar
```
This script will back up ~/foo/bar, and name it after the date.  You can make this run automatically by setting up a cron job.

---

### Post by djgrandmarquis on 2006-06-05
Here are some great posts about backing up, I use this method:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

And to backup multimedia I use rsync:
[http://ubuntuforums.org/showthread.php?t=187894](http://ubuntuforums.org/showthread.php?t=187894)

I think you're right, jpkotta, there is a Mac version of Unison available. Sounds like Unison is what you're looking for, synecdoche, since it provides two-way synchronization.
[http://www.cis.upenn.edu/~bcpierce/unison/index.html](http://www.cis.upenn.edu/~bcpierce/unison/index.html)

The remote desktop tool on the Live CD was probably a VNC client. Any VNC (Virtual Network Computing) client can connect to a VNC server. You can run a Mac VNC server and access your computer remotely from a Linux client, and likewise you can run a VNC server on your Linux box (I use x11vnc, highly recommended). I use VNC between Kubuntu and Windoze all the time, and it works great.

---

