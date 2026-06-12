---
title: "X server update issue"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by iamthez on 2007-07-05
Righty, so I installed Ubuntu 6.10 on a friends computer. Feisty won't work for some reason or other. When installing, Ubuntu automatically detects the right resolution and everything, which is cool, but there's a problem:

The automatic update system wants to install a new version of the X server. I know from previous experience (don't ask) that this will rewrite my xorg.conf file and lose my resolution (1280x1024).

One possible solution is to make a backup of xorg.conf, and replace it after the upgrade is done. Would this work? Or is there something else that I don't know about?

---

### Post by taurus on 2007-07-05
If you installed a driver for the graphic card, you need to reinstall it again after you upgrade X.  I think that is probably where the problem is.  Otherwise, reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by iamthez on 2007-07-05
meh, problem there is, every time i mess with that, i manage to crash the x server or something. rather not do that... again.

---

### Post by Raineer on 2007-07-05
Backup your xorg.conf before you do it (it should backup for you, but do it anyays so you know which file to use for 100% sure)

That's still very likely what you need to do.  Crashing (and recovering from crashing) X is a rite of passage for Linux users :)

---

### Post by taurus on 2007-07-05
Did you install any driver for the graphic card?

---

### Post by iamthez on 2007-07-05
> **taurus said:**
> Did you install any driver for the graphic card?


nope, no drivers... doesn't seem to need them.

---

### Post by taurus on 2007-07-05
What graphic card do you have and which driver do you use for it?  Post your /etc/X11/xorg.conf here if you are not sure how to read it.

```
cat /etc/X11/xorg.conf
lspci | grep VGA
```

---

