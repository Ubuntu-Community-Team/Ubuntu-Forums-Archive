---
title: "It wants my ubuntu cd... but..."
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by tocleora on 2008-01-14
I'm trying to apt-get some files and when it tries to get libssl-dev I get this message:

> Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter


I  did install using a CD but my CD is now 2 hours away and I'm trying to get sound working while at work, is there any way to turn this off?  I installed the last version on a different laptop (6.10?) from the download and it did not do this so I would assume I shouldn't have to. Any assistance would be appreciated.

---

### Post by steeleyuk on 2008-01-14
System > Administration > Software Sources

Uncheck the box which says Installable from CD/DVD-ROM.

---

### Post by Terry of Astoria on 2008-01-14
From the terminal you can comment out the cd as a repository. Do
```
sudo gedit /etc/apt/sources.list
```
And put a # in front of the part where it says " deb cdrom blah blah blah"
then ubuntu will retrieve the files elsewhere.
You might want to uncomment the universe and multiverse lines as well.

---

### Post by tocleora on 2008-01-14
Awesome guys. I'm embarrassed when it's that easy. thanks a lot!

---

### Post by BrainDedd on 2008-01-16
Is there any way to get the CD/DVD working like this to save my bandwidth?

---

### Post by ByteJuggler on 2008-01-16
> **BrainDedd said:**
> Is there any way to get the CD/DVD working like this to save my bandwidth?

Yes, put the lines referencing the CD back in if they've been removed completely for whatever reason, or uncomment/enable them if they're just comment out/disabled.  

The only problem is that the packages on the CD will be increasingly out of date with what's in the repositories.

---

### Post by Joeb454 on 2008-01-16
There's also the DVD version which contains a lot more of the packages for offline installation :) Though like **ByteJuggler** said, the online repositories will be updated, the CD/DVD won't

---

### Post by macogw on 2008-01-16
> **Joeb454 said:**
> There's also the DVD version which contains a lot more of the packages for offline installation :) Though like **ByteJuggler** said, the online repositories will be updated, the CD/DVD won't

But due to Ubuntu's policy of only updating for security fixes, most packages won't get out of date.  There aren't that many packages (at least, comparatively) that are important enough to require security fixes often, so installing from the DVD will get you at least all the important stuff to run your apps, then maybe 2 or 3 out of 20 will need to be re-downloaded from the internet in an update.

---

