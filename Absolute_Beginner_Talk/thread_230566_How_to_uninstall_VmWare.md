---
title: "How to uninstall VmWare"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by neewby on 2006-08-06
How do i uninstall vmware server???

---

### Post by Kobalt on 2006-08-06
Remeber there is a search tab in this forum... 
If you had searched you would have found thins link, to install & uninstall VmWare :
[http://www.ubuntuforums.org/showthread.php?t=183209]("http://www.ubuntuforums.org/showthread.php?t=183209")

Cheers !

---

### Post by arbogast on 2006-08-06
if it appears in the Synaptic Package manager just r-click it & mark it for removal.

I am a newb myself - this is how i've managed to install/uninstall progs.

Hope this helps

---

### Post by djsroknrol on 2006-08-06
In the temp directory you ran the install script from, run:

```
sudo ./vmware-uninstall.pl
```

that should do the job for you...

---

### Post by krewemaynard on 2006-08-24
> **Kobalt said:**
> Remeber there is a search tab in this forum... 
If you had searched you would have found thins link, to install & uninstall VmWare :
[http://www.ubuntuforums.org/showthread.php?t=183209]("http://www.ubuntuforums.org/showthread.php?t=183209")

Cheers !

I used the search and wound up at this thread, which with the exception of your post was helpful to me. If you want to be a grouch with people asking for help ("try searching," "RTFA," etc), try the Debian forums.

Qrk's post in this thread may help too: [http://www.ubuntuforums.org/showthread.php?t=137340](http://www.ubuntuforums.org/showthread.php?t=137340)  Pretty much the same thing jsroknrol said. I ran 'locate vmware-uninstall' and found that it's also in /usr/bin, so it may already be in your path.

---

