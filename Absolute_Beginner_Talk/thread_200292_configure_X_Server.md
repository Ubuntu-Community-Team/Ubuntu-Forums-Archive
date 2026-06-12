---
title: "configure X Server?"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-06-20
HI,

The other day I found a thread somewhere that mentioned how to get to configure X Server ( I think that is what it was, it's X somehing) but now I can't find it anywhere, I have done a search but haven't found it. 

Can someone help?

---

### Post by aysiu on 2006-06-20
```
sudo dpkg-reconfigure xserver-xorg
``` and/or ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf
```

---

### Post by Russty of Oz on 2006-06-20
Thanks aysiu!  That was just what I needed.  

Is there somewhere I can find a list of commands and what they do?  Or do you guys just have INCREDIBLE MEMORIES?

Russty.

---

### Post by matrooswolf on 2006-06-20
[QUOTE=Russty of Oz]Thanks aysiu!  That was just what I needed.  

Is there somewhere I can find a list of commands and what they do?  Or do you guys just have INCREDIBLE MEMORIES?

Russty.[/QUOTE]
We do have incredible memories.  Uh, what was the other question again? ;)

Try some links in this thread for starters on common commands:
[http://ubuntuforums.org/showthread.php?t=194885](http://ubuntuforums.org/showthread.php?t=194885)

---

### Post by Russty of Oz on 2006-06-20
Thanks, that really is a great help, I have put those links in my FF Bookmarks so I DON'T FORGET WHERE TO FIND THEM!!  

Russty

---

