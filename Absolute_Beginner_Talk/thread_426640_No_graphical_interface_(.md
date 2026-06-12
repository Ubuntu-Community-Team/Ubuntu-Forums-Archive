---
title: "No graphical interface :("
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by optional on 2007-04-28
I was upgrading my Ubuntu 6.10 to 7.04 but in the middle of it my computer froze.
When I restarted, it could only restart in text mode.

I tried what it says [here]("http://ubuntuforums.org/showthread.php?t=186196") but that won't work.

After the "Building package lists... Done, Reading state information... Done"  and all that I always just get

"0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded"


Anybody know what to do?

---

### Post by Tomosaur on 2007-04-28
You could try the old 'fix everything' trick (it seems like you already have the ubuntu-desktop package installed, which is why you get that output). In the terminal, type:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

If you get no errors, reboot and see what happens. If you get any errors, post them here and we'll see what's what.

---

### Post by optional on 2007-04-29
I did

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

and it worked.
Thank you very much.

---

