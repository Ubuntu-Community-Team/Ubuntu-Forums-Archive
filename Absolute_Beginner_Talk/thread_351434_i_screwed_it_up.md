---
title: "i screwed it up"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by davidseibert on 2007-02-01
I just installed dapper drake on parallels on my macbook, and I tried to change the xorg.conf file to include a resolution of 1680x1050, for my dellfpw monitor. I did this successfully when adding 1280x800 for my macbook built-in monitor, but after adding 1680x1050 to each of the "mode" lines, it now fails to boot and says "no display found". Crap!

Needless to say, I've never used linux before, and couldn't even get past getting it to look right on my monitor...any help would be appreciated.

---

### Post by pseudonym on 2007-02-01
Post back with the text of your xorg.conf file...

---

### Post by Scarlett on 2007-02-01
I recently got a new monitor, same resolution, and this worked for me:

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 31-101
VertRefresh 60-160
Modeline "1680x1050_75.00" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -HSync +Vsync
EndSection

As an interesting side note, it turned out that adding the refresh rate was imperative on my old CRT but the LCD seems quite happy now at a refresh rate of 60.00.  I had to reinstall Edgy and that was the default.  Since it was working I just left it alone.   So I don't think you really have to add that part if you don't want to.

---

