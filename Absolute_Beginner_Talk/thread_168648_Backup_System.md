---
title: "Backup System"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2006-04-30
How do I back up my system, as system I mean my configurations, files and anything else incase something happens.  I read up on sbackup but I did not understand it.  Can someone give me some advice.:)

---

### Post by pappo on 2006-04-30
sbackup is what I use.
I just loaded it with "sudo apt-get install sbackup".
Once it was finished it appears in "System -> Administration -> Simple Backup Config"
Run that and select "Use recommended backup settings" and it will do your home directory and config files most commonly backed up.  Select "backup now" and it will do a backup immediately and you can see the results.
If you want something specific, select "custom settings" and select the directories you want to save, and the destination you want them to go.
I use a second hard drive for my backups, and point sbackup to that drive for saving the backups.  I created a directory called /backup and used that directory as the mount point for my second drive.  Then I added an /etc/fstab entry so that the second drive is mounted on /backup every time my Ubuntu system restarts.  That way it's always ready to do the backups.

---

### Post by olsonar on 2006-04-30
Most, if not all of your files should be in /home/yourusername. just copy this directory somewhere (CD-RW, external harddrive, etc.) to back it up and that should be all you need. I wish I could help you with sbackup, but it won't work on my system anymore. it worked for a while, then just stopped working for no apparent reason.

---

### Post by therunnyman on 2006-04-30
I do the same thing olsonar does, but manually.  It's a little softshoe I do every morning: look at the logs, look at the file integrity report, scan /home with F-Prot (not needed, it's just fun), sudo mount a partition, sudo cp -r /home /(Backup Partition), sudo umount, done.

Once a week or so, I'll back /home up to CD-RW.  It'll be DVD-RW shortly, I'm sure.

therunnyman

---

### Post by NeoGreen on 2006-05-01
So sbackup will back up all my system files and configurations?  Okay, thanks for the information:)

---

### Post by patrick295767 on 2006-05-03
a partition or harddisk backup can be done via dd command: 

( dd can make image/backup of your disk ...)
[http://patrick295767.sitesled.com/index.html](http://patrick295767.sitesled.com/index.html)
in How to make a backup how your harddisk via Linux (via network also possible)

Greetz

---

