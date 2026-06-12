---
title: "How do I..."
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by Jrdgames on 2006-01-25
How do I install a program on ubuntu 5.10 Breezy Badger Gnome I have the .tar.gz file but I can't figure out how to install it if anyone can help then I would greatly appreciate it.

If this is the wrong forum then mods please move.

---

### Post by DirtDawg on 2006-01-25
Please let us know what program you're trying to install. It may be in the repositories.

---

### Post by localzuk on 2006-01-25
Installing programs in Ubuntu is usually handled by 'Synaptic' or 'apt-get'. Information on these programs can be found here: [https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation) and [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

I would advise looking to see if the software you want is available from the repositories first. If not, take a look at the files in the tar.gz file you have. Usually there will be files such as INSTALL and README. These usually describe the process of installing for you.

Hope this helps.

---

### Post by Jrdgames on 2006-01-25
Im trying to install bind9 although I couldn't get it through *apt-get install bind9* so i googled it and found its home: [http://www.bind9.net/download]("http://www.bind9.net/download") and I downloaded the .tar.gz file well I can't figure out how to install it.

---

### Post by kaamos on 2006-01-25
It is in the repositories.

Look here: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)
When done, install with synaptic.

---

### Post by bikeboy on 2006-01-25
Open up Synaptic, bind9 is defintely there, in the standard repository too I think.

edit. beaten

---

### Post by Jrdgames on 2006-01-25
thank you very much everyone for the quick replies and the help I will try what youve suggested and if I need anymore help ill post again about it

---

### Post by hen3rz on 2006-01-25
Hey, Just for future refrences you could try reading through this howto It tells you how to isntall .debs .rpms and .tar.gz:

[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by Jrdgames on 2006-01-25
thanks for your help bind9 is in synaptic and but i am having a few problems if anyone could help i would appreciate it.

[[IMG]http://img64.imageshack.us/img64/9339/couldnotdownloadallrepositoryi.th.png[/IMG]](http://img64.imageshack.us/my.php?image=couldnotdownloadallrepositoryi.png)
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-extras/main/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-extras/universe/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-extras/multiverse/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/Packages.gz:) 404 Not Found

[[IMG]http://img56.imageshack.us/img56/6672/screenshot10eh.th.png[/IMG]](http://img56.imageshack.us/my.php?image=screenshot10eh.png)

[[IMG]http://img90.imageshack.us/img90/9349/screenshot28db.th.png[/IMG]](http://img90.imageshack.us/my.php?image=screenshot28db.png)

[[IMG]http://img90.imageshack.us/img90/5771/screenshot30va.th.png[/IMG]](http://img90.imageshack.us/my.php?image=screenshot30va.png)

---

### Post by dueY on 2006-01-25
```
sudo gedit /etc/apt/sources.list
``` Add
```
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
```

---

### Post by aysiu on 2006-01-25
[QUOTE=Jrdgames]
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-extras/main/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-extras/universe/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-extras/multiverse/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/Packages.gz:) 404 Not Found[/quote] Mirrormax is dead. See the first link of my signature.

---

### Post by Jrdgames on 2006-01-26
thankyou it seems to be working properly now.

---

