---
title: "mouse scroll wheel doesn't work"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by ilikecoffee on 2007-11-27
Seems like an uphill battle. Does anyone have a solution for the scroll wheel not working? I'm using a generic BTC mouse with PS/2 input.

Before you all refer to this:
[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

I tried it and guess what? when I try to launch "/etc/X11/xorg.conf or /etc/X11/XF86Config-4" in terminal, I get: "command not found"

When I launch text editor to change the xorg file, it won't let me save it!

Does anyone know what's going on? Either how do I get my scroll wheel to work, or why can't I save changes to my xorg file?

---

### Post by linuxlizard on 2007-11-27
You have to be in root to save that file- it protects regular users from messing up their system.

Launch the command for your text editor from the terminal with sudo in front of it:

 sudo gedit /etc/X11/xorg.conf

make your changes and now it will save.

---

### Post by nhandler on 2007-11-27
> **linuxlizard said:**
> You have to be in root to save that file- it protects regular users from messing up their system.

Launch the command for your text editor from the terminal with sudo in front of it:

 sudo gedit /etc/X11/xorg.conf

make your changes and now it will save.

If you are using a graphics based text editor, you should use gksudo instead of sudo.

---

### Post by linuxlizard on 2007-11-28
> If you are using a graphics based text editor, you should use gksudo instead of sudo.

Just wondering why? I've never used gksudo before and never had a problem. I just ran both side by side and don't see any difference visually?... What's the reason?

---

