---
title: "Where do all of the files go?"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-06-12
I'm a new Ubuntu 7.04 user with 1 weeks experience and been having lots of fun learning stuff.  I do feel really confused nad wonder where do all of the files that i have download go.  It feels like the days of Windows95 when I bought a book Windows 95 for dummies.  I have done lost of updates and downloaded a few apps and have no idea where they reside on my system.  I also want to know how can i get rid of files that I have installed and no longer want them.  for example, i installed a flash addon for firefox and it doesn't work so I would like to remove it.  I there a history log of changes to the system that i could read to follow what i have done the last week?  Where is the map of my hardrive structure that I could post here and get some advice that have the right directories?  How so I back-up Ubunto so that i can do a quick reinstall if I screwup everything in the near future.  Any help or adice will be appreciated.

VC

---

### Post by Pragmatist on 2007-06-12
If you installed from the repositories (i.e. with Synaptic, Apt-Get, Aptitude) then you can go back there and do a complete removal.  In other cases, it just depends.

Here are some typical locates:

** /usr**      typical location for user software
** /usr/local**       Normal place to install individual user software
** /usr/local/share**
[B] /usr/local/games
[/B] 
** /opt**  some optional software installs here sometimes
[B]
/lib[/B]     has libraries

Hidden directories in your home directory.  They begin with a period.  To see them, type:  **ls -a**

For backups, and snapshots, read this:
[https://help.ubuntu.com/community/BackupYourSystem#head-62f55f1de88881e1db23938a8b887fb8a586fc04](https://help.ubuntu.com/community/BackupYourSystem#head-62f55f1de88881e1db23938a8b887fb8a586fc04)

---

### Post by videocheez on 2007-06-12
thanks man.  you've pointed me in the right direction

---

### Post by ecs_pf5 on 2007-06-12
I have similar questions to you & am reading this link

[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

It's helping to fill in the blanks a bit for me. Hope it helps.

---

### Post by videocheez on 2007-06-12
thx bro

---

### Post by bone43 on 2007-06-12
Welcome!


Below is a easy and fun little how to about learning the shell it not only teaches you a few commands but also how the file sytem works, it goes on into basic scripts a really good easy to follow guide...

[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

Have fun!

---

