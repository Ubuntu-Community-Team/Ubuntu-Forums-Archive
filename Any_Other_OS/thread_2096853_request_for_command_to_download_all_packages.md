---
title: "request for command to download all packages"
date: 2012-12-21
forum: Any Other OS
---

### Post by rupeshforu3 on 2012-12-21
I have installed Debian wheezy( testing ) on my machine. 

Sir is there any command in Debian or ubuntu to download all available packages in online repositories at a time. I found that keryx is useful software to download and install packages from online repositories painlessly. If there is any other procedure please specify.

So I tried to install keryx on my system which resulted in failure. I am providing the output.

This package is uninstallable
Dependency is not satisfiable: python (< 2.7)

So how to install keryx package. please help me.

---

### Post by howefield on 2012-12-21
Thread moved to the "*Other OS/Distro Talk*" forum.

---

### Post by sudodus on 2012-12-21
There are so many packages available, that I would discourage you to download all of them, at least not at once. Instead, download packages, that catch your interest and test them out one by one!

Browse the internet to find what might be interesting. For example this thread

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=382137[/COLOR]]("http://ubuntuforums.org/showthread.php?t=382137")

Yes, the thread is about Ubuntu, but most of these applications are also available for Debian.

---

### Post by cwsnyder on 2012-12-21
Exactly how many Exabytes of storage do you have to store the Debian repositories in, anyway?  Yes, I said, and I meant, Exabytes, not Terabytes, because you are asking to download all of the current stable, testing, unstable, and old-stable packages.

That is a large number of packages.  It might just fit in less than 5 terabytes, but I wouldn't bet on it.

An install package for Debian used to come on 10 CDs for Debian before Lenny.  I haven't even seen a full install package for Lenny or Squeeze.  Look at [http://packages.debian.org/stable/](http://packages.debian.org/stable/) for just a partial listing of the available packages for the stable only branch.  If you want possible obsolete packages, well, the package count just grows bigger.):P:popcorn:

---

### Post by 3rdalbum on 2012-12-23
sudo apt-get install * --download-only

---

### Post by fdrake on 2012-12-23
> **rupeshforu3 said:**
> I have installed Debian wheezy( testing ) on my machine. 

Sir is there any command in Debian or ubuntu to [COLOR="Red"]_**[SIZE="4"]download all available packages[/SIZE]**_[/COLOR] in online repositories at a time.
you are asking the wrong question what package do you exactly need? you are sking somehting like: " how can i download the internet in my computer? "

---

### Post by lykwydchykyn on 2012-12-24
> **cwsnyder said:**
> Exactly how many Exabytes of storage do you have to store the Debian repositories in, anyway?  Yes, I said, and I meant, Exabytes, not Terabytes, because you are asking to download all of the current stable, testing, unstable, and old-stable packages.

That is a large number of packages.  It might just fit in less than 5 terabytes, but I wouldn't bet on it.


I have an apt-mirror at the office which contains binary packages for all of squeeze and wheezy (main, contrib, and non-free), it comes in at 48 Gb.  I suppose source packages would increase the size a bit, but even with that I can't see all of official Debian being more than a terabyte, if that.

To the OP: you can use apt-mirror to set up a server with a complete copy of the repositories for any number of debian versions.  Is this of interest to you?

---

