---
title: "Where do i even begin"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by chasebadkdis on 2008-04-14
Hello,

I just installed wubi- on my laptop yesterday, got windows and linux on here now, Ive been wanting to try out linux for a long time and so far im very satisfied.

anyways, I wanna learn how to start running things and installing things, first thing ive tried downloading / installing is airpwn  and im ompletely lost, I read the install instructions and it talks about running a tar, and then making and then making, well I untarred the folder, and whenever i click make, or make file, I click run, nothing happens, i click run in terminal, nothing happens.  Im just a complete noob at this stuff, where do I start?  Any help is greatly appreciated!

-chasebadkids

---

### Post by wormser on 2008-04-14
[Read this]("http://monkeyblog.org/ubuntu/installing/") about installing software in Ubuntu.  I also recommend reading the links in my signature to get a better basic understanding of Linux.

---

### Post by misfitpierce on 2008-04-14
Google a guide for installing things in Ubuntu via tar files.

 It will show you how to install using terminal to access files instead of clicking run in terminal which is not allowing you to see an error or information which is why it is not doing anything. Also you could check to see if another program similar is avail in Ubuntu by checking add/remove programs under Applications drop down. :)

---

### Post by Michael.Godawski on 2008-04-14
Good start are these pages:
[LIST]
[*][http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[*][http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[/LIST]

First try to install applications via the Synaptic Package Manager.

---

### Post by chasebadkdis on 2008-04-15
Thank you so much everyone for the great replies, ive made some great progress these past couple days!

But now Ive ran into a new problem =[

Whenever I go to run the Synpatic package manager, I run into this error right after i enter the password

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

Any idea what to do?  I tried running dpkg --configure -a      in terminal and it sys I need superuser access??  idk if Im even going about fixing this problem the correct way or not.

Once again, thanks everyone.

---

### Post by philinux on 2008-04-15
Use 

sudo dpkg --configure -a

---

### Post by PGScooter on 2008-04-15
super user access means you need to either preceed the command by:
```

sudo

```

or do
```

sudo su

```

to login as super user. Logout when you're done by ctrl-d

good luck!

---

### Post by wormser on 2008-04-15
You need to user sudo before a command to get super user rights.


```
sudo dpkg --configure -a
```

Read this [site]("http://www.psychocats.net/ubuntu/index").  You will get all the basics with it.

---

### Post by chasebadkdis on 2008-04-15
you guys are all amazing, that totally worked, I did realize thosugh yesterday when I was installing thigns with synpatic I tried installing "chilispot" and now Im realizing i dont want this installed, but it keeps trying to install, what can I do to erase it from my computer?

---

