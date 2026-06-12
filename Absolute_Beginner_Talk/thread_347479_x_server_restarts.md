---
title: "x server restarts"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by Tucatts on 2007-01-27
Ok finally figured out this is a x server problem. After logging on and going to desktop all seems normal and then 1 to 2 hours later it just goes back to the log in screen. I can log back in and resume fine but this is not cool for sure. Do I reconfigure x server perhaps. Any ideas would be most helpful.
Thanks,
Tucatts

---

### Post by Tomosaur on 2007-01-27
You can try reconfiguring X server, yes. Best way to do this would be to open up a terminal and type:
```

sudo dpkg-reconfigure xserver-xorg

```
You'll get a setup menu and it'll ask you a bunch of questions about monitor resolution, language etc etc. Just go through and configure it to how you want it.

Once it's done, restart the X server (by logging out and then hitting ctrl+alt+backspace). If you restart x server before you log out, your current session will not be saved, and you may get a few 'Program X did not close properly' when you next run some programs. It's not a big deal, it's just better to close your stuff before restarting X.

If this doesn't fix the problem, come back here and we'll see what we can do.

---

### Post by Tucatts on 2007-01-27
Thanks! I will give that a try.

---

