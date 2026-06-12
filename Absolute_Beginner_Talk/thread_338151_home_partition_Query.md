---
title: "/home partition Query"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Jaydos on 2007-01-14
Hello All!
I recently switched over to Ubuntu 6.10 after being a long-term windows user, and whilst I found solutions via search for my ATI Drivers and duel monitors - I struggled to find a solution for this question;
As I am just beginning to understand Linux, I am of course going by a lot of Trial and Error - As such I have re-installed about 6 times now (I am un-used to being able to fix things if they are broken :-k) - and some of the things I've tried to duplicate have backfired on me.
With this trial and error process, it doesn't leave me much room to go out and download files by the masses (I end up formatting due to lack of knowledge).
With Ubuntu, is there a way I can setup a /home partition after installing the OS so I can download files without worrying about formatting them possibly in the next hour? Perhaps I should be asking more about is the means of backing up and how to apply a backup.

I apologise for the poor context and train of thought of this thread - Mind is still trying to grasp the conversion. Would still very much appreciate some possibilities on this matter of mine.
Cheers.

---

### Post by aysiu on 2007-01-14
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) is the best way I know how.

---

### Post by energiya on 2007-01-14
The best thing you can do is making a separate partition before installing the OS and mount it as /home. If you are dual-booting you can also make a FAT32 partition and use it for both Ubuntu and Windows.
To save time, you can create a partition backup, so that you don't need to reinstall again and again. Look at [Partimage]("http://www.partimage.org/Main_Page").

---

### Post by housam on 2007-01-14
If you have another partition rather than the root ( / ) , you can resize it and create an ext format partition as a home for your fils using the Gparted partitioning tool.

As for system backup and restore , you can read [this thread]("http://ubuntuforums.org/showthread.php?t=81311&highlight=backup+windows+drive").

---

### Post by Jaydos on 2007-01-14
Thank you all very much for quick replies (especially the backup/restore guide!). Will try these out :).

---

