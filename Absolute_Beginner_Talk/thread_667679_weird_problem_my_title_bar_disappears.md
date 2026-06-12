---
title: "weird problem: my title bar disappears"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by warthogism on 2008-01-14
this problem is random and intermittent.  I've no idea what causes this, but the title bar just completely vanishes.  the only fix i've found is to restart.  It does not happen every time i use the computer, but enough to make it annoyingly frustrating.

I've attached a screenshot to help illustrate the problem

[IMG]http://i16.photobucket.com/albums/b11/wartser/Screenshot-2.png[/IMG]

i've no idea where to start on this one.  Any help is appreciated.

---

### Post by timbounceback on 2008-01-14
this is most likely because of metacity being randomly killed.

---

### Post by b0rka7a on 2008-01-14
To fix it without rebooting, press Alt+F2 and type:
```
metacity --replace
```

---

### Post by warthogism on 2008-01-16
thanks.  I'll try that the next time it happens.

Btw, what is metacity, and what does it do?

---

### Post by warthogism on 2008-02-03
I tried the command you suggested, but it didn't quite do what was expected.  While the title bars did reappear, it changed my theme and some windows disappeared (firefox, awm, others).  logging out and back in seems to fix the problem for now. it sure is annoying though.

---

### Post by spiderbatdad on 2008-02-03
It looks as though you are using a custom gtkrc-2.0 file. Is the missing title bar particular to a session, or does the theme manager work in a session and then develop the trouble? All I can think of is Remember Currently Running Applications under Preferences>>Sessions>>Session Options...but I always say that.

---

### Post by SunnyRabbiera on 2008-02-03
> **warthogism said:**
> thanks.  I'll try that the next time it happens.

Btw, what is metacity, and what does it do?

Metacity is the window manager in Gnome and Gnome is a desktop environment (what you use to see your icons/ files/ etc)
This will give you more information:
[http://en.wikipedia.org/wiki/Metacity]("http://en.wikipedia.org/wiki/Metacity")
[http://en.wikipedia.org/wiki/GNOME]("http://en.wikipedia.org/wiki/GNOME")

---

### Post by warthogism on 2008-02-03
> **spiderbatdad said:**
> It looks as though you are using a custom gtkrc-2.0 file. Is the missing title bar particular to a session, or does the theme manager work in a session and then develop the trouble? All I can think of is Remember Currently Running Applications under Preferences>>Sessions>>Session Options...but I always say that.

the problem pops up randomly after i've been at work for a bit.  It's really quite rare, but annoying as heck when it does happen.  As of right now, I just log out and then back in again.

---

### Post by spiderbatdad on 2008-02-03
i didn't  think metacity supported gl desktop. I believe you should be using Emerald as your windows manager.

---

### Post by SunnyRabbiera on 2008-02-03
> **spiderbatdad said:**
> i didn't  think metacity supported gl desktop. I believe you should be using Emerald as your windows manager.


If you use compiz it wraps around metacity.
This issue might be fixed by turning off effects.

---

### Post by lmbb20 on 2008-06-13
What theme are you using when this occurs? I had the exact same problem when using Clearlooks. I have since switched to Crux and the title bar has not disappeared. Hope that helps. :)

---

