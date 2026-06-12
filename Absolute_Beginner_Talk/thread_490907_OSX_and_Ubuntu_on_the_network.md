---
title: "OSX and Ubuntu on the network"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Durden on 2007-07-03
Trying to get filesharing working between these two but it's sketchy at best. My OSX system can sometimes see my Ubuntu box and write to it, but the ubuntu box can't see any of the files on my OSX machine. It sees the machine but not the files on it, just a blank directory.

Doing this over samba, just a standard old setup. I can't see any reason why it isn't working. Any ideas?

---

### Post by thornomad on 2007-07-03
Because I only use Macs and Linux I chose to go with AFP as my protocol of choice (instead of Samba, which is windows derived).  Allows the Mac to use all its fancy file features (icons, colored labels, etc) and works well with linux.  You could use NFS (which is Unix) but I don't like it.

To have your Mac access the files on Ubuntu, you would install netatalk on ubuntu (then you can mount the folders easily enough): 

[http://www.damontimm.com/blog/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication](http://www.damontimm.com/blog/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication)

To have your Ubuntu access files on your Mac, you would install:

[http://alexthepuffin.googlepages.com/home](http://alexthepuffin.googlepages.com/home)

I have tried the former, but not the latter.

Damon

---

