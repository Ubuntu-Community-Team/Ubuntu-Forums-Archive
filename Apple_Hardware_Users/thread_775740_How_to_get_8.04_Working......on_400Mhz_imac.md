---
title: "How to get 8.04 Working......on 400Mhz imac"
date: 2008-04-30
forum: Apple Hardware Users
---

### Post by shgadwa on 2008-04-30
I still need to get xubuntu 8.04 working on this imac here. I did what other suggested and edited the /etc/x11/xorg.conf file. It said there was no such file or directory....???? So, I edited the xserver-xorg file which I thought should work but I get the same thing as I thing as I did before.

If I type "Linux nosplash video=ofonly" on the second bot prompt, then it will load and tell you what its doing...it seems to lock up and get no further.....???

Its not the date bug, I set the date right...what is it????

Help.

---

### Post by shgadwa on 2008-04-30
OK.........It is X11 not x11, I edited the file but now it says...

Kinit: No resume image, doing normal boot....


and then I can sign in to the command line...........??:-k

---

### Post by avtolle on 2008-04-30
> **shgadwa said:**
> OK.........It is X11 not x11, I edited the file but now it says...

Kinit: No resume image, doing normal boot....


and then I can sign in to the command line...........??:-k
Have you looked at this thread? It is for a g3 imac, and, as you will see, the file is different from that which I posted for a g4 Cube in the display, etc., sections. Why don't you try to edit the /etc/X11/xorg.conf file to the values shown here, and see if that will be helpful.
[http://ubuntuforums.org/showthread.php?t=770033](http://ubuntuforums.org/showthread.php?t=770033)

---

### Post by noriek on 2009-01-20
Hi.

A slight hi-jack here but it may prove useful. I had a painful time with *ubuntu on my iMac DV 400mhz (possibly same as yours?) so I did a net install of debian which installed without a hitch first time. I'm thinking perhaps you could do this and apt-get the *ubuntu kernel and desktop packages from the ubuntu repositories? Anyone know if this is possible? I assume this would near as damnit be a full ubuntu install?

---

### Post by noriek on 2009-01-20
ooops, didn't realise this thread was so old. All the same does anyone know if this method would work? Could save a lot of issues for those trying to install on G3

---

