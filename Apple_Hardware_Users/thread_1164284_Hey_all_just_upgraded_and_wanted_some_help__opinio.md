---
title: "Hey all just upgraded and wanted some help / opinions"
date: 2009-05-19
forum: Apple Hardware Users
---

### Post by mattgaunt on 2009-05-19
Hey everyone,

I just upgraded from hardy heron to jaunty and initial thoughts were amazing, dual screens working, fast boot time, tidy up on the menu stuff.

Anyway after using it for a bit there are a few things I was wondering if anyone could help me with / give advice on

First off is there anyway way I can make my left cmd key a ctrl key? I want the others to be ctrl too, this one to be an extra one? I did it in hardy pretty easily but I cant remember for the life of me how.

2nd Skype - I know the skype team seemed to of stopped building the linux version of skype so Im not too surprised that it's broken, but does anyone have any idea's as to why it has a problem accessing the sound when I haven't run anything which uses sound?

Finally my graphics card on the macbook 4.1 has been black listed, does anyone know if it is wise to remove it from the blacklist? Ideally I would have effects on mainly for gnome-do, but I do need stability, and on the thread I read it said that doing this may make it unstable and just wondered if anyone had any experience ([http://ubuntuforums.org/showthread.php?t=1131754](http://ubuntuforums.org/showthread.php?t=1131754)).

Many thanks,
Matt

---

### Post by cyberdork33 on 2009-05-19
well the reason it is blacklisted is because it is unstable. unblacklisting it brings the unstability back.

---

### Post by mattgaunt on 2009-05-20
Ok all I didnt get is it worked in hardy :-S

No worries, though, is there an easy way of getting cmd to be ctrl? or is my only option setting up a modmap thingy?

---

### Post by cyberdork33 on 2009-05-20
> **mattgaunt said:**
> Ok all I didnt get is it worked in hardy :-Syep it got blacklisted in Jaunty.

> **mattgaunt said:**
> No worries, though, is there an easy way of getting cmd to be ctrl? or is my only option setting up a modmap thingy?
Probably just xmodmap. There were a few options in the keyboard preferences, but nothing that would swap the two keys.

---

### Post by mattgaunt on 2009-05-21
Ok well thanks for the help cyberdork ):P

---

### Post by Gen2ly on 2009-05-21
The control-key can be mapped to the Apple key in xorg.conf:

```
XkbOptions
    Option      "XkbOptions"    "altwin:ctrl_win"
```

I don't have my MacBook anymore so i don't have a full reference to it, but it should get you started.

---

