---
title: "Is low graphics mode different to vesa?"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by DrQuincy on 2007-10-22
The Gutsy upgrade broke my display.  When I boot it runs in low graphics mode at 800 x 600.  When I try to test any screen setup from System > Administration > Screens and Graphics - even with the vesa driver - I get a fuzzy screen.  Could it be even vesa is not working?  How do I debug this?

Thanks.

---

### Post by kellemes on 2007-10-22
What's your videocard?
/var/log/Xorg.0.log gives debuginfo..

---

### Post by DrQuincy on 2007-10-22
Hi.

Thanks, it's ATI X1300 Pro.  Before you ask I've tried reconfiguring xserver-xorg and the ATI closed source driver in the RDM just gives me a black screen when I restart.

---

### Post by Qwerty_ on 2007-10-22
I don't if this will help its for the X1400 though.

[http://ubuntuforums.org/showthread.php?t=584561](http://ubuntuforums.org/showthread.php?t=584561)

---

### Post by DrQuincy on 2007-10-22
Thank for the liink Qwerty but I am working from an upgrade from Feisty plus when I enable the ATI driver in the RDM I just get a black screen when I log in. :S

I've checked the log X is using xorg.cong.failsafe and that is making it use the vesa driver.  How can I find out why this might be and how can I fix it?  It X server parsing the xorg.conf and finding something that doesn't work right?

---

### Post by kellemes on 2007-10-22
I don't have this card but I know it can be like a bad horror movie to get cards going..
I've found a post from someone who actually succeeded.. It's post 94 on the following thread.. read on since the link poster has given seems to have changed.
[http://ubuntuforums.org/showthread.php?t=427852&highlight=ATI+X1400+resolution&page=10]("http://ubuntuforums.org/showthread.php?t=427852&highlight=ATI+X1400+resolution&page=10")

Good luck.

---

