---
title: "how to install RPM packages?"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-02-08
how to install RPM packages in ubuntu gutsy gibbon?

---

### Post by jan quark on 2008-02-08
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

this might help

---

### Post by Paqman on 2008-02-08
You'll need to convert them using [alien](http://en.wikipedia.org/wiki/Alien_%28software%29). It's in the repos.

---

### Post by jan quark on 2008-02-08
> RPM Package (.rpm)
    RPM is another popular way of packaging software, and it's used by popular distributions such as Fedora Core, SUSE Linux and Mandriva. RPM is not used by the Ubuntu Package Manager, but there does exist a command for converting an RPM into a Deb; this doesn't mean that any RPM will work on your system, though! The same program can also install the RPM directly so that you won't have to do this yourself. The command is not available right away so you'll need to install it yourself - the package is called alien and is of course available through Synaptic. If the user carl wants to install an RPM called test.rpm located on his desktop, he will enter sudo alien -i /home/carl/Desktop/test.rpm.

if you dont want to search the site :)

---

### Post by hyper_ch on 2008-02-08
> **adi_das said:**
> how to install RPM packages in ubuntu gutsy gibbon?

Basically: You don't! Better to get .debs or compiling from source.

---

