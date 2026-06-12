---
title: "Cannot install either Backup &amp; Restore or backuppc"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2006-10-30
I'm using Dapper6.06 and when I try to install backyppc using synapsis program manager I get thid message:
Error
> E: backuppc: subprocess post-installation
script returned error status 1

When I try to install Backup & Restore I get:
> FATAL ERROR: Backup & Restore
An apt-based error occured and instalation was unsuccessful

Being a noob I don't know where to go from here. I need some help.

Peter

***I need help, therefore I am***

---

### Post by kindafunnylookin on 2006-10-30
....Bump

---

### Post by PhrankDaChickenGeek on 2006-10-30
Don't know what all your needs are, but I use Simple Backup.
It's listed as sbackup. It has an easy to use GUI, and if you have an external HDD once you set it up you can forget it.

---

### Post by kindafunnylookin on 2006-10-31
Thanks for the Simple Backup suggestion. It sounded good to me so I downloaded it and the package manager cannot install that either. I will keep trying to get rid of backuppc - that seems to be the constant with all these problems.

Peter

---

### Post by Elegantly on 2007-01-06
> **kindafunnylookin said:**
> I'm using Dapper6.06 and when I try to install backyppc using synapsis program manager I get thid message:
Error



I got the same error during the installation of BackupPC. If you look at the "Details", you will most likely see that it complains about a missing sendmail binary in /usr/sbin/sendmail.

You can fix the error - for example - by installing postfix (a very good [MTA]("http://en.wikipedia.org/wiki/Mail_transfer_agent")), which will create the required file. However, postifx will not actually install a sendmail binary; the file /usr/sbin/sendmail installed by postfix is rather a kind of wrapper to ensure compatibility with applications that rely on sendmail - just like BackupPC in your case.

Another tip: If you see a prompt after the postfix installation which asks you whether you want an "Internet" or "local only" setup (can't remember the actual terms), just pick "local only".

HTH!

---

### Post by petermck on 2007-01-06
Good advice from Elegantly. I find BackupPC to be a bit of a beast. It's excellent if you are backing up numerous machines on a network, but I find it kind of overkill for just one machine.
you could look a Backup Manager. This was easy to install and setup for one machine and if I recall correctly, it can write to DVD which is convenient.

---

### Post by kindafunnylookin on 2007-02-11
> **petermck said:**
>  I find BackupPC to be a bit of a beast. It's excellent if you are backing up numerous machines on a network, but I find it kind of overkill for just one machine.
you could look a Backup Manager. This was easy to install and setup for one machine and if I recall correctly, it can write to DVD which is convenient.
Well, several crashes and new installations and an upgrade later, backup-manager works for me, thanks for leading me to it.
Peter

---

