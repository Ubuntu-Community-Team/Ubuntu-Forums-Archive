---
title: "Can't login with KDE"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by Sarteck on 2007-09-30
**Problem**:  When I enter my user name and password in the KDE Login manager, it "acts" like it's starting up (screen flickers for a moment), then goes right back to the KDE Login Manager.

[Yes, I am using the correct password and username.]

**Temporary Solution**:  I have to switch to a console (Ctrl+Alt+F1 for the first terminal), login, and then start GDM (**sudo gdm**).  This "acts" like it's going to start GNOME, but the screen stays black.  I Ctrl+Alt+Backspace, then, to shut down the X Server, and then the GNOME Login Manager appears.  From here, I can log into my KDE session just fine.

**Possible problem?**:  It took me a while to get my onboard nVidia GeForce 6150SE nForce 430 working on Kubuntu Feisty, 7.04.  I had installed a lot of programs and whatnot since then, and only shut down once, because my mother needed the Shockwave plugin for her Math course, so I had to let her use the Windows partition.  When I logged back on, had this problem.

I have tried restoring the original xorg.conf, but all that for me was to cause me a whole heap of trouble getting my nVidia working again. XD  So I guess it's possible it's not X or nVidia, since it still did the same thing afterwards.

I've been a Kubuntu user for a while, but I'm quite a newbie to posting problems (as in, I don't know which logs I should include, which would be relevant, etc.), so I'll have to ask that you tell me what logs to fetch if you need them, and how to fetch them.

Thanks.

---

### Post by mendingo84 on 2007-09-30
you messed up something in the X server configuration. Press CTRL +ALT+F1 to get the CLI. Ther enter this command and follow the steps ;) 
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Sarteck on 2007-09-30
Y'see, that's the problem...  I've already tried that to no avail.  (First thing I did was restore my original xorg.conf (I keep it as xorg.conf.ORIGINAL), then did the reconfig, then saved that as xorg.conf.bak, then did the nVidia stuff, kept THAT as xorg.conf.  Restarted, had a problem, so I assumed it was nVidia.  I restored xorg.conf.bak, still had the same problem.  I then restored xorg.conf.ORIGINAL, still had the same problem.

(Just to make sure, I tried it again, with the same results.)

---

