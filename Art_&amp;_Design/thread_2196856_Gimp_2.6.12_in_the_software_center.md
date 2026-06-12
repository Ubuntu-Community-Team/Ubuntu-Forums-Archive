---
title: "Gimp 2.6.12 in the software center"
date: 2013-12-31
forum: Art &amp; Design
---

### Post by michael-piziak on 2013-12-31
but 2.8.4  is available for Linux

is the software center behind, or is the 2.8.4 not available for Ubuntu yet ?

---

### Post by michael-piziak on 2013-12-31
Subscribing to this thread

---

### Post by ajgreeny on 2013-12-31
There is a ppa for gimp 2.8.10 if you want it.

It works very well and has the single window mode which is great on a widescreen.

[http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu)

---

### Post by vasa1 on 2013-12-31
> **michael-piziak said:**
> but 2.8.4  is available for Linux

is the software center behind, or is the 2.8.4 not available for Ubuntu yet ?
I'm not totally sure of what I'm saying, but if you're on an LTS such as 12.04, you may not get updates to **all** your software. You'll get updates if they relate to security and possibly for major bug fixes.

The same goes **within** the life-span of non-LTS releases. 

New releases will get new software **if** such software is available in time and passes whatever quality controls the maintainers impose. In other words, just because a software package has been updated by its creator doesn't mean we'll get it ASAP.

Re. gimp, you can run **apt-cache policy gimp** to see what version of software is available on your particular version of Ubuntu. I'm on 13.10 and I see:```
[08:44 AM] ~ $ apt-cache policy gimp
gimp:
  Installed: (none)
  Candidate: 2.8.6-1ubuntu1.1
  Version table:
     2.8.6-1ubuntu1.1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu/ saucy-security/main amd64 Packages
     2.8.6-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main amd64 Packages
[08:46 AM] ~ $ 

```
So this answers your question: "is the software center behind, or is the 2.8.4 not available for Ubuntu yet ?"

As aj points out, there's always the ppa route or even installing from source but then it's up to you to deal with any issues that arise.

---

### Post by deadflowr on 2013-12-31
> **michael-piziak said:**
> but 2.8.4  is available for Linux

is the software center behind, or is the 2.8.4 not available for Ubuntu yet ?

Precise?
quantal runs 2.8.2 and raring runs 2.8.4.
As stated, saucy runs 2.8.6.

LTS releases hold a lot of older packages.
But they are supported. Just old.

---

### Post by michael-piziak on 2014-01-01
I mainly want Gimp that processes raw.  I don't know if my version does.

---

### Post by monkeybrain20122 on 2014-01-01
As ajgreeny says there is a ppa for the up to date version. Just add it to your source list and upgrade and there you go. Personally I don't really care for Ubuntu's packaging policy, I won't sit and  wait for a new Ubuntu release to upgrade foo. If I want it I am going to get it NOW. There are many ppas for the latest and greatest and you can install them easily. PPAs are one of the most attractive features of Ubuntu as they give you the flexibility of selectively upgrading certain packages and a way to roll back if something goes wrong. If I install only from the official repos and rigidly sync my upgrade with distro's release cycle I would have used Debian instead.

 You can compile from source of course. I have vlc 2.1.2 , gimp 2.9 and Octave 3.8, all self compiled as I can't get ppas for those versions. I am enjoying the new features. :)

---

### Post by monkeybrain20122 on 2014-01-01
> **michael-piziak said:**
> I mainly want Gimp that processes raw.  I don't know if my version does.

It does, but you have to install some plugins.

---

### Post by ssam on 2014-01-02
> **michael-piziak said:**
> I mainly want Gimp that processes raw.  I don't know if my version does.

install gimp-ufraw

(though you may find that rawtherapee or darktable is more useful for managing and editing raw files)

---

### Post by kurja on 2014-01-02
> **ssam said:**
> install gimp-ufraw

(though you may find that rawtherapee or darktable is more useful for managing and editing raw files)

Thumbs up for darktable, it's just wonderful.

---

### Post by ofnuts on 2014-01-03
On the KDE side of things there is also Digikam that will process Raw files. 

Personally I don't see much point in a Raw plugin for the current version of Gimp. You have to do all of your exposure/color adjustment work in the plugin to benefit from its 16/32-bit/channel processing, because the 8-bit processing in Gimp creates artifacts very quickly. So when you have done that part it is a good idea to save the results anyway before you start local editing. So you can as well switch to another application.

---

