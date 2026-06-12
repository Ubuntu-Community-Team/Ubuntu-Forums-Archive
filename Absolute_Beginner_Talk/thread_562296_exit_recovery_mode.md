---
title: "exit recovery mode"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-09-28
how do I get out of recovery mode, after booting into it, without rebooting? I will no longer need/want root privileges but just want to start the ubuntu studio desktop as normal

---

### Post by overdrank on 2007-09-28
> **ginestre said:**
> how do I get out of recovery mode, after booting into it, without rebooting? I will no longer need/want root privileges but just want to start the ubuntu studio desktop as normal

Hi I believe you have to reboot to return to the desktop.

---

### Post by bapoumba on 2007-09-28
Yes, you do. Just enter **reboot**.

---

### Post by ginestre on 2007-09-28
I'm chasing an odd error that happens intermittently on bootup: the system hangs at initramfs, but not always. It never hangs on boot into recovery mode. I want to see if it hangs on moving into normal mode from recovery: so a reboot doesn't really help. There must be some way of getting from recovery to normal, without rebooting?

---

### Post by skymera on 2007-09-28
dont htink there is.
u can log in as a normal user, but not GUI, i thik

when u enter recovery, type 'exit' thenit should exit root and be left at a tty screen

---

### Post by ginestre on 2007-09-28
is this my answer?
```

$ exit
$ telinit 2
$ xstart

```

I'm unclear from my browsing whether the new upstart thingie supports telinit, but anyway I read somewhere that doing xstart as root is dangerous. Is that true? And if I do the above, then presumably I'm not doing xstart as root? Don't want to break anything.

---

### Post by sumguy231 on 2007-09-28
Ubuntu does use Upstart, but the telinit command still emulates the way it would behave on an init-based system. Going to runlevel 2 should start X anyway, but for future reference you probably want to do this instead of 'startx':
```
sudo /etc/init.d/gdm start
```

---

### Post by bodhi.zazen on 2007-09-28
telinit 2 will work

This should start GDM (automagically) and you can then log in as you normally would.

Hit Ctrl-Alt-F1 to return to the consul and log our (as root) ; Ctrl-Alt-F7 to return to gui world

---

### Post by bruce89 on 2007-09-28
> **ginestre said:**
> how do I get out of recovery mode, after booting into it, without rebooting? I will no longer need/want root privileges but just want to start the ubuntu studio desktop as normal

Control-D takes you in to the normal mode (GDM et. al)

---

