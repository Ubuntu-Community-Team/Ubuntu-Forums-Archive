---
title: "Network sharing and printing with XP"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by Danny Boy on 2006-03-23
I've been trying to get this to work for a couple days now, even followed the tutorial on the Wiki. It just won't work. 

Here is what happens with the networking part. 

XP Comptuer sees my desktop (Ubuntu) when I try to view my computer from XP, I get prompted for a username/password. I've trying entering my Ubuntu username and password. It doesn't work that's the only un/pass combo I can think of. 

Ubuntu sees the XP system and is able to use it, grab files, send files etc without a problem.

Printing when I tried setting it up, I messed up the cups prefences and wound up having to reinstall cups, I have gotten absolutly no where with the printer. 

Thanks for any help you can offer,

Dan

---

### Post by noswal on 2006-03-23
I have a similar set up, use zonealarm on XP - have to change the permissions on it to medium. see if this helps [http://ubuntuforums.org/showthread.php?t=141464](http://ubuntuforums.org/showthread.php?t=141464)

---

### Post by echo $USER on 2006-03-23
What it is prompting you for is a samba username and password.  [http://ubuntuguide.org/#sambaserver]("http://ubuntuguide.org/#sambaserver") follow this to set up a samba user and passwd.  To print you need to go enable detect network printers and then set it up with samba and url of your printer.

---

