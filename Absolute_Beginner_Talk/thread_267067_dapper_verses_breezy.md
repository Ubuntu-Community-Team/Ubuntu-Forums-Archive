---
title: "dapper verses breezy?"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-09-28
What advantages has "dapper" over "breezy" ubuntu? Has dapper superior features? Can i upgrade without losing all new files on my breezy system?

---

### Post by Sef on 2006-09-28
Dapper is much adavanced over Breezy.  
And you can upgrade it and keep your files and setting intact. 

First, **back up** your files.

Then, open the terminal. (Applications > Accessories > Terminal)

Next, sudo aptitude update

After that, sudo aptitude dist-upgrade

And your will upgraded to Dapper.

---

### Post by stig on 2006-09-28
And if you have not already done so, give some thought to creating a separate Home partition in Ubuntu so that you can more safely upgrade in future.

See the following web page for guidance......
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by meniscus on 2006-09-28
Are you talking about another partition on the harddrive itself or just on the ubuntu file partition( as in directory)?

---

### Post by Sef on 2006-09-28
> Are you talking about another partition on the harddrive itself or just on the ubuntu file partition( as in directory)?

Another partition. If you regularly back up your data and settings, then a separate home partition is not really needed.  However, if you don't regularly back it up, then you should have a home partition.

---

### Post by stig on 2006-09-28
> **Sef said:**
> Another partition. If you regularly back up your data and settings, then a separate home partition is not really needed.  However, if you don't regularly back it up, then you should have a home partition.

I think the separate partition provides an extra layer of safety, in addition to doing essential backups.

Also, when I once had to restore from a backup, my data files were OK and most of the config files but a few configurations were lost - not a big deal but enough to be irritating. But then my backups are simply done by copy-and-paste to another PC and that is probably not the best way to do it!

---

### Post by meniscus on 2006-09-28
how do i go about doing it? Ive done it before with partition magic in windows..whats the procedure from a linux os standpoint?

---

### Post by n0dl on 2006-09-28
Doesnt dist-upgrade usually require the user to edit his /etc/apt/sources.list and change every refrence of breezy to dapper?
```
sudo -s
      less /etc/apt/sources.list | sed s/breezy/dapper/ > /etc/apt/sources.list
      sudo apt-get update && sudo apt-dist upgrade
```
of course it would be helpful if you backed up your sources.list
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```
Dapper has a lot of nifty new features :)

---

### Post by Sef on 2006-09-28
> Doesnt dist-upgrade usually require the user to edit his /etc/apt/sources.list and change every refrence of breezy to dapper?

True.  I forgot that part.

> how do i go about doing it? Ive done it before with partition magic in windows..whats the procedure from a linux os standpoint?

Don't use partition magic.  It and Linux don't get along too well.

Use a Live CD or download [GParted.]("http://gparted.sourceforge.net/livecd.php")

---

