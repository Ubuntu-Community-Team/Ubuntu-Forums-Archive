---
title: "How do YOU update Ubuntu?"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by Getwild2 on 2006-07-20
Ever since I've begun the wonderful world of Ubuntu Linux I've always used the following commands once every day or two...

sudo apt-get update
sudo apt-get upgrade

I'm curious if I should be running the upgrade command along with update?  What do you do? :-k 

Thanks!

---

### Post by Athropos on 2006-07-20
"update" downloads the latest packages database definition, while "upgrade" installs updates found thanks to the new database definition. However, you should not have to run these commands, there is an update manager that should do it by itself.

---

### Post by az on 2006-07-20
Just use the update-notifier.  It is the most reliable way to get new updates.

---

### Post by Village on 2006-07-20
What's the best way to do this using some sort of graphical programme, I'm still trying to get my head around the whole sudo thing and terminal.

Thanks

---

### Post by Sonic Alpha on 2006-07-20
The update notifier is the best way, it tells you that there are updates, and you just tell it to go off and do its thing.

---

### Post by Getwild2 on 2006-07-20
I guess I did it myself because I'm ultra-anal about that sort-of thing.  I'll check out the update manager though, I've seen it to updates for me, just usually I get to the updates before the UM does.  

Thanks guys! :D

---

### Post by Ptero-4 on 2006-07-20
Both need to be run. The first instructs apt to download the newest package list. This is needed to get apt to see the newer versions of the packages. And the second one downloads the packages themselves.
For example. If you have gcc 3.2 and apt tells you that the current version is gcc 3.3, the second command will download gcc 3.3 and install it. But if there's gcc 3.5 in the repositories, you'll need to inform apt that gcc 3.5 was recently added to the repositories and that is done with the first command, after that you can use the second command to download gcc 3.5 the same way you did to download gcc 3.3 earlier.

---

