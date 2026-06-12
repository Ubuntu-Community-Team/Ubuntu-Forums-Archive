---
title: "Packages for build-essential?"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by stupidkid on 2006-12-23
Hello, I'm trying to install build-essentail so I can compile the newest version of ndiswrapper. But I don't have internet while I'm in ubuntu (since I can't install ndis). What packages do I need for build-essential and where do I download them? This way I can just put them on a windows drive and then transfer them to /var/cache/apt/archives

Thanks a lot.

---

### Post by christhemonkey on 2006-12-23
Go to [http://packages.ubuntu.com](http://packages.ubuntu.com)


Then search for build-essential, which should take you here:
[http://packages.ubuntu.com/edgy/devel/build-essential](http://packages.ubuntu.com/edgy/devel/build-essential)

Where you can see all dependencies to get.

To get them click on the i386 (or whatever architechture your running!) an then select a mirror near you.
Remember to not only get the dependencies but the dependencies of the dependencies etc....

---

### Post by stupidkid on 2006-12-23
Hmm...seems like a pain, right? I might just drag my computer downstairs and use wired.

Thanks though.

---

### Post by christhemonkey on 2006-12-23
Just as an afterthought, the install cd used to contain build-essential on it!

(dont know if it still does)

So whack it in whilst your on and add it as a cd repository in synaptic, then see if build essential becomes available after reloading the information.

---

### Post by az on 2006-12-23
Yes, while you are at the Ubuntu desktop, insert the cd and the package manager should start.  Search for build-essential and install it.

You can install ndiswrapper-utils from there too.  You probably don't need to compile the very newest version of ndiswrapper anyway.  Just use the one that comes with Ubuntu.

---

### Post by taurus on 2006-12-23
Insert the CD and open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

