---
title: "Macbook keyboard doesn't work"
date: 2007-02-28
forum: Apple Intel Users
---

### Post by xoai on 2007-02-28
I had still typed perfectly but suddenly the keyboard has been unusable. I logged out and restarted many time but it is still not working. I found out that the keyboard is ok when login but right after it finishes booting, it is down. I searched and see that there is an issue the same as mine but no reply. Anybody can help me?

---

### Post by Praill on 2007-02-28
Type:
```
sudo gedit /etc/X11/xorg.conf
```

Do you see something like this?:
```

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

```

If you dont, add it (back up your xorg.conf file first in case something goes wrong).
Then you can go [here]("http://wiki.debian.org/MacBook#head-f5949efa9270854674acdeafc41447da1cedc3ac") for information configuring specific macbook keys and the touch pad.

---

### Post by xoai on 2007-03-01
My xorg.conf is correct. I dont know why. I was using Juploadr and blah blah the keyboard is unusable.

---

### Post by buschi on 2007-03-11
Hi!

Kind of similar problem here on a Macbook with Herd 5... However, I even can't login any more! This happened already once, after reboot things were fine again. Now rebooting does not help...

Well, I guess I have to re-install as I did not install a ssh server so far :( Or has anyone a better idea?


Thanks,
Sebastian.

---

### Post by ouilsen on 2007-03-11
If your keyboard is ok at login but not later on, it's beryl. At least that was the case here. Strangely the console switch still works (FN + CTRL + ALT + F1 if I remember correctly). 

So I switched to compiz and it works!

---

### Post by xoai on 2007-03-12
But my Beryl still works well in safemode !?!? I dont know how to compare which processs run at startup in safemode and in normal.

---

