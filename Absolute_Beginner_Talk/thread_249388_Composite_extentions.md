---
title: "Composite extentions"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by HdK on 2006-09-02
A tutorial that I was reading said I need to enabke these extentions

it says I need to add the following lines to /etc/X11/xorg.cof:

 Section 'Extentions"
   Option "Composite" "Enable"
   Option "Render" "Enable"
 End Section

How exactly do I do this, step by step


The second thing I must do is turn on some options for my nvidia driver

The tutorial says  My "Device" Section looks like this


 Section "Device"

    Identifier "Nivdia GE Force 7300"
    Driver "Nvidia"
    Option "AllowGlxWithComposite""1"
    Option "RenderAccel" "true"
 End Section

How do I do this second step aswell?

---

### Post by bodhi.zazen on 2006-09-02
You are talking about editing /etc/X11/xorg.conf.

first BACK Up -> sudo cp /etc/x11.xorg.conf /etc/X11/xorg.conf.bak.

> Section "Extentions"
Option "Composite" "Enable"
Option "Render" "Enable"
End Section is it's own "section" in xorg.conf

after the device section:

Like this:
```

Section "Device"
Identifier "Nivdia GE Force 7300"
Driver "Nvidia"
Option "AllowGlxWithComposite""1"
Option "RenderAccel" "true"
End Section

Section "Extentions"
Option "Composite" "Enable"
Option "Render" "Enable"
End Section
```

Use editor of choice, ? nano
In a terminal:
```
sudo nano /etc/x11/xorg.conf
```
Ctrl-X to exit, answer "Y" to save file after edit.

You can cut and paste to nano (select text with mouse, move cursor into nano in desired location, push middle button).

Note: comment out (# at start of line) your current "device" "Nvidia" section.

Be prepared to crash X.

After you make the changes, re-start X
Ctrl-Alt-Backspace -> this will take you to GDM (log-in screen).

If you crash X -> Ctrl-alt-F1 to tty1.
Log in
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
sudo gdm
```

---

### Post by HdK on 2006-09-02
Ok I got that working thank you , but now when I try to cuztomize transparent windows I get a composite manger error 

pleease see [http://www.ubuntuforums.org/showthread.php?t=249355](http://www.ubuntuforums.org/showthread.php?t=249355) for the error msg I am getting

---

### Post by HdK on 2006-09-02
Some1 please help

---

