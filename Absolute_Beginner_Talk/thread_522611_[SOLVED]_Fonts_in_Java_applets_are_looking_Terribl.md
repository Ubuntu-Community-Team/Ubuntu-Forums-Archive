---
title: "[SOLVED] Fonts in Java applets are looking Terrible"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Alex F. Chan on 2007-08-10
Hi, 

I've lurking in the forums for a while, looking for answers for my installation. Until now I've found almost all the solutions on this forum or from google. The problem that I have now is that when I open a Java application on Firefox, the fonts in some parts of the app cannot be read because they are small or look deformed. Everything other thing works fine. 

Have anyone encountered to a similar issue?

Thanks in advance for any help provided

Alex

---

### Post by apksr on 2007-08-29
Yes I have problems with the Oracle plugin, the fonts are barely readable.
I've tried changing font.properties in /usr/lib/j2se/1.4/jre/lib/ and fontconfig.properties in /etc/java-6-sun/ but nothing seems to work. Did you install sun-java6-fonts?

---

### Post by Alex F. Chan on 2007-08-30
Solved!
Yes, I installed sun-java6-fonts. And it didn't maka a difference. 
I found out that my dpi was set to 75 in 1024x768 resolution. I changed the dpi on the xorg.conf file. You should modify (or add in my case) the following line in the "Monitor" section:

*DisplaySize	270	203  *


This is for 96 dpi. More info [here]("http://ubuntuforums.org/showthread.php?t=20976")

---

### Post by apksr on 2007-09-06
Works great, thanks! That was really killing me.

> **Alex F. Chan said:**
> Solved!
Yes, I installed sun-java6-fonts. And it didn't maka a difference. 
I found out that my dpi was set to 75 in 1024x768 resolution. I changed the dpi on the xorg.conf file. You should modify (or add in my case) the following line in the "Monitor" section:

*DisplaySize	270	203  *


This is for 96 dpi. More info [here]("http://ubuntuforums.org/showthread.php?t=20976")

---

