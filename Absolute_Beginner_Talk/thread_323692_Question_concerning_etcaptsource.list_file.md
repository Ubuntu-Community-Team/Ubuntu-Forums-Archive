---
title: "Question concerning /etc/apt/source.list file"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by samdonaldson on 2006-12-22
I noticed that most/all of the sites listed in the sources.list file has the name of the particular "version" of ubuntu (edgy, dapper, etc).   I'm assuming that you should not add or change entries that may have a different name then from the one that you are running?

---

### Post by shane2peru on 2006-12-22
It is not recommendable.  It can cause your system to become unstable.  I wouldn't mess around with the sources.lst too much as that is how your computer gets its updates.  If you are using Dapper, I wouldn't add Edgy soures to my source.lst, or visa versa.  Also be carefull about using other sources unless you are just playing around with Ubuntu, and wish to experiment, and plan on re-installing every now and then.  

Shane

---

### Post by RudolfMDLT on 2006-12-22
Hi,


There is a big pile of software on a server some where, you have an app called synaptic on your machine and a config file called sources. This app uses the config file to find these servers and then updates it's catalog of the software pile.

By changing the name at the end of the URLs' and then running an update you will just change your pile of software on your machine, if your only changing some of the descriptors you should get an error that no installation candidate was found. Don't mix your piles, just like water and oil don't mix, so to different versions of an OS don't mix! ;)

It sounds like a stupid analogy but in essence thats how it works.


Cheers,

Rudolf

---

