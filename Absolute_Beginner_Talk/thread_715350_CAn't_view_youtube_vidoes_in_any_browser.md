---
title: "CAn't view youtube vidoes in any browser"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2008-03-04
I am trying to play youtube video on FF2 and i have installed the flash plugin and codec to lay most files i can think of but the flash flash does not fully work.  not the the buttons do anything but the max button which actually stop the video, not max window like it should.  I also get a flash big 0 in the lower right corner.  any else every has this issue?

---

### Post by philinux on 2008-03-04
Uninstall the flash you've got now and get this deb package.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)

Make sure you've got ubuntu-restricted-extras installed for the other multimedia stuff

---

### Post by jan quark on 2008-03-04
try either this:

```
sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```
or this:

[http://laiconic.quotaless.com/tutorial3.html](http://laiconic.quotaless.com/tutorial3.html)

---

### Post by RyanZec on 2008-03-04
> **philinux said:**
> Uninstall the flash you've got now and get this deb package.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)

Make sure you've got ubuntu-restricted-extras installed for the other multimedia stuff

the in wrong architecture 1386, i am assume that is because i am running on a 64-bit processor, is there a  version the works for my architecture?

uninstalling an reinstalling like you typed did not help, same result.

---

### Post by jan quark on 2008-03-04
do you run a 64 bit version of ubuntu?
[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/)

---

### Post by philinux on 2008-03-04
You'd be better posting in the 64 bit forum then.

---

