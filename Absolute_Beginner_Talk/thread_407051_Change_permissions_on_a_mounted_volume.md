---
title: "Change permissions on a mounted volume?"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by billygates on 2007-04-11
First of all, thanks for all your help in the past and future...

I was able to set my windows voume to automatically mount using the following:

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html")

The mounted drive shows up on my desktop and I can access it.  I cannot write to it.

The properties of the volume show Root as the owner and group.  Everything else is greyed-out.

How can I make this volume fully accessible from my username?

You all must think I'm a fool.  Thanks again.

---

### Post by taurus on 2007-04-11
You cannot write to ntfs filesystem without installing/using ntfs-3g.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by jackmc on 2007-04-11
You need to use Ntfs-3g. Do a search for "howto ntfs-3g" and it should be near the top (pretty popular thread).

I'm working on it myself at the moment :)

EDIT: I was too slow :)

---

### Post by darkrose on 2007-04-11
Is your Windows partition ntfs or fat32?

if it is fat, then getting user access should be as simple as opening a terminal and entering:
sudo chown -R yourusername /directory/where/windows/is/mounted

If it is ntfs, then you will need to install the ntfs-3g drivers to allow you to write to it. There is a how-to for doing so at [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by ComplexNumber on 2007-04-11
> **billygates said:**
> First of all, thanks for all your help in the past and future...

I was able to set my windows voume to automatically mount using the following:

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html)

The mounted drive shows up on my desktop and I can access it.  I cannot write to it.

The properties of the volume show Root as the owner and group.  Everything else is greyed-out.

How can I make this volume fully accessible from my username?

You all must think I'm a fool.  Thanks again.
assuming that your windows filesystem is ntfs, install [this]("http://flomertens.free.fr/ntfs-config/") (after you've installed the ntfs-3g packages, as previously suggested). it was the only thing that worked for me ;). if you look on down the page, you will see the debs for edgy and feisty ubuntu. download that to your home directory, then double click on it to install it.

---

### Post by billygates on 2007-04-11
Thanks for all your help...

I had already installed ntfs-3g.  All i had to do was add> /dev/<your partition>     /media/<mount point>     ntfs-3g     defaults,locale=en_US.utf8   0    0

to fstab, unmount the volume and remount and it works like a champ.

THANKS!

---

