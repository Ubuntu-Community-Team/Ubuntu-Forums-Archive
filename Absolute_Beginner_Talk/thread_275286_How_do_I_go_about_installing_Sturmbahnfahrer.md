---
title: "How do I go about installing Sturmbahnfahrer"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by Risotto on 2006-10-11
Hi

I thought I'd have a go at installing a Linux game - Sturmbahnfahrer.  So far all I've done is to download it to my desktop as sturmbahnfahrer-1.3.tar.gz

I have looked around the forums and I can see that the commands I need are:

```
cd Desktop
mkdir Sturmbahn
dpkg-deb --extract sturmbahnfahrer_1.0-1_i386.deb  Sturmbahn
dpkg-deb --control sturmbahnfahrer_1.0-1_i386.deb  Sturmbahn/DEBIAN
nano Sturmbahn/DEBIAN/control
dpkg --build Sturmbahn
sudo dpkg -i Sturmbahn.deb
```

But my question is how do I get the .tar.gz file into a .deb so that I can do the above please?

Many thanks
Mike

---

### Post by Perfect Storm on 2006-10-11
If you want to make the source to .deb that's a bit advance if you havn't tried it before. 
I think you should go and get the .deb instead from their homepage. Usually you just double-click to make it install.

The quote you are showing is for editing an existing .deb package, usually when you'll try cheating the dependency list.

---

### Post by mithras86 on 2006-10-11
You have to compile the source to create a playable binary. In the folder is placed a file called INSTALL which says:
```
To build sturmbahnfahrer, you need the following dependencies:

- glut
  http://sf.net/project/freeglut

- plib
  http://sf.net/projects/plib
  version 1.8.4 or later

- ode
  http://ode.org
  Version 0.6-rc1 or later

- ALSA development library, libasound
  http://www.alsa-project.org/


To build, type:
$ make

To run, type:
$ make run

To build debian package, type:
$ make deb
```
If you don't want to compile the source, you can get a rpm package [here]("http://rpmfind.net/linux/rpm2html/search.php?query=sturmbahnfahrer&submit=Search+...") and convert it to a .deb package with alien (which you can get with your package manager).

> **Artificial Intelligence said:**
> If you want to make the source to .deb that's a bit advance if you havn't tried it before. 
I think you should go and get the .deb instead from their homepage. Usually you just double-click to make it install.

The quote you are showing is for editing an existing .deb package, usually when you'll try cheating the dependency list.You cannot find any debian package at [http://www.stolk.org/sturmbahnfahrer/download/](http://www.stolk.org/sturmbahnfahrer/download/) so converting the rpm or compiling the source are the only options.

---

### Post by Risotto on 2006-10-11
Thanks guys

I've got the dependencies with the exception of ode, using Synaptic.  I've downloaded ode-src-0.7.zip from the website mithras86 quoted and extracted it to ode-0.7.  However I'm not sure what to do with it next to make sure that it can be depended upon.  I expect this is a really dumb question, and I apologise for it, but what do I need to do now please?

Many thanks
Mike

---

### Post by Perfect Storm on 2006-10-11
Try check if the ode have a readme.txt and see if it explain the installation.

---

### Post by Risotto on 2006-10-12
Thanks Artificial Intelligence - the readme.txt referred to the install.txt file and that talked about:
"1. Building with Visual Studio
2. Building with Autotools (Linux, OS X, etc.)"

I installed Autotools from Synaptic but couldn't get the commands, e.g. $ sh autogen.sh, to do anything.

So I tried making the rpm into a deb using alien.  This seemed to generate a load of stuff which I have no idea what it means:```


mike@ubuntu-mike:~/Desktop$ sudo alien sturmbahnfahrer-1.2-2.fc6.src.rpm
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key
ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key
ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key
ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key
ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key
ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key
ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
sturmbahnfahrer_1.2-3_i386.deb generated
```

I'm beginning to think that I should take up gardening or something... :-k

---

### Post by Perfect Storm on 2006-10-12
The .deb(.rpm) you use there is containing the source code to build. Try to get the other one.

---

### Post by mips on 2006-10-12
There is a deb here, [http://www.scummvm.org/downloads.php](http://www.scummvm.org/downloads.php)

---

### Post by Risotto on 2006-10-12
I presume I want an i386 .rpm then?  Not all the links work, so I got the most recent I could.  However:
```

mike@ubuntu-mike:~/Desktop$ sudo alien sturmbahnfahrer-1.2-2.fc6.src.rpm
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key
ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key
ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key
ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key
ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key
ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key
ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
warning: sturmbahnfahrer-1.2-2.fc6.src.rpm: Header V3 DSA signature: NOKEY, key                                                                                                    ID 1ac70ce6
sturmbahnfahrer_1.2-3_i386.deb generated
```

This doesn't look good to me!

---

### Post by Risotto on 2006-10-12
> **mips said:**
> There is a deb here, [http://www.scummvm.org/downloads.php](http://www.scummvm.org/downloads.php)

I can see a deb for scummvm but not for sturmbahnfahrer :???:

---

### Post by Risotto on 2006-10-12
Found a deb at [http://www.jeuvinux.net/article.php3?id_article=53]("http://www.jeuvinux.net/article.php3?id_article=53")

But now I seem to dependency issues.  Is this because the deb is for Debian?

```
mike@ubuntu-mike:~/Desktop$ sudo dpkg -i sturmbahnfahrer_1.2-1_i386.deb
(Reading database ... 113005 files and directories currently installed.)
Preparing to replace sturmbahnfahrer 1.2-1 (using sturmbahnfahrer_1.2-1_i386.deb                                   ) ...
Unpacking replacement sturmbahnfahrer ...
dpkg: dependency problems prevent configuration of sturmbahnfahrer:
 sturmbahnfahrer depends on libasound2 (>> 1.0.11); however:
  Version of libasound2 on system is 1.0.10-2ubuntu4.
 sturmbahnfahrer depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 sturmbahnfahrer depends on libgcc1 (>= 1:4.1.0); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 sturmbahnfahrer depends on libstdc++6 (>= 4.1.0); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
dpkg: error processing sturmbahnfahrer (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sturmbahnfahrer

```

---

### Post by Perfect Storm on 2006-10-12
Use the codes from your first post to change the dependency.

When you come to **nano Sturmbahn/DEBIAN/control** make sure you have all the libs the game want installed and afterwards remove the "offending" dependency.

---

### Post by Risotto on 2006-10-12
Aha - that's it.  It's all working ok!

Many, many thanks Artificial Intelligence - you have been very patient with me! :D 

I'd better get practicing my driving...!

---

