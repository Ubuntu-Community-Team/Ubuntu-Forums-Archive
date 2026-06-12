---
title: "(gedit:4834): GnomeUI-WARNING Confused newbie"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Drezliok on 2006-10-30
I'm trying to edit my mouse [I might just be in the totally wrong spot] per the instructions found here:
[http://llg.cubic.org/docs/mouse.html](http://llg.cubic.org/docs/mouse.html)

Hand when I try to enter the file with sudo and gedit it does this.

Oh and I am using Edgy.

> drezliok@TuxEater:~$ gksudo gedit /dev/input/mouse0

(gedit:4834): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.





Thankyou for your time
Drezliok

---

### Post by Mimsy on 2006-10-30
I have that happen to me in Dapper all the time. I've been told that it's a harmless bug that I can safely ignore.

I'm a bit surprised though, I'd have expected the next official release to fix that.

/Mimsy

---

### Post by ejket on 2006-10-30
Try "sudo gedit" instead.

---

### Post by aysiu on 2006-10-30
> **ejket said:**
> Try "sudo gedit" instead.
Actually, don't.

Read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Drezliok on 2006-10-30
The file I wish to open shows up blank. So I don't know whether the file has nothing in it to begin with or that it could not open it.

---

### Post by ejket on 2006-10-30
> **aysiu said:**
> 
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Ah, ok.  Actually I never heard of gksudo until I tried ubuntu, but I guess there's always new things to learn.

---

