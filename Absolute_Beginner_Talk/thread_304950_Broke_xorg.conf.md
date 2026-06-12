---
title: "Broke xorg.conf"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by Figgy on 2006-11-22
I was trying to modify my xorg.conf file by manually adding a busid to my graphics card section, but now my system won't take me to a boot screen. When I boot up, I see the little loading bar like normal, and after the bar finished it goes black and I hear the little ubuntu noise that happens when the login screen turns on. So since I can't log in, ( In my thinking ) I have to use the recovery mode to get to the root terminal, and I think I need to restore my backup of my xorg.conf file. So if my thinking is correct, how do I restore the xorg.conf file using my backup?

---

### Post by taurus on 2006-11-22
Boot into recovery mode from GRUB menu and at the prompt, edit /etc/X11/xorg.conf and remove whatever you modified before...

```
nano -w /etc/X11/xorg.conf
```

---

### Post by ReaderRat on 2006-11-22
> how do I restore the xorg.conf file using my backup?
```
sudo cp /etc/X11/?backup /etc/X11/xorg.conf
```

---

### Post by Figgy on 2006-11-23
Okay, for some reason now my system boots up. I hear the sounds of it coming to the login screen, but I only see a black screen.

---

### Post by Derek Tomes on 2006-11-23
Try booting using your Live CD and then copy the xorg.conf file from the CD to your computer.

---

### Post by MJN on 2006-11-23
Or try **sudo** [B]dpkg-reconfigure -phigh xserver-xorg

[/B]Mathew

---

