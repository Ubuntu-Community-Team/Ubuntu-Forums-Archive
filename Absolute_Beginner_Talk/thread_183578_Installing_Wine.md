---
title: "Installing Wine"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by Souljah on 2006-05-28
Well I'm trying to install WINE the windows emulator, and when I do, I get this error:

[b]E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory[/b]

Not only does this happen with wine, but also when Ubuntu informs me of updates and I try to update it, I get the same error message. I'm on, Ubuntu 5.04 I think. Preview Edition. I haven't updated in a long time. Any help on this? 

P.S.: I am using Synaptic Package Manager to install it.

---

### Post by adwait on 2006-05-28
Did you use sudo? Or did synaptic as you for the root/administrator password? If not try laucnhin synaptic with sudo
```
sudo synaptic
```

---

### Post by Souljah on 2006-05-28
No I did not use sudo, I opened up synaptic package manager from System>Administratoin>Synaptic Package Manager. Then the list came up. I did a search for WINE, found it. I marked it for install. Then at the top, I clicked on apply. Then I clicked on ok to install it and that's when the error message popped up.

Another thing to note is that while running previous updates on ubuntu, I cancelled them prematurely before it finished updating. Did a search on google and someone said that's because you cancelled your updates prematurely so you will have to clear it out. Not sure though.

So basically to answer your question, synaptic asked me for my root password which I gave.

EDIT: Another thing, when I try to open up my menu.lst file through gedit, I get this that comes up before it opens up:

[b](gedit:8338): Gdk-WARNING **: locale not supported by Xlib

(gedit:8338): Gdk-WARNING **: cannot set locale modifiers
[/b]

Any Idea on what that is?

---

### Post by adwait on 2006-05-28
Ok so it asked for your root password so thats fine. If you stopped the update prematurely that maybe the problem. Try renaminmg the lock file
```
sudo mv /var/cache/apt/archives/lock /var/cache/apt/archives/lock.backup
```

---

### Post by Souljah on 2006-05-28
[QUOTE=adwait]Ok so it asked for your root password so thats fine. If you stopped the update prematurely that maybe the problem. Try renaminmg the lock file
```
sudo mv /var/cache/apt/archives/lock /var/cache/apt/archives/lock.backup
```[/QUOTE]

Yes thank you that worked. It seems the lock file was the problem.

---

