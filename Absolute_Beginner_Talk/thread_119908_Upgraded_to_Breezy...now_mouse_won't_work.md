---
title: "Upgraded to Breezy...now mouse won't work"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by Edward The Bonobo on 2006-01-20
When I installed Hoary, my serial mouse wouldn't work. I followed the instructions in the wiki [https://wiki.ubuntu.com/SerialMouseHowto](https://wiki.ubuntu.com/SerialMouseHowto) to reconfigure xserver-xorg and select my mouse port. It worked fine.

I've just upgraded to Breezy. Same mouse problem...but the instructions don't work; it doesn't give you the option of selecting the mouse port.

I also tried to edit xorg.conf with gedit, but I got 'Cannot open display'.

Any ideas?

---

### Post by endersshadow on 2006-01-20
[QUOTE=Edward The Bonobo]When I installed Hoary, my serial mouse wouldn't work. I followed the instructions in the wiki [https://wiki.ubuntu.com/SerialMouseHowto](https://wiki.ubuntu.com/SerialMouseHowto) to reconfigure xserver-xorg and select my mouse port. It worked fine.

I've just upgraded to Breezy. Same mouse problem...but the instructions don't work; it doesn't give you the option of selecting the mouse port.

I also tried to edit xorg.conf with gedit, but I got 'Cannot open display'.

Any ideas?[/QUOTE]

[http://ubuntuforums.org/showpost.php?p=604061&postcount=6](http://ubuntuforums.org/showpost.php?p=604061&postcount=6)

Use those instructions.

Make sure that you use:

```
sudo gedit /etc/X11/xorg.conf
```

If you do not use sudo, you cannot edit xorg.conf!!!

---

