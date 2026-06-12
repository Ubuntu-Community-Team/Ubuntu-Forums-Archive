---
title: "Ubuntu Backup Server"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Benjay on 2007-11-02
Hi, I've recently upgraded my main PC so I have a spare PC hanging about, its specs are 
AMD 1.8ghz processor
1Gig RAM
120GB HDD 
Nvidia GeForce 5200FX

I have installed Ubuntu 7.10 (Gutsy Gibbon) on it. All I currently use it for is hosting a TeamSpeak server.
I was hoping to also use it to make automatic backups of the the other pcs connected to the network
(3x XP,1xVista) 
would be possible to specify which folder i want to be backed up on each PC?
any help greatly appreciated

Thanks

---

### Post by startherepodcast on 2007-11-04
Here is what I would do, though I´ve never tried it out:

Make a Samba Share in your Server with permission so other Computer can write to it.
Make it mount on startup on all the other Ubuntu PCs like this: [http://lists.freebsd.org/pipermail/freebsd-questions/2003-November/025207.html](http://lists.freebsd.org/pipermail/freebsd-questions/2003-November/025207.html) (first google result)

Use a backup software for ubuntu from the repositories or use this guide [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) for backing up everything. Make sure to select the Samba Share as the target for the backup.

Here is a complete guide that covers what u want to do in greater detail:

[http://www.linux.com/feature/118225](http://www.linux.com/feature/118225)

Hope that helped

Leon

---

