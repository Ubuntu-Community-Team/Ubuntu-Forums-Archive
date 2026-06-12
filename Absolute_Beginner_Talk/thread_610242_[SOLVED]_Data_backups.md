---
title: "[SOLVED] Data backups"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by ARhere on 2007-11-11
Hey Everyone,

I am planning to move my file server from Windows to Ubuntu, but I want to understand more about data backups, and how to back up non-critical data.

My situation and experience is very similar to the [poster of this thread]("http://ubuntuforums.org/showthread.php?t=271766"), except that I had my file server on Linux before, Red Hat 8.  I had a power loss and something happened to the "file table???" and in an attempt to recover, I made things worse and lost all my data.  I was able to rebuild the important data using back-up DVD's, but it still hurt.  (*My wife was very angry at the loss of a months worth of pictures of our daughters.*) 
 I plan to use RAID mirroring to protect against a hard drive failure, I have a Belkin 1200VA that works well with Linux for power failures, but besides DVD backups, I don't have a device to protect my data against the worst failure... me!  :lolflag:
What are some suggestions?  Backup of all of my data on DVD is impractical due to size, and I am never a big fan of backup software that stores a compressed file that is only readable by the back-up program.

-ARhere

---

### Post by chamberlain2006 on 2007-11-11
Thats a good question.  Often, the best way, I find, is to use a fairly large external drive, and back up your filesystem to a .tar.gz archive once every two weeks or so.  This is pretty easy to do, in terminal, you can type the following:

```

tar -pczf /media/DISK/backup.tar.gz / --exclude=/proc --exclude=/dev --exclude=/media --exclude=/mnt --exclude=/tmp

```

That will create an archive of your filesystem.  Make sure to change /media/DISK to the folder where your external drive is mounted.

---

