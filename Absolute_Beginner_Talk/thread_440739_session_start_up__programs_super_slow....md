---
title: "session start up  programs super slow..."
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by searayman on 2007-05-11
alrighty, i am running ubuntu feisty wth beryl and so forth.  Even before i installed beryl it took a supe rlong time before the window manager came up, i usually started it in termianl by hand, becaus eit was quicker. 

But no i have compiz and i added that to the session manager and changed the order to 45 and it too either doesnt start or take for ever.

---

### Post by Billy_McBong on 2007-05-12
i have the same problem my start up programs take forever to come up and somehow i feel it is caused by compiz.

---

### Post by searayman on 2007-05-12
> **Billy_McBong said:**
> [COLOR="Blue"]i have the same problem my start up programs take forever to come up and somehow i feel it is caused by compiz.[/COLOR]

see i dont think it is compiz because i had the sma problem before i enabled it. Metacity wouldnt load, untilll late.

OK so i noticed when i changed things orders in the session manager i wasnt saving. SO i saved it now and things still load up very late....

---

### Post by Billy_McBong on 2007-05-13
i dont think i had the problem before i enabled compiz but i disabled it and they still start up really slow

---

### Post by moe_syzlak on 2007-11-20
I have compiz installed but not turned on. I don't think that compiz has anything to do with it.

hdparm is a console program that can tweak the HDD for more speed. I looked at my hdparm.conf and it was not configured. Also I found out that hdparm service (just the init script to configure the hard drive at boot time) was not set to run at boot time. I have a SCSI drive.

With that said, the system loads in a normal amount of time, but the programs launched in gnome take forever to show up in X.

Right now I'm configuring tons of stuff in Ubuntu. doing what Conical should've done. Damn you mark. I'm gonna restart and let you guys know the results.

---

### Post by moe_syzlak on 2007-11-20
I restarted and no effect on program startup times. Firefox, gnome-terminal, KTorrent and anything that has gui still takes 30 seconds to load. I am on a pretty fast laptop, AMD Turion X2 1.6Ghz, 1GB RAM, 120GB HDD. I used to be able to play CS:S in 800x600 at 45fps on Windoze.

---

### Post by carstanje on 2007-11-21
You can try resetting your session. All your startup programs are defined in a so called *session* file.

This file will be recreated during login as soon as you removed it. I suggest you move it just in case something goes wrong.

Open a terminal and type:

```
mv .gnome/session .gnome/session_old
```

After this, reboot and you should be fine. All you have left is to add your favourite programs in your session again if you have any.

---

### Post by moe_syzlak on 2007-11-22
if anyone wants to chat about ubuntu IM me,  tmantist on Yahoo messenger

---

### Post by carstanje on 2007-11-22
The session file could also be in the .gnome2 directory, in this case use:

```
mv .gnome2/session .gnome2/session_old
```

the .gnome2 directory is hidden, so won't see this directory on default. Did this work?

---

