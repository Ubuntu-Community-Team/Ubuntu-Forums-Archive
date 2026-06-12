---
title: "Help me understand the fglrx entries in Synaptic!"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by Cherry Popper on 2006-07-14
Here's my fglrxinfo -

```
zealot@zealot-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Platinum Edition Generic
OpenGL version string: 2.0.5879 (8.26.18)

zealot@zealot-desktop:~$

```

and here's a screenshot of Synaptic -

[ATTACH]12713[/ATTACH]

In the past I've botched video driver installs - that is, I follow a guide, copy+paste all the way but somehow I messed up and ended up with the Mesa stuff. Blah! So I'll go find another guide, install again until I got it right and today while poking around Synaptic, I find all these entries and have no idea what they're for.

Are these entries 'half-installed' drivers that are the result of my mistakes? If so, can I delete them? How can I tell exactly what should be left alone and what can be safely deleted?

Thanks :)

---

### Post by adam.tropics on 2006-07-14
You appear to have more than one kernel available, and each of those (in the screenshot) is the fglrx module for a specific kernel. If, as many do, you find the choice of kernel helpful, keep these. They are not huge, and present no problems for you.

---

### Post by MrHorus on 2006-07-14
```
uname -a
```

That will show you what version of the kernel you have and thus which version of the driver that you will be wanting to keep.

---

### Post by Cherry Popper on 2006-07-14
My uname -a shows -

```
zealot@zealot-desktop:~$ uname -a
Linux zealot-desktop 2.6.15-26-686 #1 SMP PREEMPT Fri Jul 7 19:48:22 UTC 2006 i686 GNU/Linux
zealot@zealot-desktop:~$

```

Also, I followed [this guide](http://ubuntuforums.org/showthread.php?t=85917) to install the new kernel, and I don't think I'll be needing the old 386 kernels anymore. 

So it would be okay for me to delete the old 386 kernels and fglrx-xx-xx-386 drivers correct?

---

