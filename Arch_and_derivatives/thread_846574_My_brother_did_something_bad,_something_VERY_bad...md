---
title: "My brother did something bad, something VERY bad..."
date: 2008-07-01
forum: Arch and derivatives
---

### Post by Barrucadu on 2008-07-01
As I mentioned in another thread, I am using ramfs for /var/lib/pacman, /var/cache/pacman, /tmp, and /var/abs/local, with files being synced to disk in /etc/rc.local.shutdown. I also backup those folders into tarballs in /etc/rc.local.
My brother decided to turn off my computer by holding the power button about an hour ago. Obviously, everything in RAM was lost. I also just discovered that while the rest of the backups are fine, the backup for /var/lib/pacman is just missing for some reason. I have *no* package database.

My question is... Is it easier to rebuild the database by hand, or just reinstall Arch? Either way, I'll be thinking up some evil revenge plan for my brother...

---

### Post by ruffEdgz on 2008-07-01
Well, I would check to see if you still have /etc/pacman.d/mirrorlist and it's still connected to the ftp site you want to go to. 

From there, is the /var/lib/pacman folder still there without the local and sync folders in it? If that's the case, you could always just try to do

```

sudo pacman -Syy
sudo pacman -Syu

```

and see if pacman populates it.

I just did a test myself by doing:

```

sudo cp /var/lib/pacman /var/lib/pacman.bak
cd /var/lib/pacman
sudo rm -R local/ sync/

sudo pacman -Syy
:: Synchronizing package databases...
 core                      32.0K   80.8K/s 00:00:00 [#####################] 100%
 extra                    404.6K   82.3K/s 00:00:05 [#####################] 100%
 community                346.9K   81.4K/s 00:00:04 [#####################] 100%
 local database is up to date

sudo pacman -Syu
:: Synchronizing package databases...
 core is up to date
 extra is up to date
 community is up to date
:: Starting full system upgrade...
 local database is up to date

```

and the folders inside /var/lib/pacman came back (local and sync).

---

### Post by Barrucadu on 2008-07-02
The folders come back, but not the contents of local/. I'm having to reinstall everything to fix that...

---

### Post by ruffEdgz on 2008-07-02
Well  I did find a way on the arch forums which the link can find found below:

[http://bbs.archlinux.org/viewtopic.php?pid=388142](http://bbs.archlinux.org/viewtopic.php?pid=388142)

It isn't fun but it could help. Reinstalling is the other way around this and it sucks :(

---

### Post by Barrucadu on 2008-07-02
I'm mid-way through reinstalling everything. This *could* be a blessing in disguise - I did have a lot of junk on this computer.
Anyway, I've ensured that the backup script is working now for every folder I copy into RAM, so from now on the worst that could happen is having to reinstall a few packages - not them all.

---

