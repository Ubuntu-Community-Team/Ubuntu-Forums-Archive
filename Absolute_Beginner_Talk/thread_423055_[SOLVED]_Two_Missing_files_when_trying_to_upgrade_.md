---
title: "[SOLVED] Two Missing files when trying to upgrade to Feisty"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by arvevans on 2007-04-25
On the first day Fiesty was available I tried to upgrade using the upgrade manager.  Everything went well up to the point that it downloaded 58 files then complained about two missing security files and the upgrade process aborted.

Today I tried it again...same problem.  It gets the 58 files downloaded, complains about two missing security files, then aborts.  The suggestion shown on screen is that this is a network problem...I don't believe that because it is able to get the 58 file download, and I don't have any problem doing any other type of software install using synaptic.

/home/arv/Desktop/Screenshot.png

I am stuck.  Where do I go from here.  I don't want to do a clean update unless there is no alternative, but it is looking more and more like that may be the only option?

Arv
[arvevans@earthlink.net]

---

### Post by johnc4510 on 2007-04-25
Try downloading the alternate cd. Pop it in and it will bring up the same upgrade feature as the upgrade manager. You can also choose to use or not use the internet for updates during the upgrade. Worked well for me and is the same type of upgrade as using the upgrade manager.

---

### Post by zvacet on 2007-04-25
If you know name of these two files try
```
sudo aptitude install file_name
```

---

### Post by flysurferrosa on 2007-04-25
I'm having the same problem when trying to upgrade from 6.10 to Fiesty, I get to 39 out of 41 files and over and over again it can't seem to get those last two and each time it says something about my network.  Granted my wired connection has not been working and I suspect my ethernet card may be fried, I have been using my wireless connection with no problem up until this point.  I guess I'll try downloading the cd and doing the installation directly from there.  Thanks for the help.

---

### Post by arvevans on 2007-05-03
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2:) Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_edgy-security_main_binary-i386_Packages - open (2 No such file or directory)

---

### Post by oilchangeguy on 2007-05-03
unless you like getting spam, change your screen name to something else besides your email address.

---

### Post by sailor2001 on 2007-05-03
errors look like the repositories are not Complete...Chek with synaptiCs for your repositories.  (small C is being used as a hot key)

---

