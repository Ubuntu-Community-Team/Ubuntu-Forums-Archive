---
title: "How To Install Vga Driver in Ubuntu"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by sam1981 on 2007-05-29
I have a pc which has a on board video and now that i installed ubuntu on it there is only two resulotions are available 600x480 / 800x600 help required

---

### Post by pnix on 2007-05-29
backup your /etc/X11/xorg.conf then
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by riven0 on 2007-05-29
You're going to need to reconfigure the xserver. Go to terminal: Applications >> Accessories >> Terminal. Copy and paste this command: **sudo dpkg-reconfigure xserver-xorg**

Now, keep hitting enter until you get to the resolutions section. Choose the selections you want with the **space bar** and when everything is finished, restart the xserver with ctrl+alt+backspace.

Good luck.

---

### Post by Welskyy on 2008-01-10
I tried the the command u suggested and I got what you said but when i restart the xserver by pressing ctrl alt backspace, the monitor will no longer display the the lead indicator of the monitor will just keep on blinking...what cause this problem?

---

