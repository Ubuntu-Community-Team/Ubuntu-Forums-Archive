---
title: "Whats does this mean??"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-07-22
I installed compiz and tried to run but I got this!

ryan@Ted:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
ryan@Ted:~$

---

### Post by GMachine_24 on 2007-07-22
i don't know but it sounds pretty serious.....


j/k.... i'm sure someone will know.

---

### Post by sad_iq on 2007-07-22
Do you have the video driver correctly installed??' Post the output from these commands: ```
glxinfo | grep direct && cat < /etc/X11/xorg.conf | grep Driver
```

---

### Post by LouisvilleLIP on 2007-07-22
I get that message when trying to run compiz without running an XGL session.  I think it's a common thing with ATI cards.

---

### Post by buffylette58 on 2007-07-22
getting the same thing ( [http://ubuntuforums.org/showthread.php?t=507301](http://ubuntuforums.org/showthread.php?t=507301) )

heres the output:
```


monica@monica:~$ glxinfo | grep direct && cat < /etc/X11/xorg.conf | grep DriverXlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
        Driver          "kbd"
        Driver          "mouse"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver  "fglrx"

```

---

### Post by alienexplorers on 2007-07-22
What type of graphics card are you running.  If it's an ATI or Nvidia you could try the envy script to get the drivers loaded correctly.
> [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by buffylette58 on 2007-07-22
I'm using Envy....
Sorry, I've taken over this thread lol, mine is here: [http://ubuntuforums.org/showthread.php?t=507301](http://ubuntuforums.org/showthread.php?t=507301)

---

