---
title: "use a television monitor to my laptop"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by darkstr2o4 on 2008-02-09
I am able to use my television as a second clone of my laptop monitor with a standard monitor cable from my laptop to the RGB input on my television. I mainly use this to watch videos and such on my television rather than my small laptop screen.  However, the only way I can manage to get the computer to recognize the TV as a second monitor is to reboot with the cable plugged in.   I have integrated graphics on an older IBM thinkpad R31.  Is there a way to get Ubuntu to recognize that the TV as a second  monitor without having to reboot?

---

### Post by Rocket2DMn on 2008-02-09
Does hitting the monitor hotkey on your keyboard not work ( something like Fn+F8 ).  Otherwise you can try restarting X instead of doing a full reboot (CTRL+ALT+BACKSPACE to force X to reload - make sure you have everything saved and closed first).

---

### Post by darkstr2o4 on 2008-02-09
The  hotkey Fn +F7 does not seem to work. ctrl + Alt + Backspace does work. seems like a much better alternative to rebooting for now but I would like to get the hotkey to eventually function. Thanks.

---

### Post by Rocket2DMn on 2008-02-09
That's a good start.  I think Fn+F7 key might be a hardware setting which has to be set in BIOS (if it's configurable at all).  Not entirely sure, though.

---

### Post by asmoore82 on 2008-02-09
IBM Thinkpad T42 here with ATI Integrated Graphics...

I have exactly the same situation as you and I just reboot.
In theory I could connect the TV, turn off X, reload the ati modules and start X again;
but the non-free ATI drivers like to lock up when you switch to a console and back, so I just reboot.

If you have ATI too, you/I/we could make the clone display setup permanent
by using aticonfig to add the proper lines to xorg.conf
you can check in terminal if you have ATI like this:
```
lspci | grep VGA
```

---

### Post by darkstr2o4 on 2008-02-10
Looks like its an Intel 82830 chipset graphics controller.

---

