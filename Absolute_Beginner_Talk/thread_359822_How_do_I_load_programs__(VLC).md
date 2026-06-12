---
title: "How do I load programs?  (VLC)"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Mashuteichou on 2007-02-12
Ive checked sites they all say something about a universe something.  I downloaded the VLC file, but it won't load.  And I have no idea about anything on Linux.  But, I would like to learn.  So, how do I put VLC on Ubuntu?  And other programs, like Yahoo Messenger.

---

### Post by Paerez on 2007-02-12
Loading programs is different from windows. You don't find a DEB online and install it, you select programs from a repository and linux installs them and keeps them updated for you.

Read this:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

it is very friendly

---

### Post by Darklighter137 on 2007-02-12
The term "universe" refers to a certain repository.  Repositories are archives of installable software that exist on official Ubuntu servers.  When you go to Add/Remove, the software you are presented with depends on which repositories are enabled (that is, where it can look to find software).  To enable or disable repositories, click **System->Administration->Software Sources**.

Please understand that not all Windows software has a Linux counterpart.  Some can be run using emulation, but many others must be replaced by alternatives.

---

### Post by Maestro23 on 2007-02-12
> **Mashuteichou said:**
> Ive checked sites they all say something about a universe something.  I downloaded the VLC file, but it won't load.  And I have no idea about anything on Linux.  But, I would like to learn.  So, how do I put VLC on Ubuntu?  And other programs, like Yahoo Messenger.

VLC can be found in the repositories.  You can get it by:

Synaptic (GUI) 
apt-get (command line)

You will have to enable extra repositories: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Also these links will help you as well:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

What you are trying to do is install from source.  Not a good thing to do for someone who is new to linux.  Always check the Ubuntu repositories first for a program.

Good luck.

---

### Post by loell on 2007-02-12
> **Mashuteichou said:**
> Ive checked sites they all say something about a universe something.  I downloaded the VLC file, but it won't load.  And I have no idea about anything on Linux.  But, I would like to learn.  So, how do I put VLC on Ubuntu?  And other programs, like Yahoo Messenger.

try [gyachi]("http://gyachi.sourceforge.net") for yahoo messenger , if you like webcam and voice chat. :)

---

