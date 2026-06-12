---
title: "Debian 7 minimal install on VM - can't install anything."
date: 2013-04-26
forum: Any Other OS
---

### Post by Carl H on 2013-04-26
I'm having a play with VirtualBox and have installed Debian 7 from CD1, which gives a minimal setup. The VM seems to be working fine, but I can't install some packages. 

The packages that I want are gedit, python-qt4, pyqt4-dev-tools, and python-pythonmagick. They do not appear to be in the repo. Other packages chosen at random are not there either. I've done apt-get update but no difference. 

From memory (I'm at work at the moment) the sources list just has the CD and security wheezy main (?) repo listed. 

Either I'm missing something fundamental, or I need to add another repository - if so, which one? 

Thanks in advance.

---

### Post by Carl H on 2013-04-26
For instance:- [http://packages.debian.org/wheezy/gedit](http://packages.debian.org/wheezy/gedit)  How can I tell which repo this is in?

---

### Post by lykwydchykyn on 2013-04-26
All of those should be in the main repo.

Can you post the output of:
```

aptitude update

```

(run as root, of course).

You also might find this enlightening:
[http://www.alandmoore.com/blog/2012/05/17/debian-for-ubuntu-people/](http://www.alandmoore.com/blog/2012/05/17/debian-for-ubuntu-people/)

---

### Post by cortman on 2013-04-26
Did you configure apt during installation?
If not, you may need to edit sources.list. Check that it has the line

```
deb http://ftp.uk.debian.org/debian testing main contrib non-free
```

Assuming (from your info) that you're in the UK.
And as was mentioned, you need to update first- either aptitude update, or apt-get update.

---

### Post by Carl H on 2013-04-26
> **cortman said:**
> Did you configure apt during installation?
If not, you may need to edit sources.list. Check that it has the line

```
deb http://ftp.uk.debian.org/debian testing main contrib non-free
```

Assuming (from your info) that you're in the UK.
And as was mentioned, you need to update first- either aptitude update, or apt-get update.

That's done the trick. Thank you very much. :D

---

### Post by iamkuriouspurpleoranj on 2013-04-26
You did well, though. If you choose the mirror during installation, it takes forever and a day to actually install.

---

### Post by cortman on 2013-04-26
No problem. Please mark the thread [SOLVED] by editing the first post.
Good luck!

---

### Post by kiyop on 2013-04-26
Replace "testing" with "wheezy" if you want to stick to debian 7 = wheezy.
Otherwise, your system will be debian testing.
Refer [http://www.debian.org/releases/](http://www.debian.org/releases/)
and
[http://lists.debian.org/debian-devel-announce/2013/04/msg00006.html](http://lists.debian.org/debian-devel-announce/2013/04/msg00006.html)
> We now have a target date of the weekend of 4th/5th May for the release.

We have checked with core teams, and this seems to be acceptable for
everyone.  This means we are able to begin the final preparations for a
release of Debian 7.0 - "Wheezy".

Mixing two different releases or more in /etc/apt/sources.list messes your debian up.

---

### Post by Carl H on 2013-04-27
> **kiyop said:**
> Replace "testing" with "wheezy" if you want to stick to debian 7 = wheezy.


Done that, cheers. :D

---

