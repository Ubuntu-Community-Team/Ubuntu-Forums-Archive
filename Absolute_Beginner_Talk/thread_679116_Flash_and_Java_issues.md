---
title: "Flash and Java issues"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Famicommander on 2008-01-26
I've installed flashplugin-nonfree and ubuntu-restricted-extras, but I still can't watch any videos or anything in either Opera or Firefox.

Does anyone know how to fix this?

---

### Post by FuturePilot on 2008-01-26
The flashplugin-nonfree is broken right now.
Have a look here
[http://ubuntuforums.org/showthread.php?t=636397]("http://ubuntuforums.org/showthread.php?t=636397")

---

### Post by family on 2008-01-26
Hmm, I havent looked at the link yet, but what I did for Flash (for Firefox) was go to Adobe's Flash page, download the Linux version, unpack it, and run the installer.
That may be what FuturePilot is suggesting, but I haven't looked at the link yet.
As to why videos wont play (in Firefox), check if you have totem-mozilla installed.
```
 sudo apt-get install totem-mozilla 
```
Do vids play ion your Desktop?

---

### Post by doorknob60 on 2008-01-26
I'll confirm that installing flash player from the tar.gz from the adobe site is the easiest way to get flash working right now :)

---

### Post by jan quark on 2008-01-26
here I have a quick tutorial on this issue
[http://janquark.fatfreehost.com/tutorial3.html](http://janquark.fatfreehost.com/tutorial3.html)

perhaps it helps

---

### Post by Famicommander on 2008-01-26
> **FuturePilot said:**
> The flashplugin-nonfree is broken right now.
Have a look here
[http://ubuntuforums.org/showthread.php?t=636397]("http://ubuntuforums.org/showthread.php?t=636397")

Thanks a lot. That fixed it.

---

