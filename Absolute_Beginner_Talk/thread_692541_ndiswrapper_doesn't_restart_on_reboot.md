---
title: "ndiswrapper doesn't restart on reboot"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by FreeJersey2007 on 2008-02-09
I've successfully installed a USB wireless adapter (TrendNet TEW-424UB) by following the instructions found throughout the forum.  The only problem I'm having now is that ndiswrapper doesn't want to start automatically upon a reboot.  I thought that by executing sudo ndiswrapper -m would do the trick.  However, it seems that every time I reboot, the usb won't engage until I go into Terminal and run sudo modprobe ndiswrapper.  Since the end result is that I'm up and running, this is a minor inconvenience.  However, when I had my internal wireless set up through ndiswrapper (before it died), I didn't have to keep manually restarting each time I booted up.  Any thoughts on this one?

---

### Post by Presto123 on 2008-02-09
Go into System/Preferences and click on "Sessions". In that applet, make sure you are on the tab marked "Startup Programs", click "Add" and name it whatever and place in that command and restart your computer. Only thing I see is that it might not start being a sudo command. 

Try it and see, if it doesn't work, we can try something else.

---

### Post by amingv on 2008-02-09
Try this:

```
sudo cp /etc/modules /etc/modules.backup
gksudo gedit /etc/modules
```

type ndiswrapper in the last line and save.

Should work when you reboot.

---

### Post by anewguy on 2008-02-09
I think sudo ndiswrapper -m  is supposed to do the same thing if anyone's interested.:)

---

### Post by Presto123 on 2008-02-09
> **anewguy said:**
> I think sudo ndiswrapper -m  is supposed to do the same thing if anyone's interested.:)

If it makes it easier on this fellow than what I told him, then, yeah! I'm interested. ;)

---

### Post by amingv on 2008-02-09
> **anewguy said:**
> I think sudo ndiswrapper -m  is supposed to do the same thing if anyone's interested.:)

According to OP he already tried that. It's not a complex process either way.

---

### Post by Presto123 on 2008-02-09
> **amingv said:**
> According to OP he already tried that. It's not a complex process either way.

LOL. I missed that too.

---

### Post by FreeJersey2007 on 2008-02-09
Thanks to all!  I took the modification to /etc/modules approach (not to say Sessions wouldn't work).  It worked like a charm.  Odd that the standard approach didn't work - like I said, it worked on this machine before and others that I've installed ndiswrapper.  This is a great backup plan.

Thanks again!

---

### Post by anewguy on 2008-02-10
Oooooppppsssss - my bad!   Soryy!:)

---

