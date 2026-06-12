---
title: "Need  backup plan for home"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Joviannm on 2007-05-04
Over the past few months I have been switching over my 2003 server to Ubuntu. FTP, OpenVPN, samba, torrent and Mail are all set, but the last thing I need to do is backups. I was using a Microsoft powertoy called Synctoy before that just synced files from on location to another over network at scheduled times. 

So here is is what I need:
1. syncs files from set drive locations on windows box's to set locations on the Ubuntu server
2. scheduled times
3. fairly easy to setup since I am a beginner.

What do you all suggest for a backup tool and do you have a guide? As I am posting in the Absolute Beginner Talk forum I do not know a lot yet and will most likely need a step by step guide.

Thank you all for any help,
Jovian

---

### Post by piti118 on 2007-05-04
You should look into a program call rsync. Search for rsync in this forum. I'm pretty sure there is a how to somewhere.

---

### Post by starcraft.man on 2007-05-04
[Here]("http://linuxappfinder.com/backupandrecovery/backup") you go :)

Grsync might be what your looking for, its a GUI on top of regular rsync, always useful to learn regular rsync later though :)

---

### Post by piti118 on 2007-05-04
here is one

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_copy_files.2Ffolders_from_remote_Ubuntu_machine_into_local_machine_.28rsync.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_copy_files.2Ffolders_from_remote_Ubuntu_machine_into_local_machine_.28rsync.29)

If you want to schedule it you should look in to

1) how to ssh with no password [http://www.debianadmin.com/ssh-your-debian-servers-without-password.html](http://www.debianadmin.com/ssh-your-debian-servers-without-password.html)
2) crontab [http://doc.gwos.org/index.php/Crontab](http://doc.gwos.org/index.php/Crontab)

Hope this helps :)

---

### Post by Joviannm on 2007-05-04
Thank you all very much for your suggestions I will look into all of them =)

---

### Post by starcraft.man on 2007-05-04
Your welcome, feel free to ask more questions, we MUST meet our monthly quotas or the master slave driver Tux *looks around to see if hes watching* will whip us :p

---

