---
title: "Gnome won't automatically load"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by schlange on 2007-01-11
I've just leaped in to using Ubuntu 6.10 on my laptop, having had no
previous experience in Linux. I've been trying things out and somehow
have lost Gnome loading automatically when I boot.

I arrive at a text based login screen and after I type in my username
and password I can get to Gnome by typing startx.

But I would prefer to get back to having the graphical login screen
that I had previously.

I got a tip to try sudo dpkg-reconfigure gdm but when I did I got /usr/sbin/dpkg-reconfigure: gdm is broken or not fully installed 

Can anyone help me?

thanks
Richard

---

### Post by Jussi01 on 2007-01-11
I would try this:
```

sudo apt-get install gnome --reinstall
```

Hope it works.

Let us know how you go.

---

### Post by miceagol on 2007-01-17
> **Jussi01 said:**
> I would try this:
```

sudo apt-get install gnome --reinstall
```

Hope it works.

Let us know how you go.

Thanks a lot, Jussi01. I had the exact same problem, and doing what you suggested solved it. Another problem of mine, non-existing shutdown and reboot button, was also fixed after doing this. :D

---

### Post by Jussi01 on 2007-01-19
No probs.!! glad I could help.

---

### Post by ComplexNumber on 2007-01-19
the reason could have been caused by either uninstalling GDM or altering a setting(probably /etc/X11/default-display-manager) so that the system doesn't know which login manager to use, so it defaults to xdm.

---

