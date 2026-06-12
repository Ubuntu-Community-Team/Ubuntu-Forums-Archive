---
title: "[SOLVED] Ubuntu Backup"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Powerman2442 on 2008-02-12
There there any program for Ubuntu that makes it so you can manually create a backup restore file so that if something should occur with the Os you can roll back to the backup? I am asking because I found a program called Keep and I had problems earlier when I updated Ubuntu and lost my sound. So I had to completely reinstall. Hopefully someone had used Keep or can give me and idea of another program. I'd like to back up the whole Ubuntu OS state.

---

### Post by klemens on 2008-02-12
i heard sbackup ain't bad but never used it.

if i'm not mistaken it is in the repositerys and can be installed via synaptic.

---

### Post by themusicwave on 2008-02-12
Yes,

There are several programs out there for this purpose.  If you search backup in the Synaptic Package Manager you will find a bunch.

System -> Administration - > Synaptic Package Manager

I recommend the sbackup package it is a Simple bacup utility that can do manual or automatic backups.  You specify what to backup and where to send it

install it with:
 sudo apt-get install sbackup

Then go to System -> Administration -> Simple Backup Config

Now you can set everything up and run a manual backup.

To restore use  System -> Administration -> Simple Backup Restore

I hope this helps.

I am also sure there are other packages out there that other will like more.  Try a few and take you pick.

---

### Post by steve-shinn on 2008-02-12
Or try flyback :-

[http://www.howtoforge.com/creating-snapshot-backups-with-flyback-ubuntu-7.10](http://www.howtoforge.com/creating-snapshot-backups-with-flyback-ubuntu-7.10)

---

### Post by Powerman2442 on 2008-02-12
> **klemens said:**
> i heard sbackup ain't bad but never used it.

if i'm not mistaken it is in the repositerys and can be installed via synaptic.

I tried sbackup and it wouldn't install correctly for some reason. Not sure... :-S I will try it agian though.

Update: Hey it worked this time. Thanks.

---

