---
title: "beryl on kde/dapper/ati"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by Foudre on 2006-10-21
i was trying to install beryl on my computer ran into a snag, i tried to find a thread about this here, but nothing that was the same as me 

[code}
me@computer: beryl
beryl:  GLX _EXT_texture_from pixmap is missing
beryl:  Failed to manage screen :0
beryl:  No managable screens found on display :1.0
[\code]

so if any one else had this issue and knows what to do, i'm about to head over to the beryl forums, and see

---

### Post by jordanmthomas on 2006-10-21
This usually happens when you aren't running a proper X server (no XGL or AIGLX)

What is the output of 
```
ps -A | grep X
```

If you were trying to use XGL and Xorg (sans XGL) is running, you have a problem.
If you were trying to use AIGLX (which I doubt because of the ATI card) then on dapper you will see Xorg-air instead of Xorg.

Maybe you should look in whatever guide you followed about setting up your Xserver.

---

### Post by Foudre on 2006-10-21
1941 tty7     00:00:02 Xorg
 1999 ?        00:00:10 Xgl

---

### Post by jordanmthomas on 2006-10-21
In that case...not having XGL running is not your problem.

**slaps self on head

You either need to run 
```
beryl --replace
```
or
```
beryl-manager
```
and select beryl as the window manager.

Sorry I wasted your time before.

---

### Post by Foudre on 2006-10-21
score it works, and xgl was runing i just didn't get it working right i tried the command beryl as soon as i tried beryl-manager  it came up with this wicked cool spalsh screen

i saw that entry in the k menu but when i clicked it it would do nothing, as long as i remember to type it in its great, or create a start up script

---

### Post by jordanmthomas on 2006-10-21
Just to help because I am bored today:
```
kate ~/.kde/Autostart/beryl
```
and put
```
#!/bin/bash
beryl-manager
```
save and quit
```
chmod +x ~/.kde/Autostart/beryl
```


**OR THE FUN WAY**
```
ln -s /usr/bin/beryl-manager ~/.kde/Autostart/beryl
```

Maybe I helped, maybe I didn't.

---

### Post by Foudre on 2006-10-22
well the beryl-manager was helpful, the wiki didn't say to use that command, if it did i missed it a few times saying so, i think i'll edit it to tell people to do so

---

