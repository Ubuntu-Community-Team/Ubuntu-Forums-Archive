---
title: "how to install numlockx. numbers lock on boot."
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by gordong11 on 2006-04-01
hello,

I saw this posted somewhere, but I cant seem to find it. I just want to install numlockx, so the number lock starts on bootup.

Can anyone help? Thanks

Gord

---

### Post by red_Marvin on 2006-04-01
You need to enable the universe repositories:
Walkthrough here:
[http://ubuntuguide.squarecows.com/doku.php#repositories](http://ubuntuguide.squarecows.com/doku.php#repositories)

---

### Post by Mustard on 2006-04-01
Do you have the universe and multiverse repositories enabled?

[http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse](http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse)

If you have then you do this to install

```
sudo apt-get install numlockx
```

I think the setup is something along these lines.

Adminstration>>Preferences>>Sessions , got to the Startup Up tab, then add numlockx to the startup programs.

Just executing via the terminal command, 'numlockx' does it temporarily, but to do it at startup will mean that it will be executed each time gnome desktop manager starts.

---

### Post by catlett on 2006-04-01
If your like me and like things easy. Automatix can install numbers lock for you. [http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)

---

### Post by gordong11 on 2006-04-01
ah yes..thats it...thanks!!!

---

### Post by dvarsam on 2006-04-01
In My PC, my BIOS has an enable/disable the keyboard's numlock.

If you want you could first check on that, before you go on & install additional apps...

---

### Post by gordong11 on 2006-04-01
[QUOTE=catlett]If your like me and like things easy. Automatix can install numbers lock for you. [http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)[/QUOTE]


I got it installed....but curious can Automatix run on 64bit breezy? I see the i386 at the end of the WGET link, so it made me hesitate. Thanks

---

### Post by Sef on 2006-04-02
> but curious can Automatix run on 64bit breezy?

It can only run on 32 bit systems, right now.

---

