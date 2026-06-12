---
title: "azureus updates don't automatically work"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-09-03
I use ubuntu 7.04 and have azureus as my bittorrent client and it works great except there seems to be a write permission error when trying to do the azureus updates.  i would like to be able to take advantage of the update feature if some one knows how to do this i would appreciate a suggestion.

Thx in advance,

VC

---

### Post by beefcurry on 2007-09-03
try open it in sudo. after update close it and open it again as a normal user. or you can just chmod the files your updating.

---

### Post by Atomic Dog on 2007-09-03
To clarify, open a terminal window and type: sudo azureus

---

### Post by CapitanYochua on 2007-09-03
Azureus isn't that great, in my opinion.

---

### Post by Perfect Storm on 2007-09-03
This guide I wrote: [http://ubuntuforums.org/showthread.php?t=144546](http://ubuntuforums.org/showthread.php?t=144546) for latest version of Azureus (non repo way), it tells you to give user permission to Azureus folder when updating getting a plugin. 
So you just need to know where Azureus is installed and do the same (remember to set the permission back afterwards).

---

### Post by derred on 2007-09-03
To update Azureus you have to change "system files". As a user you can't do this. That is why you have to run azureus as root, download the patches and apply them. This may not be a good security practive but it is an easy fix. 
While I would recommend using rtorrent(small, light, ncurses based) instead, I won't since I don't want to be killed by all the Azureus fans.

---

### Post by videocheez on 2007-09-04
> **CapitanYochua said:**
> Azureus isn't that great, in my opinion.
Thanks for your opinion.  This statement tells me a lot of useful information.

---

### Post by videocheez on 2007-09-04
> **derred said:**
> To update Azureus you have to change "system files". As a user you can't do this. That is why you have to run azureus as root, download the patches and apply them. This may not be a good security practive but it is an easy fix. 
While I would recommend using rtorrent(small, light, ncurses based) instead, I won't since I don't want to be killed by all the Azureus fans.
Thanks for providing a suggested bittorrent client. Does it have a gui?  Does it have remote HTML interface?  Those are two features in Azureus that I find useful.

---

