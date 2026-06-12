---
title: "Newbie installing issue"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by georgew77 on 2008-03-22
Hi new user to ubuntu,

First off thanks for the time to read and respond to this.

I downloaded the 7.1 file from the internet and burnt it to a cd, stick it in the drive and boot it it does the loading kernel bar after selecting start or install, it gets to 100% and then simply hangs and doesnt do anything.

Do I have a duff cd/download or do I need some special options?

I am using a HP TX1000 (TX1138EA) laptop but have also tried using it in a packard bell laptop and it does the same thing.

I am reading through the help and forum trying to resolve but as yet have not seen anything that will solve this problem, hence the post.

Thanks,

G.

---

### Post by ghost_ryder35 on 2008-03-22
have you tried booting using Safe Graphics Mode

---

### Post by georgew77 on 2008-03-22
Yeah ive tried that, just writing a new cd, will let you know how that goes...

G.

---

### Post by acidsolution on 2008-03-22
i too had the problem before when i tried installing 7.04 but , safegraphics mode was working fine for me then

---

### Post by georgew77 on 2008-03-22
CD looks like a dud, new one has gone straight past that bit, now i have translating orange progress block....  

Fingers crossed.

G.

---

### Post by which_chick on 2008-03-22
Don't give up if the second CD dies on you -- if that happens, try the "alternate install" option -- it's what worked for me.  Sometimes, the installer has trouble with your graphics card and just ... can't.  The alternate-install method worked for me -- I got a low-graphics screen in gnome where I could "enable restricted drivers" and that fixed everything.

Good luck!

---

### Post by georgew77 on 2008-03-22
Ok now its locked on a text screen at

* Starting ConsoleKit daemon console-kit-daemon

Sigh.

G.

---

### Post by tvtech on 2008-03-22
my suggestion have em' ship you a free one!

---

### Post by georgew77 on 2008-03-22
I stuck a noapic on the F6 options and im in now it seems...

G.

---

### Post by waspbr on 2008-03-22
dude, I got the same laptop series, there's a thread on it

[http://ubuntuforums.org/showthread.php?t=442483]("http://ubuntuforums.org/showthread.php?t=442483")

it's a large thread so lemme give you the links for  2 summary posts:

this is the one i wrote:
[http://ubuntuforums.org/showpost.php?p=4413930&postcount=652]("http://ubuntuforums.org/showpost.php?p=4413930&postcount=652")

and this is one someone else wrote:
[http://ubuntuforums.org/showpost.php?p=4452489&postcount=18]("http://ubuntuforums.org/showpost.php?p=4452489&postcount=18")

if ya have any questions just post in the thread

for installing just adding```
noapic
```

to the command line should work, after you install,  I would recommend you add ```
noapic irqpoll doscsi
``` 

that's what woks for me



good luck

PS: remember to burn you (vista/xp ) recovery disks before installing anything

---

