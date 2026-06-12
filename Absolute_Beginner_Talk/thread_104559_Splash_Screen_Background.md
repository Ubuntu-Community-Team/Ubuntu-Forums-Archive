---
title: "Splash Screen Background"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by Micro Rotors on 2005-12-16
How does one go about changing the background for the splash screen, The brown just looks out of place when you change the splash screen to anything but the defalt.

---

### Post by Rackerz on 2005-12-16
[http://www.gnome-look.org](http://www.gnome-look.org) if your using Ubuntu
[http://www.kde-look.org](http://www.kde-look.org) if your using Kubuntu.

---

### Post by stuporglue on 2005-12-16
If you mean the color of the screen behind the splash screen, you'll need to edit /etc/X11/gdm/gdm.conf

There's a value called "BackgroundColor" in there you can change.

---

### Post by kaamos on 2005-12-16
[QUOTE=stuporglue]If you mean the color of the screen behind the splash screen, you'll need to edit /etc/X11/gdm/gdm.conf

There's a value called "BackgroundColor" in there you can change.[/QUOTE]

And a bit simpler way of doing this.. type "sudo gdmsetup" in a terminal and change the color for the GTK+ greeter.

---

### Post by Micro Rotors on 2005-12-16
[QUOTE=stuporglue]If you mean the color of the screen behind the splash screen, you'll need to edit /etc/X11/gdm/gdm.conf

There's a value called "BackgroundColor" in there you can change.[/QUOTE]

Thats the one,   Thanks Guys ;)

---

### Post by Micro Rotors on 2005-12-16
One more question........

Can one make this a picture to lay behind the splash screen instead of the BackgroundColor=#523921?

---

### Post by bscbrit on 2005-12-16
Yes, it looks as if you can select an image rather than just a colour using gdmsetup.  I haven't tried it but I cannot imagine what else it might do...

---

