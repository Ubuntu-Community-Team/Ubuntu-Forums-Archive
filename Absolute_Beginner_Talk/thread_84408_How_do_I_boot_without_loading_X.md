---
title: "How do I boot without loading X?"
date: 2005-10-31
forum: Absolute Beginner Talk
---

### Post by Doc.Caliban on 2005-10-31
I need to do this so I can install nVidia drivers.  Supposedly, X Server should not be running at all when I do the driver install.

Thanks,

-Doc

---

### Post by goodmanbrown on 2005-10-31
After you boot to Gnome and log in, you can run:

```
sudo /etc/init.d/gdm stop
```

and then kill your X session with ctrl-alt-backspace.

That's the easiest way I know of.  I'm sure you could enter the grub boot menu and tell it to boot to a specific runlevel, but I don't know how to do that.

---

### Post by Doc.Caliban on 2005-10-31
[QUOTE=goodmanbrown]After you boot to Gnome and log in, you can run:

```
sudo /etc/init.d/gdm stop
```

and then kill your X session with ctrl-alt-backspace.

That's the easiest way I know of.  I'm sure you could enter the grub boot menu and tell it to boot to a specific runlevel, but I don't know how to do that.[/QUOTE]


Thank you.

nVidia suggested setting the default boot level to one that doesn't load X in case the new drivers cause a problem.  The range is 0-6 with 0 being a full stop, and 6 being a reboot.  The default in Ubuntu is 2, so I tried 1 and couldn't boot at all unless I did a failsafe boot.

I'll try it with your instructions and if there's a problem with the drivers I'll just use a failsafe boot to try to fix the problem.

-Doc

---

### Post by 23meg on 2005-10-31
Stopping gdm will work for Nvidia driver installation; you won't need to adjust default runlevels, so just revert that setting back to 2 (1 is single-user mode, 0 is a complete halt and 2-5 are various multiuser levels in most *nix variants). Hit ctrl+alt+f1 to go to a virtual terminal before issuing the gdm stop command if you have any trouble doing it from a normal terminal. You shouldn't need ctrl+alt+backspace.

---

