---
title: "Alternative to Dropbox"
date: 2011-10-05
forum: Apple Hardware Users
---

### Post by canhoto on 2011-10-05
Does someone know an alternative to Dropbox for PPC?

I want to synchronize my most important documents between my Macbook running Mac OS 10.6.8 and my Power Mac running Ubunto 10.04. 

Apparently, most of the backup/synchronize tools (direct or cloud) don't work with Ubuntu for PPC.

There's Unison, but it's really complicated.

Any ideas?

---

### Post by kurt18947 on 2011-10-05
No experience with PowerPC versions but I've been looking at synchronization stuff. Does rsync work on PPC?  If so, is grsync available in the repository? I've been experimenting with that and while there's no synchronization per se,  I've tried backing up one way then the other.  IOW back up folder A to folder B then backup folder B to Folder A.  Both folders appear to contain the same files when I'm done.  There may well be an automated way to do this but by creating 2 sessions it's pretty quick for modest sized folders.  If you can run java stuff, you can look at this:
[http://www.dirsyncpro.org/](http://www.dirsyncpro.org/)
It's a java app that claims to be platform independent.  I installed it and played with it a few minutes but I think I'll stick with rsync/grsync.  One thing that threw me for a couple minutes with dirsyncpro  was USB drives not appearing as a backup destination.  The trick was to navigate to /home/user/media.  The USB driver was there.  This wasn't necessary with grsync; the removable drives appeared as expected. I hope this is helpful for you.

---

### Post by canhoto on 2011-10-06
> **kurt18947 said:**
> No experience with PowerPC versions but I've been looking at synchronization stuff. Does rsync work on PPC?  If so, is grsync available in the repository? I've been experimenting with that and while there's no synchronization per se,  I've tried backing up one way then the other.  IOW back up folder A to folder B then backup folder B to Folder A.  Both folders appear to contain the same files when I'm done.  There may well be an automated way to do this but by creating 2 sessions it's pretty quick for modest sized folders.  If you can run java stuff, you can look at this:
[http://www.dirsyncpro.org/](http://www.dirsyncpro.org/)
It's a java app that claims to be platform independent.  I installed it and played with it a few minutes but I think I'll stick with rsync/grsync.  One thing that threw me for a couple minutes with dirsyncpro  was USB drives not appearing as a backup destination.  The trick was to navigate to /home/user/media.  The USB driver was there.  This wasn't necessary with grsync; the removable drives appeared as expected. I hope this is helpful for you.

I installed both (grsync and dirsyncpro). They seem to work, but I cannot locate my Mac folders when I try to define the directories for sync or backup. I'm connected to it (it appears on my desktop as "sftp at mycomputersname), but it doesn't show when I browse folders on both grsync and dirsyncpro.

Any ideas?

---

### Post by TiBaal89 on 2011-10-06
What about Unison turns you off?  I use it to sync my Mac and Linux machines, it works extremely well (fast and smart about syncing in both directions).  I use it from the command line - I've got the command itself stored in a script and just type 'backupblahblah' into the terminal to do a backup.

---

### Post by canhoto on 2011-10-06
> **TiBaal89 said:**
> What about Unison turns you off?  I use it to sync my Mac and Linux machines, it works extremely well (fast and smart about syncing in both directions).  I use it from the command line - I've got the command itself stored in a script and just type 'backupblahblah' into the terminal to do a backup.


Each time I try to read the manual it seems very complicated to configure!

Am I wrong?

---

### Post by TiBaal89 on 2011-10-06
Like many things, the manual is wildly complicated because the program has tons of options and capabilities.  Simple/normal usage is very easy - I'd look into it more.

To use on the command line it can be as simple as:

```
unison -ui text /some/directory ssh://the.other/computer/
```

---

### Post by canhoto on 2011-10-06
> **TiBaal89 said:**
> Like many things, the manual is wildly complicated because the program has tons of options and capabilities.  Simple/normal usage is very easy - I'd look into it more.


You're right! 

I just didn't care about the Manual, I experimented using the GUI, and it's working!

Great Unison!

Thanks!

---

