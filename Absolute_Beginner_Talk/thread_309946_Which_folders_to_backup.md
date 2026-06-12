---
title: "Which folders to backup?"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by RogerD on 2006-11-30
Hi

I'm planning a backup strategy. Which folders should I backup to enable me to restore my system to pretty much as it was following a re-install of Ubuntu? Clearly my home folder is top of the list, but what other folders will I need?

Roger D

---

### Post by deadgobby on 2006-11-30
well in case you need to reinstall or back up your data
[https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=backup&titlesearch=Titles](https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=backup&titlesearch=Titles)
Gobby

---

### Post by RogerD on 2006-11-30
> **deadgobby said:**
> well in case you need to reinstall or back up your data
[https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=backup&titlesearch=Titles](https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=backup&titlesearch=Titles)
Gobby

Hmm...I've looked at this link, but it doesn't seem to answer my original question. I've worked out how I'm going to backup folders, I just want to know what folders to backup and, ideally, why.

Roger D

---

### Post by dwblas on 2006-11-30
I'll start this out, I backup /home, /root, /env, /bin, /usr/bin, /sbin, /usr/sbin, /usr/lib, /usr/local, and /var although there is a lot of stuff in /var that you don't want.  Let's see what others think about this.  Backup of dirs like /home happens every night, but most are backed up once a week, as they don't change, and if they have, it's easy to reinstall or whatever.  I would suggest that you concentrate on data first and programs second.  In today's world, if you have a problem you will likely use the live cd or Knoppix to reinstall/uninstall the problem, so backing up /usr/bin, etc is something that some do not do.

---

### Post by CatKiller on 2006-11-30
I've just started thinking about this myself. Obviously data first. If you want to back up a whole partition (data, or your entire / ), aysiu recommends [partimage]("http://www.psychocats.net/ubuntu/partimage"). I've not yet used it.

The deb packages that are used for installation of software are kept for a while in /var/cache/apt/archive. If packages are put there on a new install, then they can be used to install the software again without having to download it again. I also remember reading that it's possible to generate a list of all the packages that are installed, and to use such a list to install all the same packages. I can't remember where I read about it now, but that might be something to think about too.

So, no real answers, I'm afraid. Possibly thoughts that would be useful while you develop your own strategy though.

---

### Post by po0f on 2006-11-30
You only really need to backup /etc, /home, and possibly /var if you do a bunch of database/website stuff.  A backup of / (sans /dev, /proc, and /sys) is what I would call a restore point, and IMO shouldn't even be backed up weekly or on a desktop system at all, try monthly instead.


CatKiller,

[Link](http://www.ubuntuforums.org/showpost.php?p=1825968&postcount=14).  :)

---

### Post by CatKiller on 2006-11-30
> **po0f said:**
> CatKiller,

[Link](http://www.ubuntuforums.org/showpost.php?p=1825968&postcount=14).  :)

Brilliant. Thanks.

---

### Post by JayTee on 2006-11-30
My backup strategy is fairly simple. I backup my entire system partition every time I've made several major changes since the last one. This depends on how often I install new programs or updates. I use Partimage from the SystemRescueCD which is downloadable as an ISO file. It boots linux and lets you run Partimage as well as other utilities to help with system issues.
The rest of the time I run rsync to sync my /HOME folder to another folder on an external USB drive. Someone posted that rsync only works over the network but I must be lucky as it works just fine between local drives for me. :-)
Once a month I make a backup to DVD from my external USB drive backup of /HOME.

---

### Post by dwblas on 2006-11-30
You've convinced me to try partimage.  The big advantage over backup is that the entire system can be restored if or when (in my case) you mess something up.  I've been using Linux since 1995 so I can almost always figure out what I did wrong and fix it.  But a lot of times I'm not sure which tweak broke things and so would want to "just fix it" with the least amount of hassle.  This evening, I removed a java sym-link when installing software, so the browser would close on any java page.  It took about an hour to figure this out.  And so a lesson for those who are fairly new to Linux.  In most cases, you just wnat restore the entire system and figure out what happened later.

---

