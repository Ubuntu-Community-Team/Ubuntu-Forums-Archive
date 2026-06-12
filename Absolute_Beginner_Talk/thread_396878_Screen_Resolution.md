---
title: "Screen Resolution"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by familyjules74123 on 2007-03-30
Hey guys,

I was wondering if there was a way to get a screen resolution higher than 1024X768.  I enjoy having everything just a little bit smaller than the 1024x768 size.  It is not a serious problem, but I would like to know if its possible, and if it is, how would I go about doing it.

---

### Post by h0ax on 2007-03-30
Have you tried System -> Preferences -> Screen Resolution?

---

### Post by Bachstelze on 2007-03-30
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by alienexplorers on 2007-03-30
Have you tried adding 1280x1024 to your xorg.conf file.  Type: 

> sudo gedit /etc/X11/xorg.conf

add the new resolution as shown below.

> SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"

Save the file Hit ctrl+alt+backspace.  Login and check System>Preferences>Screen Resolution.

If the new resolution is not there please let us know.

---

### Post by CrucialTK on 2007-03-30
The last entry (the Xconf editting) worked perfect for me. Thanks!

---

### Post by familyjules74123 on 2007-03-30
HELP!!! I did the xorg edit and now my X wont load.  I cant login, and its a blue screen that says that there was a fatal error with xorg.  I looked at the error report it had and it said that the section I added to my xorg was not a good command.  How do i fix this???

---

### Post by familyjules74123 on 2007-03-30
bump

---

### Post by ed-j on 2007-03-30
Caution: Advice from a Novice!

Boot up or restart the machine. When you see the Grub loading, press [COLOR="SeaGreen"]esc[/COLOR].
This will give you the choice of a recovery mode. Chose the system you are using from the choices, press [COLOR="SeaGreen"]enter[/COLOR].

When it finishes doing it's own thing, type [COLOR="SeaGreen"]sudo dpkg-reconfigure xserver-xorg[/COLOR]. Enter your password and follow the on-screen instructions to configure your system.

When finished, type [COLOR="SeaGreen"]exit[/COLOR] and press[COLOR="SeaGreen"] enter[/COLOR].

All the best!  :-)

---

### Post by familyjules74123 on 2007-03-30
I fixed it, had to reconfigure my xserver-xorg

---

### Post by ed-j on 2007-03-31
Nice one!!  :)

---

