---
title: "Ubuntu 6.06LTS won't allow better than 1024x768 screen res"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by samadams on 2007-03-07
While I've had some major problems with Ubuntu thus far concerning getting online (and still not resolved)  I have a few annoying ones that I'd like to fix in the meantime.

My monitor (Gateway EV700) is capable of displaying resolutions above 1024x768.  Most notably the one I use when in XP. (1152x864)  It also has the ability for 1280x960 and 1280x1024.  But Ubuntu 6.06 (Dapper I believe), has 1024x768 as the maximum resolution I'm, allowed to set.  I can drop down to 800x600 but I'm not interested.  I want a higher resolution - how do I fix this?

p.s. - I still have no internet connection in Ubuntu so if I need to download anything and install it, please let me know how to find it in windows XP and how to install it once I copy it to my home directory.

Thanks in advance,
SamAdams

---

### Post by larrybrazos on 2007-03-07
You may have to edit the xorg.cong file to include all the resolutions supported by your monitor.

Backup Xorg.conf:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

Open xorg.conf:

sudo gedit /etc/X11/xorg.conf

FInd the section that list the modes for your monitor and include the resolutions you want.

This would be my guess.

---

### Post by Brandel Valico on 2007-03-07
Not positive it will work. But if you haven't all ready tried to. You may be able to add higher resolutions to x-org config using the command below to open and reconfigure it.

> sudo dpkg-reconfigure -phigh xserver-xorg


I don't believe you will need internet access to do so either. But hopefully someone with more experience then me can help you out.

---

### Post by samadams on 2007-03-07
Thanks, this did the trick!

---

### Post by samadams on 2007-03-07
Thanks, I tried the first option above and it worked.  So your solution might have as well too I'm not sure.

---

### Post by larrybrazos on 2007-03-07
Just curious, I am confused . . .

Did you . . .? 

1. manually edit your xorg.conf file or run 

or

2. sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by samadams on 2007-03-08
I manually edited the file.

---

### Post by larrybrazos on 2007-03-08
awesome! glad you got it working!

---

