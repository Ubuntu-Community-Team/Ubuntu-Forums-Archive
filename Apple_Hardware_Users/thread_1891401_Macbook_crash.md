---
title: "Macbook crash"
date: 2011-12-05
forum: Apple Hardware Users
---

### Post by charliedudeck on 2011-12-05
My Macbook was working fine with Ubuntu - and then suddenly stopped working.  When I turn the computer on now all that happens is the Ubuntu logo appears followed by a screen with shut down options and a box in the center teling me who the computer belongs to.  Does anyone know what I can do to get the computer working again - and if at all possible - save what I had on the harddrive?

---

### Post by Anon7-2521 on 2011-12-07
Did you try logging in?

---

### Post by Rxke on 2011-12-08
Can you describe what you see exactly? is it a login screen?


In any case no worries, you should -in 99% of cases- be able to boot up from a livedisk and save things to an external disk/ USB key.

---

### Post by Anon7-2521 on 2011-12-09
Did you try dropping down to the TTY, logging in and then startx?

---

### Post by charliedudeck on 2011-12-11
I don't know what TTY is - but the screen that appears has no options other than shutdown restart or suspend.  It just tells me who the Macbook belongs to in the middle of the screen - otherwise that's it.
in terms of sounds - it definitely whirls - the fan or something - but I don't specifically remember the scratchey sound.  The sound, not - though, is exactly the same as it was when the computer was working fine.

---

### Post by island_monkey on 2011-12-11
A TTY is a terminal. To get to one, press Cmd + Alt + any F button from 1 to 7.

When you get to it, login, then type:
```
sudo pkill X
```

The X must be uppercase.

---

### Post by charliedudeck on 2012-01-31
So I tried this - and when I enter in Sudo pKill X the response is "no Sudo image kernel found" and then it simply goes to the Linux installation disk. I'm trying to install the Linux onto the computer hoping once I have Linux installed I may be able to access the old Ubuntu (11.4) and all my old data - but I can't even install the new Linux (11.10) because of partitioning problems (it tells me I don't have a root file).  What can I try next?

I checked my bootCD and found that it has to 2 errors, so re-burned, re-checked and found it perfect, and then installed it on the Mac and Ubuntu was installed...or thought it was: when the cd ejected and the computer re-started the white screen appeared and after a few moments a folder with a question mark appeared. Now, I know that Ubuntu has installed - actually twice now - but for some reason when I boot without the CD the computer has no way to access it. Any ideas of what I can do?

---

