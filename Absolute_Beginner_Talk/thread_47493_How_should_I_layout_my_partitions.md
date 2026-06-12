---
title: "How should I layout my partitions?"
date: 2005-07-08
forum: Absolute Beginner Talk
---

### Post by jamsea on 2005-07-08
I've been using LInux for a bit and I normally just format my whole drive and  put it all on / . However, I have this odd habit of completly screwing up my whole system every few months, and I'm wondering how I should partition my hard drive so I wouldn't have to make so many backups. I want to make a seperate partition for /home and /var mostly, because all my personal files and website are stored in those two places. I have 40 gigs to spare, anyone have any hints as to how much space I should use for each partition? Thanks in advance.

---

### Post by Kvark on 2005-07-08
If you reconfigure your webserver to store the pages in your home then you don't have to make an extra partition for var.

Give the / partition enough space for all the packages you want to install. If you got everything you want now, then looking at how much disk space is used for other things them home and webpages should give a good idea of how big / should be, add some extra on top of that value to make sure you got enough, keep in mind that the temporary files in /tmp/ will also need space from time to time.

Give the swap partition the same size as your ram, making it a bit larger also works.

Give all the space left after that to /home/.

---

### Post by HercuLeeZ on 2005-07-09
Out of habit alone, I would usually format my 40GB HD as follows:

/          == 2GB
/swap  == 512M
/usr     ==  2.5GB
/var     ==  10GB
/home ==   Remainder

Hope that helps

Herc

---

### Post by chaumurky on 2005-11-08
That makes alot of sense - I hadn't thought about seperate /usr and /var partitions. The configs in /etc would still be overwritten on a reinstall so I  personally wouldn't worry about losing the stuff in /usr.

---

