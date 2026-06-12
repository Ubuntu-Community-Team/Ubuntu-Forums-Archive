---
title: "Display Problems after Install"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by flaran on 2006-05-21
I installed everything from my CD and then when it finished installing the last of my packages it just showed a bunch of strange vertical and horizontal lines all across the screen.

Does anyone have any idea how to remedy this?
I'm on a HP zv6000 laptop with an AMD Athlon 64 processor.

---

### Post by Qrk on 2006-05-21
Most problems of this type can be fixed with 

```
sudo dpkg-reconfigure xserver-xorg
```

change the driver to "vesa" on the second screen of the the dialog box; after that you can look for a specific driver for your hardware.

---

### Post by confused57 on 2006-05-22
It may be a problem with the wrong driver for your video card.
You could try pressing Ctrl+Alt+F1 to get to a text command prompt, then enter what Qrk suggested.

If you have a Nvidia card you could also try "nv" or "vga",  if it's ATI, try "ati" or "radeon".

Then enter "startx"(without quotes) to restart the GUI.

If you're able to get to a command prompt with "Ctrl+Alt+F1, it may work better to enter:
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
```

when your finished setting up xorg, then:
```
sudo /etc/init.d/gdm start
```

---

### Post by flaran on 2006-05-23
Are there any alternatives to CTRL + ALT + F1?

---

