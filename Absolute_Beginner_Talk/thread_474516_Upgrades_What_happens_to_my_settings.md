---
title: "Upgrades: What happens to my settings?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by R_U_Q_R_U on 2007-06-15
I have read that the best way to upgrade to each new Ubuntu release is to burn the ISO and install it. This requires a reformat of the of the drive where Ubuntu's current installation resides.

Q: I finally got my Samba server setup and working in 7.04. Let's say I want to upgrade to 7.10 later in the year. How do I save all my Samba settings and other preferences so I don't have to reconfigure everything?

Thanks.

---

### Post by buuntuu! on 2007-06-15
that's why a separate /home partition is useful... your settings will be there and doing a new install will not do them any harm afaik

---

### Post by hyper_ch on 2007-06-15
well, not all settings are there... server/daemon settings are stored in /etc

for samba that would be /etc/samba/*

So backing up /home and /etc is advisable... if you run mysql then the dbs of it are stored in /var/lib/mysql and by default apache sets up the webroot at /var/www

---

### Post by R_U_Q_R_U on 2007-06-15
Thanks for the head's-up. Is there any place in the documentation that lists where all the settings folders are and which ones need to be backed-up?

From what I gather, if I back-up my /home and /etc folders ( and maybe some others) all I have to do is copy them back after doing an install of a new version. Is this correct?

---

### Post by hyper_ch on 2007-06-15
Well, I tend to think

/home
/etc
/var

should cover everything... and not everything in /etc and /var needs to be backed up... just have a look at both folders and you'll see what you need...

---

