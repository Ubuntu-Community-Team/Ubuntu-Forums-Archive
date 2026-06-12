---
title: "Question regarding apt-get &amp; ubuntu 6.06"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by morgolis on 2006-08-31
Hello folks,

Sorry for the semi-nuub question, but as this is my first time using ubuntu (debian) i'm not very familiar with apt-get.  I've always used Fedora Core or CentOS and yum automatically updates packages when it see's new ones in the repository.  I could always check on updates by looking at the /var/log/yum.log file which told me specifically which packages were updated.  However, i'm unable to find any such log in ubuntu and i'm not sure that just running apt-get update at the cmd line will update packages on the system.

Could someone tell me how ubuntu updates it's packages for security fixes / patches or is there something I need to do via writing a cron job or script?

Many thanks in advance!

---

### Post by %hMa@?b&lt;C on 2006-08-31
sudo apt-get update
sudo apt-get upgrade
and your system is up to date!

---

### Post by kkruecke on 2006-08-31
Or try aptitude. u (lowercase) to update. g to apply.

---

### Post by morgolis on 2006-09-01
So what you're telling me is that i need to add apt-get update;  apt-get upgrade to cron.daily to have the system update itself or is there another tool that i'm not aware of?

---

### Post by jordanmthomas on 2006-09-01
By default, Ubuntu will show an icon in the System tray when it finds updates.  You don't have to do anything as it will tell you when they are there.

I suppose you could disable that and add a cron job if you were so inclined, though.

---

### Post by morgolis on 2006-09-01
> **jordanmthomas said:**
> By default, Ubuntu will show an icon in the System tray when it finds updates.  You don't have to do anything as it will tell you when they are there.

I suppose you could disable that and add a cron job if you were so inclined, though.

You would be correct IF I were running it w/ a gnome X desktop or something as that.  I don't have X installed, this machine is pure cmd line, so no icons etc.  I'll just flop a quick script and have cron.daily call it.

---

### Post by jordanmthomas on 2006-09-01
Hey, if you even *know* what a cron job is, what are you doing in the Absolute Beginner's forum?  :) Just kidding...your cron job will work fine if you use those two commands in it.

---

### Post by jordanmthomas on 2006-09-01
Apt will ask you if it is going to install new packages as part of the upgrade, so you may want to tell it to go ahead and say yes to this.

sudo apt-get --assume-yes upgrade

(but this will install some things without letting you know, so it's up to you...)

---

