---
title: "Can't get into desktop anymore"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by hyper_ch on 2007-12-27
I got a strange problem:
I rebooted my computer because of some weird behaviour with Kontact and Konqueror...
then I just got the Ubuntu default background but no loging window or so (I have auto-login enabled)...
and then the keyboard didn't do anyhting and nothing else was loaded...
I thought maybe some glitch or something, tried again -> same result...

ok, I logged then into recovery mode and installed KDE through kubuntu-desktop...
restarted again, in KDM I saw the login manager, I could select my user with the mouse and type 3 letters of my password but then the keyboard stopped working again. The CapsLock and the LED right to it started flashing (the same happened in GDM)

Any idea what's wrong here?

---

### Post by rune0077 on 2007-12-27
Did your keyboard work normally while in recovery mode? Could be something wrong with it, like a bad cable (or running out of batteries if it's wireless)? Or is it only on the Gnome desktop it screws up?

---

### Post by spiderbatdad on 2007-12-27
eek. hope its not a hardware issue like bad sector on disk.

---

### Post by hyper_ch on 2007-12-27
works fine in windoze and recovery mode and entering the password for LUKS at bootup....

I don't think it's a bad secotr on disk as it happens with GDM and KDM and the disk was checked just before.

---

### Post by hyper_ch on 2007-12-27
I did not starx from the recovery shell and I got the working interface... but why the keyboard stops responding (or whatever's happening) when I try to login with kdm or gdm is stily a mystery to me.

---

### Post by hyper_ch on 2007-12-28
Another clue is the .xsession-errors file which tells me this:

```

Xsession: X session started for hyper at Fri Dec 28 00:44:04 CET 2007
can't lock memory: Cannot allocate memoryWARNING: not using secure memory for passwords
SESSION_MANAGER=local/gubi:/tmp/.ICE-unix/5280
Segmentation fault
Segmentation fault
Segmentation fault

```

However the only thing I know is that warnings and segfaults aren't good... but what is meant there or why I get that I don't know at all...

---

### Post by rune0077 on 2007-12-28
Maybe you should try to reinstall Gnome?

---

### Post by hyper_ch on 2007-12-28
I'll restup the whole system... haven't done a reinstall since Feisty Herd 5...

---

### Post by rune0077 on 2007-12-28
If it's just Gnome that's screwed, there's no need to reinstall the whole thing, just the Gnome desktop. It shouldn't mess up your other settings.

---

### Post by hyper_ch on 2007-12-28
it's not only gnome... same happens with kdm and kde

---

