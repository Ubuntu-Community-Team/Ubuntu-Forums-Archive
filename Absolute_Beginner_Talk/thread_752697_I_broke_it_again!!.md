---
title: "I broke it again!!"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by Zralou on 2008-04-11
After days of trying to set up my video drivers (previous thread, 13 pages long!!), I finally get things working.
Last night I used Hardy and downloaded the updates that were waiting when I logged in.  Tonight I fire up the system only to find a black screen where the log-in used to be.  It displays the 'Nvidia' splash, then flickers and gives the message:
> Nvidia drivers xxx.xx is already installed on this kernel. then goes to a black screen.

I assume the update has installed video drivers and that is now conflicting, but my problem being new to Ubuntu is, i'm not sure how to edit xorg.conf in a non GUI environment.  I normally use 'Kate', but that obviously doesn't work without x-server.
How do I get into an editor to change the xorg.conf?.

Sara Lou

---

### Post by JoshuaRL on 2008-04-11
In the Recovery Mode do:
```

nano /etc/X11/xorg.conf

```

Nano is a CLI text editor and it should let you view and change your xorg.conf.  You won't need sudo since you are root when you are in Recovery Mode.

---

### Post by Zralou on 2008-04-11
Ok, thanks, i'll try that and see what happens.

Sara Lou

---

