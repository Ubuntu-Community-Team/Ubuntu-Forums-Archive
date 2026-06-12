---
title: "Simple backup; problem"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Oki on 2006-11-09
Hi;
I want to make a backup to an extern HD, so if I ever need to install Ubuntu again I could to that, but also get my files, settings, system settings and software back as they where. 

As a newbie I just wanted to try som different programs, and the first is called Simple Backup([http://librenix.com/?inode=7851)](http://librenix.com/?inode=7851)), from synaptic. 

Is this a good application?
It lets me make a backup to this hd, of my /var, /etc, /home and /usr/local folder. But when I press the “Make backup now” I get this message; “A backup run is initiated in the background. The process id is: 22136”. When I check the folder later, it is empty?

Any advice on backup would be great! 

Thanks

---

### Post by zvezdogled on 2006-11-09
I backup my important files to an external hd with rsync.
for exampel if you have external hd mounted to /mnt/ext/ and you want to make  a bckup of your  user home folder /home/user
the comand would be

rsync -av /home/user /mnt/ext/

---

### Post by lowracer on 2006-11-09
I have used the tar command to make backups as well.  tar will do full, incremental, and multi-volume backups as required.

---

### Post by Oki on 2006-11-10
So rsync is the recommended program for backup. But it is not Easy backup:-/ Well, I shall head over to rsync homepage and try learn those commands.

Would be great if the Ubuntu team could make a GUI for rsync for us Windows users he he

I also read somthing about Partimage(or somthing), and I have downloaded the iso file so I shall try that one to. 



Thanks

---

### Post by hyper_ch on 2006-11-10
I think he is rather looking for a full system image backup...

You may want to look here:  [http://www.howtoforge.com/howto_linux_systemimager](http://www.howtoforge.com/howto_linux_systemimager) and [http://www.howtoforge.com/dedicated_server_backup_restore_systemimager](http://www.howtoforge.com/dedicated_server_backup_restore_systemimager)

---

