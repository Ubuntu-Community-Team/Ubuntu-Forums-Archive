---
title: "rm -r directory"
date: 2005-09-15
forum: Absolute Beginner Talk
---

### Post by d1337 on 2005-09-15
Have I goofed?  I installed a piece of software, vhcs, to play with on my server at home.  It ate too much of my 1 gig of ram, so I decided to scrap it and stick with postfix.  After using the uninstall script from within the software, I still had many of the files left, some of which resided in /var/www/vhcs2.  So, I did the following:
```
cd /var/www
rm -r vhcs2
```which indeed removed the directory.  However, for grins, I ran
```
locate vhcs2
```which shows a bunch of vhcs files still in that directory.  I understand that rm often allows files to be recovered if needed, but should they still be found via locate?  I also think that I should've used **rm -rf** instead.  Any ideas how I might clean my mess up?

d1337

---

### Post by mlomker on 2005-09-15
You need to run **updatedb** to refresh the slocate database.

---

### Post by d1337 on 2005-09-15
Thanks...I never knew that.  Worked like a charm

---

### Post by mlomker on 2005-09-16
[QUOTE=d1337]Thanks...I never knew that.  Worked like a charm[/QUOTE]

It runs as a background process using a cron job, but not very often.  I find myself using that command quite a bit when installing/removing software.  You can exclude directories and whatnot by editing the /etc/updatedb.conf file.

---

