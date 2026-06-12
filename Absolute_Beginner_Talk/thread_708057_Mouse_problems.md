---
title: "Mouse problems"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Loki*PI on 2008-02-26
I have PC2 mouse, nothing fancy, is optical.    The accelerator function doesn't work. In mouse preferences I move the slide somewhere in the middle and close the window and it defaults back to slow.  This is a new mouse and it worked fine when I first attached it. Now it takes two swaps across the mouse pad to cross the screen.
How do you reinstall the mouse drivers or does someone have another suggestion?   I'm a newbie so please keep it simple.
Thanks

---

### Post by mbsullivan on 2008-02-26
Hi!

Unfortunately, I don't have the default Ubuntu setup (including Gnome, etc) so I can't be *super* user friendly. That being said, I may be able to help you.

First, open a terminal (ALT+F2 by default, I believe). Then type any commands I tell you in order to set your mouse acceleration. From the command line, the way to set mouse acceleration is with the following command:

```
xset m **[ACCELERATION]** **[THRESHOLD]**
```

Where "m" denotes "mouse", **[ACCLERATION]** is a decimal number denoting the accleration variable, and **[THRESHOLD]** is another variable, normally set to 10. If you want more information on the specifics, here's what man (i.e. help) page has about the command:

> The m option controls the mouse parameters.  The parameters for
               the mouse are ‘acceleration’ and ‘threshold’.  The acceleration
               can  be  specified as an integer, or as a simple fraction.  The
               mouse, or whatever pointer the machine is connected to, will go
               ‘acceleration’ times as fast when it travels more than ‘thresh&#8208;
               old’ pixels in a short time.  This way, the mouse can  be  used
               for  precise  alignment  when it is moved slowly, yet it can be
               set to travel across the screen in a flick of  the  wrist  when
               desired.   One or both parameters for the m option can be omit&#8208;
               ted, but if only one is given, it will be  interpreted  as  the
               acceleration.   If no parameters or the flag ’default’ is used,
               the system defaults will be set.

Play around with the acceleration variable until it feels comfortable... My mouse feels comfortable @ 3.5. Leave threshhold @ 10, unless you really want to play with the settings:

```
xset m 3.5 10
```

Hopefully this won't change back instantly (I'm not sure why you're currently having that problem). If this helps, let me know and we'll talk about ways to make it apply this setting each time you start up.

Mike

---

### Post by Loki*PI on 2008-02-26
Hi Mike - yes that worked. Thank you very much.   Mouse is acting more normally now.  How do I make this permanent?

---

### Post by mbsullivan on 2008-02-27
Hi Loki*PI,

Okay... there are a bunch of ways to make it permanent. Unfortunately, since it must be done after X windows has started, it may be slightly different on your machine than mine.

Assuming that you are using gdm to login (if you have default Ubuntu then you do), I think the best way is to do the following:

(1) edit /etc/gdm/Init/Default (backing it up first):

```
sudo -s
cp /etc/gdm/Init/Default /etc/gdm/Init/Default.old
gedit /etc/gdm/Init/Default
```

(2) add whatever sensitivity you want to the end of the file, BEFORE "exit 0"

... save and hopefully this will be applied each time that GDM starts (@ bootup).

I think this works, and I would test it for you but I have some programs running that I can't cancel until they complete (so I can't restart my X server right now). If it doesn't work, try adding the command to the bottom of ~/.xsession, such that it reads like the following:

```
#!/usr/bin/env bash
xset m [ACCELERATION] [THRESHOLD]
exec gnome-session
```

If you don't have an .xsession you can just make one with the above commands. If you make it from scratch, you need to make sure that it's executable:

```
chmod +x ~/.xsession
```

Okay... let me know how it goes!
Mike

---

