---
title: "Looking for Simple, Fast Backup Utility"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by eyemeansit on 2007-04-06
I have been disappointed so far with every backup utility that I have tried in Linux. Here are the things I am looking for in a backup program...

a) Simple, meaning the interface and instructions shouldn't require a computer science degree to figure out. (I'm guessing that Amanda and Mondo are beyond me... though I have not tried them)

b) There should be some visual indication that things are going along nicely toward the goal. (One of the apps I tried recently simply said something like "A backup process has been started. It is process number 6171." Well how on earth are you to tell if it's doing anything, or when it has finished?

c) Speed! As we speak, hubackup is running. It has been running continuously for about 10 hours, and so far the archive created is only up to 14.1GB of the 27GB partition I'm backing up. And its interface tells me it is still "preparing the backup."

d) Reliable. Several of the options I have tried did nothing, as far as I could tell. For example, earlier today I tried KDE Konserve. Several tries produced no files on the destination drive whatever, despite all the humming and spinning of the source drive. Perhaps it was creating an archive file on the source drive before writing it to the destination drive??

If somehow I have missed "THE" Linux backup program, please let me know!

---

### Post by dbbolton on 2007-04-06
check out:
-flexbackup
-afio
-cdbackup


if you would prefer to manually backup, all you really need to do is make archives of important directories like '~' and '/etc' and burn them to a dvd.

some recommend that you keep separate partitions for such directories, but i don't bother.

---

### Post by devnulljp on 2007-04-06
rsync ?

---

### Post by eyemeansit on 2007-04-07
These are all options I haven't looked into yet, but I certainly will! Thanks!

---

### Post by aysiu on 2007-04-07
> **devnulljp said:**
> rsync ?
Or, if you want a graphical interface, *grsync*

More details here:
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

### Post by Trackieman on 2007-04-07
From your comment:
"A backup process has been started. It is process number 6171."
I'm guessing you tried sbackup.
A month ago I was looking for a simple GUI tool to do daily backups of a Linux server to a 500GB removable USB hard drive. I played with sbackup and was unsure if it was doing the job.
As you say - no progress bar, status etc. However the next day I noticed an archive file on the USB drive.
Well that was all a month ago. sbackup for me is working flawlessly.\\:D/ 
The Windows server that I also have to look after with BackupExec 10d with 500GB removable USB hard drive is much more frustrating - It sometimes switches to "paused mode" at the moment of backup. Yea, that's really retarded at 21:00 at night when theres no one there to right click and untick pause.:twisted:

To recap:
Install sbackup from the repositories.
From the Gnome desktop, configure it in System -> Administration -> Simple Backup Config

I have mine set to use custom backup settings, time set to daily at 21:00

---

### Post by zeddock on 2007-04-11
From what I have looked for sbackup seems to be it. However, and as written above, without a progress bar it is far too unnerving.

Hope they add this feature soon, as I really don't care what process it has started on.... because I don't know how to check on that process anyway!

...but I'll bet I could kill it!<laughs>

zeddock.

---

