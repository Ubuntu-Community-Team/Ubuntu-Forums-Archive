---
title: "Not able to run yum on Ubuntu."
date: 2013-02-25
forum: Any Other OS
---

### Post by sumukhmailings on 2013-02-25
I am trying to install a command line client from Amazon EMR docs.

I am using this command: 

```
$sudo apt-get install ruby-full
```

But I get this error

```
Loaded plugins: fastestmirror, security
    Loading mirror speeds from cached hostfile
    amzn   | 2.1 kB     00:00
    java   | 9.9 kB     00:00 ...
    http://hg.openjdk.java.net/jdk7u/jdk7u/repodata/repomd.xml: [Errno -1]  Error   importing repomd.xml for java: Damaged repomd.xml file
    Trying other mirror.
    Error: Cannot retrieve repository metadata (repomd.xml) for repository: java.
    Please verify its path and try again
```

Can someone guide me on how to resolve this?

---

### Post by TheFu on 2013-02-25
I'm confused. The title and contents do not match.

yum - that tool is used on RPM-based distros. Ubuntu uses apt-get, aptitude, synaptic or even software center instead.

As to the apt-get issue with ruby - could you please post the entire command AND output together?  I can't see where java has anything to do with installing ruby.  BTW, if you are a ruby programmer, like me, you really should use **rvm** [https://rvm.io/](https://rvm.io/) to install and manage ruby, not the Ubuntu version.

---

### Post by sumukhmailings on 2013-02-25
TheFu,

You are correct it is my mistake. I am not using ubuntu but Amazon's own Linux flavor.

---

### Post by howefield on 2013-02-25
Thread moved to the "*Other OS/Distro Talk*" forum.

---

