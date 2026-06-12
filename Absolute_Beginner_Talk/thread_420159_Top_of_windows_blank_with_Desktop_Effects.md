---
title: "Top of windows blank with Desktop Effects"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by yigals on 2007-04-23
When I enable Desktop Effects in Feisty the top of windows (especially Firefox) become blank (you can't see the close / minimize buttons)

I use IBM T30 with ATI RADEON 7500 16MB, P4 1.8 ghz

---

### Post by Cypher on 2007-04-23
I installed Beryl and had the exact same thing happen. I then tried desktop-effects and it also behaved the same way. The various effects seem to work, however I lose the border on the windows so that I can't do anything with them.

I would also love to read a solution for this..

Regards

**UPDATE:** I searched on Beryl's forums and found the answer, if you have a NVidia video card like I do, then there's an option that needs to be added to the /etc/X11/xorg.cnf file to make things work. Get details at: [http://forum.beryl-project.org/viewtopic.php?f=35&t=1631](http://forum.beryl-project.org/viewtopic.php?f=35&t=1631).

---

### Post by Yuzem on 2007-04-23
You can try this:

```
metacity --replace&
sudo killall emerald&
```

Then enable Desktop Effects

---

### Post by yigals on 2007-04-24
Not helping for me

---

### Post by Yuzem on 2007-04-25
Sorry, it was wrong.

Try this:
```
gtk-window-decorator --replace&
compiz --replace&
```

---

### Post by yigals on 2007-04-26
Still not helping, I npotice that change is being made, but it won't solve the problem, do I need to restart or anything in order to to this take effect?

Anyways, I found this thread too, it has a few solutions, I haven't tried them all yet:
[http://ubuntuforums.org/showthread.php?t=412527&page=3](http://ubuntuforums.org/showthread.php?t=412527&page=3)

---

### Post by Yuzem on 2007-04-26
When Desktop Effects is enable can you move the windows (alt+clic and drag)?
Try this:
[http://ubuntuforums.org/showpost.php?p=2535540&postcount=27](http://ubuntuforums.org/showpost.php?p=2535540&postcount=27)

---

### Post by 5-HT on 2007-04-26
> **yigals said:**
> Still not helping, I npotice that change is being made, but it won't solve the problem, do I need to restart or anything in order to to this take effect?

Anyways, I found this thread too, it has a few solutions, I haven't tried them all yet:
[http://ubuntuforums.org/showthread.php?t=412527&page=3](http://ubuntuforums.org/showthread.php?t=412527&page=3)

You will need to restart X for any changes to take effect (either by a ctrl+Alt+Backspace or a reboot, or other....)

I had a similar problem because my default colour depth was set to 16 instead of 24.
If you take a look at /etc/X11/xorg.conf, under section 'screen' you will find your colour depth. Does changing it to 24 solve the problem?

---

### Post by yigals on 2007-05-05
No depth value for me under screen section

---

