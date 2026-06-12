---
title: "Graphic browsing as root?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Quaxo76 on 2007-07-09
Hello,
I have Kubuntu 7.04, and I have the following problem: when I browse around the hard disk, if I want to delete some files owned by root, I'm denied access. Is there a way to delete them without using the terminal? Something like "right click -> Delete as root" or something like that? Or do I have to open a whole new instance of Konqueror as root?

Thanks
Cristian

---

### Post by Regel on 2007-07-09
Well, you could open terminal, type
```
kdesu konqueror
```
and then you have a konqueror session as root.

---

### Post by Nekiruhs on 2007-07-09
You will have to start a whole new instance of konqeror. The command is ```
kdesu konqueror
```

---

### Post by aysiu on 2007-07-09
Actually, if you have *konq-plugins* installed, I think there should be an **Edit as root** option in the right-click. I don't think there's a **Delete as root** option, though, so you may have to use Alt-F2 ```
kdesu konqueror
```

---

### Post by Quaxo76 on 2007-07-10
Hello,
Thanks for the replies! I have installed the konq-plugins and now I have the "Edit as root" option, but I can't get it to work - I tried editing Xorg.conf, but all I get is the "bouncing mouse pointer" for a few seconds, and in the taskbar I see "Edit as root" with the hourglass, but after a few seconds it quits.

Cristian

---

### Post by Outrunner on 2007-07-10
Yes, KDE has this 'little' problem... It's very annoying, but as far as I know, you'll have to live with it. Also, if you want to edit xorg.conf:

```
kdesu kate /etc/X11/xorg.conf
```

---

