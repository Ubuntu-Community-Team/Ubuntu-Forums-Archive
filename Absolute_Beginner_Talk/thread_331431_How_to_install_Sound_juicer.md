---
title: "How to install Sound juicer?"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-01-04
I downloaded ' sound-juicer-2.16.2.tar.bz2 ' and have it on my desktop.

Also, I have a folder ' sound-juicer-2.16.2 ' which I think I got from opening the above mentioned package.

When I try to install this upgrade I get this:-

qwer@qwer-desktop:~$ sudo apt-get install sound-juicer-2.16.2
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sound-juicer-2.16.2

I would appreciate it if someone wold tell me what I did wrong.

Thanks.

---

### Post by ragnar_123 on 2007-01-04
try sudo apt-get install sound-juicer

if that doesn't work either, please post your /etc/apt/sources.list file here. (or even better a link to a paste at pastebin :-) )

---

### Post by benuski on 2007-01-04
If you have a tar.bz2 file, you can't use apt-get to install it.  If you go to [this]("http://psychocats.net/ubuntu/installingsoftware") website, it will show you how to compille that package from source.

---

### Post by ragnar_123 on 2007-01-04
> **benuski said:**
> If you have a tar.bz2 file, you can't use apt-get to install it.  If you go to [this]("http://monkeyblog.org/ubuntu/installing.html") website, it will show you how to compille that package from source.

but sound-juicer is in the repos, so I do see any point in installing from source.

---

### Post by L Campbell on 2007-01-04
> **ragnar_123 said:**
> try sudo apt-get install sound-juicer

if that doesn't work either, please post your /etc/apt/sources.list file here. (or even better a link to a paste at pastebin :-) )

Thanks.

When I try your first suggestion, I get:-

qwer@qwer-desktop:~$ sudo apt-get install sound-juicer
Password:
Reading package lists... Done
Building dependency tree... Done
sound-juicer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Checking Synaptic shows that I have version 2.14.4 not the 2.16.2

---

### Post by benuski on 2007-01-04
If you try the link I posted, and scroll down to option #4, installing from source, it should work.  You might want to remove the current version first though, with a "sudo apt-get remove sound-juicer".

---

### Post by ragnar_123 on 2007-01-04
ahh.. so you want a newer version.
go to directory on desktop, sound-juicer-2.16.2, and see the README, and INSTALL files. They will guide you through :-)

If there is any troubles, then feel free to post here.

---

