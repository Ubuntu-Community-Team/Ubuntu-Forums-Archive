---
title: "DNS servers list won't stick"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by Cherry Popper on 2006-07-02
Hello.

Is there a way to make the DNS servers list stick? I can set it up just fine but everytime I restart my settings are lost and I have to redo the whole thing again. I've already read the Ubuntu documentation [here](https://help.ubuntu.com/ubuntu/desktopguide/C/internet.html) but it didn't say anything about 'saving' DNS servers list.

Feel free to assume that I'm very stupid and needs to be told everything in detail. :neutral: 

[ATTACH]12065[/ATTACH]

---

### Post by Max Luebbe on 2006-07-02
Haven't had this problem.

Try up at the top where it says 'Location', and create a new one.
With this selected, change your settings and click ok.

After reboot, see if that location is still there and has the settings you selected.

---

### Post by MaximB on 2006-07-02
I've had the same problem
you need to make the "dns list" file to be read only - after you change it
for more info read my thread :
[http://www.ubuntuforums.org/showthread.php?t=197763](http://www.ubuntuforums.org/showthread.php?t=197763)
be sure to read zefram's replay...

---

### Post by Cherry Popper on 2006-07-02
Thanks for the replies. The 'read only' trick did it. :D

---

