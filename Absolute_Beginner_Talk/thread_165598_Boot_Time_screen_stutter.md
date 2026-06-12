---
title: "Boot Time screen stutter"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-04-24
At boot up, the lines fly by.

At about:

Checking Dependencies
Loading Modules
Configuring Network Interface
Setting up general console font

Around those lines, the monitor practically drops dead. At the best of times with this there is a "stutter" or "jitter" like the monitor is about to turn itself off. At the worst of this the screen almost blanks and the relay clicks, real quickly. The raster collapses, almost.

This is the 2nd monitor to experience this. The first was to Dell issued 770s  that came with this Dell Dimension 4100 and now has a ViewSonic A75f. Both of these are great monitors and I seriously doubt the problem is with the monitor. I'm pretty sure Ubuntu is doing this, well, the linux kernel is.

I thought the problem was due to the system looking for ntp.ubuntulinux.com or some such, but I used the  sysv-rc-conf to look at the boot processes and removed the ntpdate from the list of boot-up processes. So it can't be that any longer.

Anybody else seeing this? Anybody else determined what is causing it?

---

### Post by htinn on 2006-04-24
Have you tried one of the vga=xxx options in the kernel line of the grub menu.list?

For example:

```
kernel		/boot/vmlinuz-2.6.15-21-k7 root=/dev/hdd1 ro quiet splash vga=791
```

vga=788 (800x600x24)
vga=791 (1024x768x24)
vga=794 (1280x1024x24)

---

### Post by Mark_in_Hollywood on 2006-04-25
[QUOTE=htinn]Have you tried one of the vga=xxx options in the kernel line of the grub menu.list?

For example:

```
kernel		/boot/vmlinuz-2.6.15-21-k7 root=/dev/hdd1 ro quiet splash vga=791
```

vga=788 (800x600x24)
vga=791 (1024x768x24)
vga=794 (1280x1024x24)[/QUOTE]

Working on it.

---

### Post by Mark_in_Hollywood on 2006-04-25
Using GRUB editing I set vga=791

only difference was the 1024 made the boot time lines smaller. Monitor still stuttered about the same place.

Folks, this isn't preventing Ubuntu/and all the applications from working, so don't sweat this one. Yet, it is an odd problem and I would like to know if I'm causing it, or if it's an OS glitch.

---

