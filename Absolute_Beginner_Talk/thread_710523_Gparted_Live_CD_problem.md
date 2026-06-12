---
title: "Gparted Live CD problem"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by rain4ever on 2008-02-28
When I run the live Cd it asks for driver and resolution. My driver is nvidia and is not on the list. i tried vesa and didnt work. So I went into file system and tried to edit so that the driver for my video card said "vesa" but i could not because of the whole permissions thingy. Any help is greatly appreciated. thanx in advance.

---

### Post by OffAxis on 2008-02-28
If gparted is giving you issues, try running off the ubuntu liveCD. There's a version of gparted on it that detects hardware a bit better than the gparted disc. 
If it still gives you issues try the kubuntu liveCD, it has qtparted on it.

---

### Post by Arthur Archnix on 2008-02-28
I'd try a few different things first. Try xvesa again, if you haven't already (not vesa, xvesa) and select 800x600 if you're asked. And choose a low colour depth, no more than 24, but lower is better.

---

### Post by rain4ever on 2008-02-28
xvesa doesnt work (module doesn't exist) i tried lower color and res. The reason i wanted to use the live cd is because i want to resize the partition i am running ubuntu on and if i log into ubuntu then i cannot do that.

---

### Post by Arthur Archnix on 2008-02-28
Is it the latest version of gparted live? 

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by rain4ever on 2008-02-28
yep its the latest version alright

---

### Post by Arthur Archnix on 2008-02-28
hm.. well, maybe try an older one. Go back two versions. Sometimes new bugs are introduced. Or use a linuxrescue cd. [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

It's got gparted on it. Easier to use than ubuntu live. HAs more drivers and such than gparted live.

---

### Post by UbuKunubi on 2008-02-28
> **rain4ever said:**
> yep its the latest version alright
Could you please explain more about the 'whole permissions thingy'? 
Do you know how to change the permissions? if you do, can you point me in the right direction?

Im also a newbie have hit a small snag myself, only a stumble...

---

### Post by Omnios on 2008-02-28
I used the lice Gparted iso disk as an image and though it had problems the fix was right there in the text. Force??? and setting the res.

---

