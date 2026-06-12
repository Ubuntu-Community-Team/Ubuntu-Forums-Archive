---
title: "Is there something wrong with my backup config?"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by baz.g on 2008-04-07
I have the simple backup config, installed by default on ubuntu, setup to the recommended settings, so enable purging of old or imcomplete backups is enabled and set to logarithmic.

but my /var/backup folder just seems to be getting bigger and bigger, i do not see any old backups being removed, right now i have an incremental backup folder for every day back to 15th march, this cant be right surely?

it should be:

1 backup per day from last week
1 per week from last month
1 per month from last year etc.
erase all other backups

right now i have 1 full backup from 2008-03-04, 1 from 2008-03-15 and an inc every single day since then, its just getting a little annoying now as currently its taking up 39 GB and it can only get bigger :(

please someone help :)

---

### Post by ajgreeny on 2008-04-07
Personally I can't understand simple backup's default backup destination of /var, which means that if your disk goes kaput, you're left with no backups at all.  Far better in my opinion to get a cheap external hard disk (Iomega do some great ones) and put your backups there.  As to the logarithmic backups, I'm afraid I can't help, though with my home being 22 GB I would soon fill up any disk I've got with backups if I didn't remove the previous one, if I was using simple backup..

Personally I use grsync for my backups and have the default **not** to delete any files from the backup that I have deleted from the source. That way if I suddenly find I need a file that I deleted a while ago it will staill be there in my backup unless I have since made a file of the same name in the same folder.  Incidentally I also backup my var/cache/apt/archives so if I do need to reinstall, I have all the deb files for any other package installation I need to do.  Give that a try if you have never used it; I think it is better, though I know many don't agree with me.

---

### Post by Tews on 2008-04-07
I have yet to find a backup solution as complete, quick and reliable as Quick-Start!  Developed specifically for Ubuntu, it will do all what you require and more.  

[IMG]http://www.libertymanor.org/menu.png[/IMG]

Read/Get it Here [http://ubuntuforums.org/showthread.php?t=613462]("http://ubuntuforums.org/showthread.php?t=613462")

---

### Post by baz.g on 2008-04-08
thanks tews, gonna try that :)

---

