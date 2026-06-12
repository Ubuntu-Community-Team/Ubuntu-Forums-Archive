---
title: "Ubuntu: Crashed, XP: Crashed.  Using Ubuntu LiveCD"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by cutlerite on 2006-11-29
I'm using the liveCD so any help would be totally awesome.

here's what I was trying to follow:

[http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/nVIDIA]("http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/nVIDIA")
I wanted to install Beryl, and I went and edited the xorg.conf, and I am pretty sure I ruined my ubuntu.

This was probably too big of a task for me, however right now, after I log in, all of the menu and buttons will load for a split second, and then disappear.

And I don't know if I should start a new topic, but I think I have my partitions/boot setup all messed up as well.  Because windows gets stuck at "starting up"

help?  AIM: TrentCutler, yahoo=cutlerite

---

### Post by LLRNR on 2006-11-29
Hi,

Ummm... why did you try to install the drivers according to an Edgy guide since you (appear to) use Dapper? :)

Ok, if there is no other way you can login, wait for your computer to boot, and when the login screen dies hit Ctrl+Alt+F1 - you'll get in a tty, you have to login and type in your password in text mode...

Now it's time to reconfigure your X Server: 
```
sudo dpkg-reconfigure xserver-xorg
```

Answer the questions and hopefully you'll get your GUI back.

HTH,

LLRNR

PS - You have in your User CP (Control Panel) an option to show AIM/Yahoo/MSN/Skype accounts under your personal info (at the right side of your username/avatar)

---

### Post by cutlerite on 2006-11-29
> **LLRNR said:**
> Hi,

Ummm... why did you try to install the drivers according to an Edgy guide since you (appear to) use Dapper? :)

Ok, if there is no other way you can login, wait for your computer to boot, and when the login screen dies hit Ctrl+Alt+F1 - you'll get in a tty, you have to login and type in your password in text mode...

Now it's time to reconfigure your X Server: 
```
sudo dpkg-reconfigure xserver-xorg
```

Answer the questions and hopefully you'll get your GUI back.

HTH,

LLRNR

PS - You have in your User CP (Control Panel) an option to show AIM/Yahoo/MSN/Skype accounts under your personal info (at the right side of your username/avatar)


dude seriously, thanks. I am using edgy.  I have no idea why it was on dapper.

I hope it works.

---

### Post by LLRNR on 2006-11-29
> **cutlerite said:**
> I am using edgy.  I have no idea why it was on dapper.

The link you posted is for Edgy indeed, but... I'm sorry maybe it's my fault but I COULD HAVE SWORED that I saw your "id" as "Ubuntu 6.06 Dapper User"... I might be wrong of course, in this case please forgive my partial blindness :)

Good luck ! ;)

LLRNR

---

### Post by cutlerite on 2006-11-29
> **LLRNR said:**
> The link you posted is for Edgy indeed, but... I'm sorry maybe it's my fault but I COULD HAVE SWORED that I saw your "id" as "Ubuntu 6.06 Dapper User"... I might be wrong of course, in this case please forgive my partial blindness :)

Good luck ! ;)

LLRNR

Oh it did.  I went and changed it.  Now my question for you, 


someone said my problem is that I have beryl starting when I enter gnome, beryl though can't run with your xorg.conf.

I had the beryl-manager in startup.

---

### Post by kvonb on 2006-11-29
If you have the Edgy CD, you might want to try my guide here:

[http://ubuntuforums.org/showthread.php?t=301364](http://ubuntuforums.org/showthread.php?t=301364)

It seems that some people have had success with nvidia cards too.

---

### Post by LLRNR on 2006-11-29
Hmmm I don't know what to say, I also have beryl-manager loaded on startup, but since I use KDE I put a script in ~/.kde/Autostart... I don't remember how to do it in Gnome, i.e. to enable / disable something from running at the beginning of each session, but I think it's a setting that you can change graphically (through the System menu or something like this).

I **DON'T** want to discourage you at all, but I just wanted to try Beryl out of curiosity (I wanted to see if I could make it run on my PC which has really low specs); I used Dapper before, and I tried twice to install Beryl/XGL, using 2 different guides and being sure I knew the stages I went through - it was useful indeed since something went wrong every time and I had to "restore" my system the way it was.

Anyway, I run Edgy for 2 days now :) and I just installed Beryl from [here](http://doc.gwos.org/index.php/BerylOnEdgy) (I have a nVidia card) - I must tell you that this time it works awesome - it's clean, smooth, fast and a lot more stable (I also got the beta 0.1.2 version of Beryl).

So the thing is to be lucky enough to find a guide that is "appropriate" for your system configuration. Unfortunately, there's no guarantee in this, after all it's just a trial-and-error process (it's fun too).

About "trial and error", yes, I also fiddled around with my xorg.conf file, doing backups though, and in the worst case scenario there's always "sudo dpkg-reconfigure xserver-xorg". Still, you're aware of this, this operation will result in overwriting your current xorg.conf file, so there's a chance that you might have to redo some stages...

LLRNR

---

