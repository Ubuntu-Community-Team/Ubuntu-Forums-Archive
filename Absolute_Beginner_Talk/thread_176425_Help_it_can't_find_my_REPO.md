---
title: "Help it can't find my REPO"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by zxcvbnm on 2006-05-14
[http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz:](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz:) 404 Not Found
[http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz:](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz:) 404 Not Found


I was wondering on how to add this repo to my list or 

I am very new

I also get this when i reload my Packet manager

W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)

---

### Post by catlett on 2006-05-14
That repository may be offline or something. To add to your repository just open  the list in a text document you can edit. ```
sudo gedit /etc/apt/sources.list
```
Just be careful this is the place the repository gets it list of servers to go to to get your packages. If you erase it you won't have acces to repositories. To add just copy/paste in those urls. To elimi,ate a repository you can just put an "#" before it.
Also if you want to open a repository on your list, just remove "#" before it.

---

