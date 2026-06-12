---
title: "Magic SysRq key not activating"
date: 2008-03-17
forum: Arch and derivatives
---

### Post by kpkeerthi on 2008-03-17
I can't seem to get the magic SysRq key working in Arch. Alt + SysRq + R E I S U B is not rebooting instead launches whole lot of 'Save screenshot' dialogs. It worked fine in Ubuntu but not in Arch.

I'm running Arch in a Dell XPS M170 Laptop, GNOME + compiz enabled. I turned off Compiz and still no luck. I even tried Alt + Fn + SysRq + R E I S U B (as SysRq is linked with Fn). Any help is much appreciated.

---

### Post by ch_123 on 2008-03-17
> **kpkeerthi said:**
> I can't seem to get the magic SysRq key working in Arch. Alt + SysRq + R E I S U B is not rebooting instead launches whole lot of 'Save screenshot' dialogs. It worked fine in Ubuntu but not in Arch.

I'm running Arch in a Dell XPS M170 Laptop, GNOME + compiz enabled. I turned off Compiz and still no luck. I even tried Alt + Fn + SysRq + R E I S U B (as SysRq is linked with Fn). Any help is much appreciated.

The kernel needs to compiled with support for SysRQ, are you sure the kernel you're using supports it?

---

### Post by kpkeerthi on 2008-03-18
I'm using the stock kernel from the repository. You say it is not compiled with SysReq support?

---

### Post by drbob07 on 2008-03-18
```

echo 1 > /proc/sys/kernel/sysrq

```

Try that, and then *hold* Alt+PrtScrn while you're typing REISUB. (Remeber to give some time inbetween E, I, S, and U, as to not bork up your file system)

EDIT: Also, if your window manager is still running (and able to catch keys), it will be responding to the Print Screen key until you hit E, after hitting E you should either be at a black screen or TTY1.

---

### Post by kpkeerthi on 2008-03-19
> **drbob07 said:**
> ```

echo 1 > /proc/sys/kernel/sysrq

```

Thanks. I'll try that when I get back home today.

---

### Post by aeto on 2008-03-20
Your answer is in **/etc/sysctl.conf**

---

### Post by lariosa42 on 2008-11-09
I am having the same problem.  "Save Screenshot" windows come up faster than an army of flying monkeys.  I am running Ubuntu 8.10 (kernel 2.6.27) updated from Ubuntu 8.04, and don't even know how to rebuild the kernel, so my settings should be the default settings.  I am using a Dell Inspiron E1405 laptop with a slightly compact keyboard (blue Fn key instead of the keypad). I get:

```

$ cat /proc/sys/kernel/sysrq
1

```
and
```

$ grep MAGIC_SYSRQ /boot/config-$(uname -r)
CONFIG_MAGIC_SYSRQ=y

```
I also tried putting
```
kernel.sysrq = 1

```
into /etc/sysctl.conf and rebooting, but still no luck.  I have tried all kinds of combinations: Alt+Prnt Scrn, Fn+Alt+Prnt Scrn, Alt+Fn+Prnt Scrn, Fn+Prnt Scrn followed by either b or h (reboot or help) to test, I all I get is those darn screenshot windows.  Maybe I need to try the whole REISUB or RSEIUB sequence to see anything, but I'm worried that I will get too many windows and crash my system (oh, the irony).

Can anyone help?

---

