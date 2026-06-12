---
title: "Minimize leaves a trail of boxes!!"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by bootslap on 2007-01-27
Hi .. I am on Dapper Drake with a VIA PN800 graphic card. I have assigned approximately 6 GB to root and 6 GB to /home with 1 GB to swap. However, whenever I minimize my windows it leaves a trail of rectangular boxes. I was just wondering if there is a way this can be fixed..

Thanks in advance!!

---

### Post by charles.g.moore on 2007-01-27
Mine does it too but I think it has something to do with the settings associated with the window manager or theme...

Are the trails really slow to fade?

Do you have 3d acceleration with the vid card drivers?

---

### Post by bootslap on 2007-01-27
Hi .. thanks for your reply... I do not have 3D acceleration, but the boxes does not take long to fade. It is fast, but it is distracting at times ... and Window users just love to tell me that my box is screwed up due to linux... but I think there is definitely a solution to it.

---

### Post by jordanmthomas on 2007-01-27
A quick fix would be to disable the boxes from ever coming up:
Press Alt + F2 and type:
```
gconf-editor /apps/metacity/general
```
In the pane on the right, you can choose to turn on reduced_resources to get rid of the wireframe boxes.  It says it lowers usability, but I never had a problem with it turned on.

If you want to keep the boxes you will need better graphics drivers as charles.g.moore suggested.

---

### Post by bootslap on 2007-01-27
But isn't ubuntu supposed to be friendly with low config systems?

---

### Post by jordanmthomas on 2007-01-27
It is if you disable the extra eye-candy.  :)
If you want it to be really fast try installing e, fluxbox, or even something like xfce.  Everything'll be a lot faster after that.

---

### Post by bootslap on 2007-01-27
Hi jordanmthomas .... your advice helped. It is not leaving any trails now...Yeah, I know that XFCE would be fast as I use Puppy and DSL also at times ... just for fun... but ubuntu is my workhorse and would like it to be as user friendly as possible ... Thanks again for your advice..

---

### Post by xmastree on 2007-01-27
> **jordanmthomas said:**
> A quick fix would be to disable the boxes from ever coming up:
Press Alt + F2 and type:
```
gconf-editor /apps/metacity/general
```

Wow, I didn't know you could do that. Thanks.

> **jordanmthomas said:**
> It is if you disable the extra eye-candy.  :)So those black lines are considered eye-candy, are they? :confused:

---

### Post by NanoXbuG on 2007-01-27
A most satisfying solution indeed!

---

### Post by xmastree on 2007-01-28
Hmm... There is an annoying side-effect though. When dragging or resizing a window, lines appear on it dividing it into 3x3 sections.

---

### Post by miceagol on 2007-07-14
Anyone know any better way to fix this than just the workaround suggested by jordanmthomas? It doesn't completely remove the problem. When resizing windows, switching between windows or maximizing/minimizing windows, there's a short delay before the content inside the windows is redrawn. In addition scrolling is slow.

---

### Post by erginemr on 2008-03-17
The new version of metacity (to be implemented in Hardy) supports basic compositing such as drop-shadows under windows and menus. It also replaces the lines shown during minimize and maximize with a better animation.

So, for those who you are not currently using Compiz, you can give the new metacity compositor a try by following the thread:
[http://ubuntuforums.org/showthread.php?t=648364](http://ubuntuforums.org/showthread.php?t=648364)

and downloading and installing the three debian packages given by the OP.

---

