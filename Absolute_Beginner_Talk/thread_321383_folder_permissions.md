---
title: "folder permissions"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2006-12-18
Hi again,
I've got a new problem, this time I couldn't fix it.
I want to install some plugins and skins into aMSN so I have to paste them in those two folders, but the problem is that when I enter to the folder I can't do anything. I've tried to change the permissions but it says: "you are not the owner, so you can't change these permissions". How can I change that? :confused:

---

### Post by Rippey on 2006-12-18
"sudo chmod" should do it.

---

### Post by user007usa on 2006-12-18
> **Jorge32 said:**
> Hi again,
I've got a new problem, this time I couldn't fix it.
I want to install some plugins and skins into aMSN so I have to paste them in those two folders, but the problem is that when I enter to the folder I can't do anything. I've tried to change the permissions but it says: "you are not the owner, so you can't change these permissions". How can I change that? :confused:

Click on the folder once to highlight it, then right click. (or just right click on it for Kubuntu/KDE)  Choose properties.  Hit the permissions tab.  Who does it say the owner is .. it you?  Also what does it say for the permissions?

If you know how to use the terminal, chown is the command to use.

Like:

chown yourname:yourname /home/yourhomedirectory/somefiletochange.txt

it might be that you have to use sudu before the command like:

sudo chown yourname:yourname /home/yourhomedirectory/somefiletochange.txt


This will change the file "somefiletochange.txt" in the directory "/home/yourhomedirectory" to USER: yourname and GROUP: yourname

Change

 yourname to your login.
 somefiletochange.txt to the name of the file to change
/home/yourhomedirectory/ to whichever directory the file is in.

Or you can omit the directory portion entirely.

Be careful when using this command.  There may be a better way to do this from the GUI as well but I do not know it.

---

### Post by aysiu on 2006-12-18
This should help you:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by timboe73 on 2006-12-19
> **Rippey said:**
> "sudo chmod" should do it.

type in a terminal 

sudo nautilus

enter your password and now you can browse your folders as root.

Be careful though as will be able to delete the entire system if you wanted to ....or not.

---

### Post by aysiu on 2006-12-19
> **timboe73 said:**
> type in a terminal 

sudo nautilus

enter your password and now you can browse your folders as root.

Be careful though as will be able to delete the entire system if you wanted to ....or not.
```
gksudo nautilus
``` is a better habit to get into.

---

