---
title: "Is ubuntu big?"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by guyomarj on 2005-10-20
Hi,

I've jutst installed Ubuntu, a few days ago. The system is on 4.7G hd and my /home is on another partition.

I was wondering if the 4.7G will be enough to hold Ubuntu + the packages I might install.

Thx

---

### Post by patrick295767 on 2005-10-20
[QUOTE=guyomarj]Hi,

I've jutst installed Ubuntu, a few days ago. The system is on 4.7G hd and my /home is on another partition.

I was wondering if the 4.7G will be enough to hold Ubuntu + the packages I might install.

Thx[/QUOTE]

Server installation is about 400Mb around ... i dont exactly recall ... 
After installation, I am at 2.5 GB... (no KDE)

... I dont know more ...

---

### Post by Psy-Q on 2005-10-20
That depends on how many packages you're going to install, and what kinds, of course :)

A few big games take up more space than a dozen command line utilities. For normal desktop use, your 4.7 GB should be enough. I have 8 GB myself, but rarely use more than 2 GB. Also make sure to delete your cache of downloaded .deb packages from time to time (sudo apt-get clean). That should remove a bunch of things.

A utility I recommend if you want to find out where all your space is going: kdirstat. It shows you directories as treemaps.

---

### Post by guyomarj on 2005-10-20
Can I use kdirstat even if I use Gnome? Or is there a Gnome-equivalent?

And is there a way to automatize the 'apt-get clean'.

---

### Post by az on 2005-10-20
You need two gigs for a complete default install.

4.7 is fine unless you edit video or like to download many iso images and stuff...

---

### Post by Psy-Q on 2005-10-21
[QUOTE=guyomarj]Can I use kdirstat even if I use Gnome? Or is there a Gnome-equivalent?
[/QUOTE]

Yes, you can use any KDE application even in Gnome. If you install a KDE application with Ubuntu, the package manager will automatically take care of installing the needed KDE libraries along with it.

[QUOTE=guyomarj]
And is there a way to automatize the 'apt-get clean'.[/QUOTE]

You could add it to a cronjob:

```

sudo gedit /etc/crontab

```

Insert this:

```

# Every sunday at 10 o'clock, delete the apt package cache
0 10    * * 7   root  apt-get clean

```

NOTE: If you happen to be installing packages while this job runs, it will probably exit with an error instead of cleaning out the cache. Only one package manager can be at work at any one time. I'm running out of time, otherwise I would have looked up how to cleanly find out if there's another apt and delaying the apt-cache clean appropriately, until the other apt exits (it's just a matter of a few lines of shell script).

---

### Post by heimo on 2005-10-21
This is from Hoary box, but I believe it's same in Breezy. There are configuration files in /etc/apt/apt.conf.d to handle archive clean up. In /etc/apt/apt.conf.d/10periodic there's line with:
```
APT::Periodic::AutocleanInterval "0";
```
which is interval in number of days, 0=disabled, 7=weekly

In /etc/apt/apt.conf.d/20archive, we have:
```
APT::Archives::MaxSize "500";
```
where we can choose the maximum size cached .deb packages can use (in megabytes). These are used by /etc/cron.daily/apt which is run daily.

---

### Post by trash on 2005-10-21
you can also keep an eye on your available space typing in terminal:
df -h

or in disks gui found in system/admin/disks

---

### Post by skoal on 2005-10-21
Ubuntu big?? It's huge! huge I tell ya!

...but you're talking about the installation.  Nah, it's quite tame actually.  If you wanna trim reinstall, you can fit it down to a workable desktop under ~600MB using XFCE (and server install like patrick said).  Search the forums if you go that route.

I'm scraping the hdd sewer myself with an old SCSI 9 gig'er.  I've installed quite a few apps and already chewed up 2.0 gigs on *just* my root partition.  But just do like I'll do (if you can) - search eBay for an old second drive to slap in there as your needs grow.  I can get another scsi 9 gig'er for <$10 (incl. shipping!).  Ububooyah!

\\//_

---

### Post by guyomarj on 2005-10-21
The command line
```
sudo du -s -h /*
```
works fine for me.

I'll check the cron thing and configurations files for an automatic apt-get clean.

Thx all of you.

---

