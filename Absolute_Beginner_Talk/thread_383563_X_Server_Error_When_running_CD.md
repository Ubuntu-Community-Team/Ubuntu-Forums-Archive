---
title: "X Server Error When running CD"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by atownjoe on 2007-03-13
I am running an Intel Dell and my Video card is an ATI Radeon X600. When I boot from the Ubuntu 6.10 CD, it does the loading bar and then i get an error stating that the "X Server" could not be started. In a list that it spplies me with, I see that I have "No screens found" and "(EE) No Devices detected"

Also, i get errors about fonts missing such as /usr/share/X11/fonts/[misc, cyrillic, 100dpi, 75dpi, Type1]
'fonts.dir not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"

I've read things about changing the xorg.conf file (which I have no idea about), but I'm guessing I can't even get to the Ubuntu desktop to install anything.

---

### Post by overdrank on 2007-03-13
> **atownjoe said:**
> I am running an Intel Dell and my Video card is an ATI Radeon X600. When I boot from the Ubuntu 6.10 CD, it does the loading bar and then i get an error stating that the "X Server" could not be started. In a list that it spplies me with, I see that I have "No screens found" and "(EE) No Devices detected"

Also, i get errors about fonts missing such as /usr/share/X11/fonts/[misc, cyrillic, 100dpi, 75dpi, Type1]
'fonts.dir not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"

I've read things about changing the xorg.conf file (which I have no idea about), but I'm guessing I can't even get to the Ubuntu desktop to install anything.

Hi you should have a choice of safe graphics mode. If you use this one it should work. Good luck!

---

### Post by atownjoe on 2007-03-13
I've used the safe graphics mode, but to no avail. I do (sometimes) get to the prompt where it shows "ubuntu@ubuntu" and "sudo" and all that good stuff, which I don't understand.

---

### Post by highfructose327 on 2007-03-13
Hey I am having the same problem, I just found a post that may help, I hope so...

[http://ubuntuforums.org/showthread.php?t=190133]("http://ubuntuforums.org/showthread.php?t=190133")


good luck...

---

### Post by atownjoe on 2007-03-13
This seems to have done the trick. Thanks a lot. I guess I'm not as good at searching as I thought I was.

---

### Post by highfructose327 on 2007-03-13
Good deal it worked for me as well!

---

