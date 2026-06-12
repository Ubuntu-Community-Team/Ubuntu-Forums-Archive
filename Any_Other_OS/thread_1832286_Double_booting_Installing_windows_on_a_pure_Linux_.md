---
title: "Double booting: Installing windows on a pure Linux system"
date: 2011-08-24
forum: Any Other OS
---

### Post by Dry Lips on 2011-08-24
I need to install XP on one of my spare computers, but I want to keep 
the Linux installation(s) I already have on it. (Ubuntu Server + Mint Debian ed.) 
Will the XP installer overwrite the existing entries in the MBR?   

 Any advice on how I should set this up?

---

### Post by dave01945 on 2011-08-24
yeah windows will mess with the mbr this guide should help

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Dry Lips on 2011-08-24
Cheers mate!

Ok, I'll have to reinstall the grub? That's what I thought... :x
Well, well... :roll: I'm sure I could do that, but I was hoping there
was a more elegant way...

---

### Post by BrokenKingpin on 2011-08-26
> **Dry Lips said:**
> I'm sure I could do that, but I was hoping there was a more elegant way...
There isn't, unless you can somehow modify the XP install to not overwrite the MBR (which I doubt you can).

---

### Post by Dry Lips on 2011-08-26
> **BrokenKingpin said:**
> There isn't, unless you can somehow modify the XP install to not overwrite the MBR (which I doubt you can).

Now, that's a shame! However, I went ahead with the install, 
and have encountered an annoying problem afterwards...

You can read about it here:
[http://ubuntuforums.org/showthread.php?t=1832996](http://ubuntuforums.org/showthread.php?t=1832996)

---

### Post by Sef on 2011-08-26
Or you could virtualize XP with Virtual Box from the repositories.

---

### Post by Dry Lips on 2011-08-27
> **Sef said:**
> Or you could virtualize XP with Virtual Box from the repositories.

Been there, done that! ;) I need to run some 3d programs which
runs too slow in virtualbox. My machines aren't that powerful,
so running one OS at a time would definitively be an advantage.

---

