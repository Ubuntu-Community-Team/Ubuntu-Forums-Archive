---
title: "ScreenSaver locks up System"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by des421 on 2006-09-19
I was simply trying the different provided screensavers. First 2 (blank & random) were OK, but when selecting the 3rd no thumbnail\sample was displayed and the system froze. The Preferences have been permenately set to the "bad" so that Screensaver can't even be selected from the Options without locking her up. Should the screensaver timeout a motionless image is dispalyed on the monitor (so that's there) with the same frozen system results.

This could be hardware related (Saphire Radeon 9700 Pro graphics card)? As I've filed a Bug which remains unconfirmed.

Question is... can anyone tell me how to modify the preferences back to one that works (default - random) from the terminal?

Thanks: DES

---

### Post by Miademora on 2006-09-20
You could try opening the **gconf-editor** and go to **/apps/gnome-screensaver/mode** and set the key **mode** to **blank-only**.

---

### Post by des421 on 2006-09-20
Yes! (I had found it before coming back to answer my own question.) After tracking down the configuration editor via the terminal, I then located "System Tools" on the "Alacarte Menu Editor" and turned on a list of goodies (eaiser to access). In the Configuration Editor\Apps\Gnome-ScreenSaver\ changing Mode to Random (default) unstuck things. (Think I get it now, you can have a blank screen or the system will choose a screensaver at "random".) But there's a problem here, choose a 'single' screensaver yourself from System\Preferences\Screensaver and you're done for this session! There's a ton of goodies available in the configuration editor. Why... it's the Windows registry... sort of.

Now, If I could just get my W98 machine connected to Ubuntu Shares.  Preferably in NetBEUI, but at this point I'll settle for connected. Ubuntu sees the Windows shares OK (although very slowly compared to M$ networking?).

Thanks: DES

---

