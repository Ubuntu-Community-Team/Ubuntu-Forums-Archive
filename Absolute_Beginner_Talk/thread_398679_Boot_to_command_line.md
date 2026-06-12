---
title: "Boot to command line?"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by disk11 on 2007-04-01
I'm trying to setup a file/firewall server using 6.10 server edition, but I installed the ubuntu-desktop metapackage so I can have a GUI.  How do you edit GRUB's menu.lst file so Ubuntu will boot to the stock command line login prompt and not use the recovery console?

---

### Post by bukwirm on 2007-04-01
Try the advice on [this page]("http://www.plug.org/pipermail/plug/2005-October/017588.html").

---

### Post by jnoreiko on 2008-01-31
..which, for reference, is:

```
update-rc.d -f gdm remove
```

How do I reinstate gdm in the future, so system boot is back to normal?

---

### Post by DouglasAWh on 2008-03-11
This doesn't answer the question, but I got here looking for this.  "recovery mode" is how you boot into the command line if you want to just do it once...of course, that didn't actually help me, so off to post another thread.

---

### Post by tubasoldier on 2008-03-11
to do it properly you will have to remove gdm from the services at runlevel 5. If you install BUM (boot up manager) you should be able to do this graphically.

---

