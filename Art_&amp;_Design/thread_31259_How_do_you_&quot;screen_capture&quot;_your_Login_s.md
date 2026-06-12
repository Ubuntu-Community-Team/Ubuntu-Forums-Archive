---
title: "How do you &quot;screen capture&quot; your Login screen?"
date: 2005-05-02
forum: Art &amp; Design
---

### Post by americanrockradio on 2005-05-02
I've put together a modified version of an existing GDM login screen and the only thing I'm missing before I make it available is a "screen capture" preview pic of the login screen itself.

How do you do this?

Thanks

---

### Post by Fab on 2005-05-02
[QUOTE=americanrockradio]I've put together a modified version of an existing GDM login screen and the only thing I'm missing before I make it available is a "screen capture" preview pic of the login screen itself.

How do you do this?

Thanks[/QUOTE]
 quick reply:
xnest

---

### Post by rototom on 2005-05-02
Use a digital camera!
;-)

---

### Post by benplaut on 2005-05-02
[QUOTE=Fab]quick reply:
xnest[/QUOTE]

xnest?  :?

---

### Post by Fab on 2005-05-03
[QUOTE=benplaut]xnest?  :?[/QUOTE]
 [http://www.xfree86.org/current/Xnest.1.html](http://www.xfree86.org/current/Xnest.1.html)

essentially, you can start an x server in your current x session, and therefore capture the window with the second X displaying gdm with the print button

---

### Post by americanrockradio on 2005-05-03
[QUOTE=rototom]Use a digital camera!
;-)[/QUOTE]
 Hahaha I liked this one =)

Xnest did the trick, thanks much!

---

### Post by Fab on 2005-05-03
[QUOTE=americanrockradio]Hahaha I liked this one =)

Xnest did the trick, thanks much![/QUOTE]
 no prob, glad it worked :9

---

### Post by dmontalvao on 2007-11-01
I must be really stupid. How does Xnest work? I already installed it.

---

### Post by crimesaucer on 2007-11-01
This is the easiest way I found to take a screenshot of your GDM: [http://ubuntuforums.org/showthread.php?t=2127](http://ubuntuforums.org/showthread.php?t=2127)

I use this command in Archlinux to take screenshots of my GDM... all though I do it in root tty2, and I don't use the "sudo" command like in the link I put above... so I'm going to explain it how I do it.

First install the package "Imagemagick", then I start my computer, and when I'm on my Login screen, I press "ctrl+alt+f2" to enter my tty2 or "virtual terminal #2"... then when in tty2, I type:

```
root
```

...and then enter the root password.


Next I use this command while I'm root in tty2:

```
chvt 7 ; sleep 5 ; XAUTHORITY=/var/lib/gdm/:0.Xauth DISPLAY=:0.0 import -window root gdm-screenshot.png; chvt 2
```

This will change the screen from tty2 (or vt2) to tty7 (or vt7)... then it will wait 5 seconds before taking a screenshot and putting it into your Root Folder... then it will change back to your tty2 (or vt2)...

Then type:

```
exit
```


... to log out of root privilege of tty2... then type "ctrl+alt+f7" to get back to your normal GDM login screen where you can now login like normal.


Now your last step is to run this in "alt+f2":

```
gksu nautilus
```

... now you should have your root nautilus folder open and you will see your "gdm-screenshot.png"... just change permissions to your username (right click properties, and select permissions)... then copy it to your home folder.


#########################################33

I also think there you might be able to use this command in tty2 without logging in to root:

```
chvt 7 ; sleep 5 ; XAUTHORITY=/var/lib/gdm/:0.Xauth DISPLAY=:0.0 sudo
import -window root gdm-screenshot.png; chvt 2
```

---

### Post by Crafty Kisses on 2007-11-01
> **Fab said:**
> [http://www.xfree86.org/current/Xnest.1.html](http://www.xfree86.org/current/Xnest.1.html)

essentially, you can start an x server in your current x session, and therefore capture the window with the second X displaying gdm with the print button

Exactly!

---

