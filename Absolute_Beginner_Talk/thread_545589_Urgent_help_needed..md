---
title: "Urgent help needed."
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by antisocialist on 2007-09-07
my windows dont work right
at the top of them it has everything except the bar that says:
<current process of window> - <what program it is> and has the minimize maximize and close buttons.
how do i get that bar back?

---

### Post by felicity on 2007-09-07
Maybe you turned desktop effects on? Try turning it off? Just a guess!

---

### Post by antisocialist on 2007-09-07
nope its off however i do have compiz which doesnt seem to be working (probably that)

---

### Post by Paul133 on 2007-09-07
Hmmm...your window manager is not working. Do you know what window manager you're using? Is it Emerald or Gtk Decorator?

---

### Post by felicity on 2007-09-07
You might need to add a line to your /etc/X11/xorg.conf file..

Maybe this in the Device section:
```
Option          "AddARGBGLXVisuals" "True"
```

or

```
Section "Extensions"
  Option "Composite" "Enable"
EndSection
```

at the end of the xorg.conf file

---

### Post by oldos2er on 2007-09-07
Using Gnome? If so, hit Alt-F2, and type metacity --replace in the window.

---

### Post by antisocialist on 2007-09-07
> **Paul133 said:**
> Hmmm...your window manager is not working. Do you know what window manager you're using? Is it Emerald or Gtk Decorator?

it ***was*** compiz but i just uninstalled it

---

### Post by Paul133 on 2007-09-07
Right. I meant to say window decorator. The window decorator is is a separate program from the window manager that draws the window borders. Usually, Emerald is the decorator used for Beryl and GTK Window Decorator is used with Compiz.

At any rate, now that you've uninstalled Compiz, your wm will be Metacity and you should have no problem. Hoepfully, you'll find a way to get Compiz to work. I'drecommend you try to install Compiz Fusion. Are you using ATI or nVidia graphics?

---

### Post by antisocialist on 2007-09-08
it was working just fine til i restarted after updating. i reinstalled it and its working again.
just cant remember how to set it as my default wm =p

---

