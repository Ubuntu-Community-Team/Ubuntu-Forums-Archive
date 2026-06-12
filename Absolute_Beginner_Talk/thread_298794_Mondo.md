---
title: "Mondo"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by fatneck on 2006-11-13
Hi all,

I've just 'installed' Mondo from the Synaptic Package Manager but I can't find it. It isn't in the Apps > Add/Remove section and a search for Mondo doesn't find anything. If I go back into Synaptic it is there and can be marked for re-installation or uninstallation.

Anyone know where it is please?

---

### Post by danbe on 2006-11-13
Run
```
sudo mondoarchive
```
in a terminal and read [http://www.mondorescue.org/docs.shtml](http://www.mondorescue.org/docs.shtml) .

---

### Post by fatneck on 2006-11-13
Thank you, that certainly found it. Please can you explain why I can't access it through a GUI though? As a newbie how would I know to 'sudo mondoarchive'? After downloading from the repository shouldn't it be a point and click away?

Cheers

---

### Post by Marsolin on 2006-11-13
Unfortunately some programs don't include menu entries.  Hopefully Ubuntu will do something to address this in the future.

---

### Post by ephman on 2006-11-26
hi,

if you have the debian menu going you'll find it under debian-->apps-->system-->mondoarchive

ephman

---

### Post by Roger Gundberg on 2007-05-28
I have the Debian menu  installed, but when I type in the root password it kicks it out saying"Authorization failed" i rebooted in order to inilize the program (the only thing I could think of) with the same result. I'm sure this is a fine program but I'm at a loss. Any ideas?

---

### Post by wh33t on 2007-06-05
> **fatneck said:**
> Thank you, that certainly found it. Please can you explain why I can't access it through a GUI though? As a newbie how would I know to 'sudo mondoarchive'? After downloading from the repository shouldn't it be a point and click away?

Cheers

Yup... that is definitely something Ubuntu needs to work on. I find Ubuntu is all about hiding anything from the user that requires root privileges which is damn annoying sometimes. But its also very useful for people who might destroy their computers. Ubuntu should have an option where you can run it with full privileges or not.

---

### Post by wh33t on 2007-06-05
> **Roger Gundberg said:**
> I have the Debian menu  installed, but when I type in the root password it kicks it out saying"Authorization failed" i rebooted in order to inilize the program (the only thing I could think of) with the same result. I'm sure this is a fine program but I'm at a loss. Any ideas?

No idea man... I've had troubles finding documentation on the root password and changing it. I don't recall once during the install being asked for what my root password would be... :(

---

### Post by whitefort on 2007-06-05
Mondo is one of the most useful programs I've come across - unfortunately, I think you might find that even though it's in the Ubuntu repository, it won't work with Ubuntu.  There have been some other threads about this, and most people only seem to be able to get it to work after a lot of tinkering.

Personally, I haven't been able to successfully make/restore a Mondo backup since I upgraded from Dapper.

Perhaps you'll be lucky and have no problems, but if you have... well, you're certainly not alone.

---

### Post by wh33t on 2007-06-05
I think I may switch back to Dapper... is there any downside to this?

---

