---
title: "Backing up my system?"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by jeffinhedon on 2006-01-20
Well I have done quite a bit of work on getting my Ubuntu Breezy Badger to work how I want it to....so far so good!!!
Can I "backup" the system I've got so far so that it will not get "lost" 
If I wanted to get back to my current stage if anything went wrong
It would entail a lot of work..to re-input all the settings etc 
So can I run a "backup" to save everthing as it is so that it could be recovered in the event of a catastoph!!!!!!!!!
Any ideas folks;)

---

### Post by Razorback on 2006-01-20
[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

---

### Post by Vengeful Cynic on 2006-01-20
While I definitely encourage you to back up your settings, files, etcetera, I think you'd find that if you had to do a cold load of Ubuntu onto your system, it wouldn't be anywhere near as difficult as your first load.  In fact, I might even encourage you to try backing up your data separately and try doing just that after you've used Ubuntu for a couple of months.  I almost guarantee that the install will be a cleaner one than the one you have now (no old mistakes lurking forgotten in config files, dozens of spare packages that you don't really need, multiple redundant programs installed in that first mad package manager rush, etcetera.)  Just food for thought...

-Vengeful Cynic

---

### Post by oldgoat on 2006-01-20
You might try sbackup - I believe it's in the repositories.  I use it to back up my laptop to a machine with a large hard drive - don't see what good it will do you if you are backed up on the drive that crashes.  A second hard drive would be just as good.  

There is one issue that I know of - there is an option to run automated back ups but I see that a few folks out there are reporting that the automated back up only backs up empty directories.

By default it doesn't back anything up over 100 MB or any multimedia files.  This can be easily changed in sbackup.conf.  Before you go there, you might want to use the search tool  Places > Search for Files...  and search for 'sbackup' in the drop down that reveals 'File System'.  Look for sbackup.conf.example and it should make the configuration changes clear.

Run sbackup from  System > Administration > Simple Backup Config   right below it is Simple Backup Restore.

---

### Post by bulldogzerofive on 2006-01-20
If you want to absolutely with certainty back up everything on your computer no doubts or discussion, there is nothing that beats making drive images, in my humble opinion.

First, you need a liveCD that has partimage on it.  I don't know if the ubuntu one has it but knoppix does.

Second, you need either enough disk space on a seperate partition or external HD (my prefered option), or a CD burner in addition to the drive that the live CD is running from

Then, just start the computer from the live cd, open an command line, and type:

```
sudo mount -rw <name of partition to back up>
sudo mount -rw <name of partition to copy file to>
sudo partimiage
```

Then follow the steps in the partimage GUI and you are good to go.

Good Luck!

---

