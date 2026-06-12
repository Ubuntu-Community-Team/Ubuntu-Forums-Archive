---
title: "Dapper --&gt; Feisty: what to back up?"
date: 2007-04-06
forum: Apple PPC Users
---

### Post by dpny on 2007-04-06
I'm thinking about upgrading my Pismo from Dapper to Feisty. From what I understand, I should back up my home folder, plus stuff like xorg.conf, samba.conf, mt-daapd.conf, etc. Am I missing anything else?

---

### Post by PapaNerd on 2007-04-07
To be safe, you might want to consider saving the entire /etc directory in addition to /home.  This will preserve many of your critical files (like passwd, shadow, group, hosts, etc.) just in case you need to revert to Dapper or Edgy, plus it will maintain your configurations of other things like apache2, bind, etc. that you may have enabled.

I typically use tar for my backups (since it preserves all the date/time/ownership info).  Example:
sudo mkdir /home/backups
sudo tar -cvf /etc > /home/backups/backup-of-etc~2007MMDD.tar
It is also a good idea to copy your backups off to some external media (external hard disk, CD, DVD, etc.).

In addition, I like to save the /usr/share/backgrounds and /usr/share/sounds directories as the contents of these tend to change from release to release (and I like some of the older ones better).

---

### Post by dpny on 2007-04-08
> **PapaNerd said:**
> To be safe, you might want to consider saving the entire /etc directory in addition to /home.  This will preserve many of your critical files (like passwd, shadow, group, hosts, etc.) just in case you need to revert to Dapper or Edgy, plus it will maintain your configurations of other things like apache2, bind, etc. that you may have enabled.

I typically use tar for my backups (since it preserves all the date/time/ownership info).  Example:
sudo mkdir /home/backups
sudo tar -cvf /etc > /home/backups/backup-of-etc~2007MMDD.tar
It is also a good idea to copy your backups off to some external media (external hard disk, CD, DVD, etc.).

In addition, I like to save the /usr/share/backgrounds and /usr/share/sounds directories as the contents of these tend to change from release to release (and I like some of the older ones better).

Thanks.

---

### Post by ssam on 2007-04-09
if you are running any server software (eg apache, mysql ) it might be storing stuff in /var

---

### Post by dpny on 2007-04-09
> **ssam said:**
> if you are running any server software (eg apache, mysql ) it might be storing stuff in /var

I'm not, but thanks for the tip.

---

### Post by dpny on 2007-04-11
Well, that was a partial disaster.

The upgrade to Edgy, using the gksu method, failed about two thirds of the way through. I traced the problem to a bad symlink to samba. One I removed that I was able to to a dist upgrade and finish the Edgy upgrade. But Edgy seems brittle: I've had to restart several times to fix weird problems: applications launching but not showing up in X, etc.

Maybe I will wipe and install Feisty from the CD.

---

