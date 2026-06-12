---
title: "Expanding the Desktop"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by Jeremy Owens-Boggs on 2006-03-02
I have Ubuntu installed on an older machine hine in my basement. Hooked to that machine is a really old crappy Monitor that maxes out at 800x600.  Since I have all my machines on a LAN, I have noticed that I am accessing the Ubuntu machine more and more via VNC on an upstairs machine with a much nicer monitor.  What I would like to do is to inclease the size of the screen when I am using VNC.  How does one make the screen bigger?  I have looked at system and preferences, and can't find where I can change the resolution displayed.  Also is there a way I can switch back and forth easily?  I would hate to have to log in using the attached monitor and not be able to for some reason?

---

### Post by TrendyDark on 2006-03-02
I've never used VNC before, but I'm guessing that it displays at the set size on the actual machine. To change your resolution goto System> Preferences> Screen Resolution

---

### Post by Jeremy Owens-Boggs on 2006-03-03
Selection options max out at 800x600.  Thinking I might actually know something, i zipped over to my xorg.conf file and added "1024x768" resolutions for color depths of 24, 16, 15, and 8.  Ctl-Bkspace later and still nada.  I don't need to do a full reboot do I?

---

### Post by IYY on 2006-03-03
Not a full one, but you'll need to kill the X server. Ctrl+Alt+Backspace.

---

### Post by TrendyDark on 2006-03-03
You shouldn't if you kill xorg, but reconfiguring xorg might not hurt. During that process you can choose more resolutions than 800x600.  

sudo dpkg-reconfigure xserver-xorg

^^reconfigures xorg

---

