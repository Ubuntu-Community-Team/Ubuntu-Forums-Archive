---
title: "1440 x 900 resolution monitor"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by frank26080115 on 2007-10-07
i have an Acer 5570 computer (with Intel GMA 950 (I have 915resolution installed and working)) and a new Dell SE198WFP monitor with a maximum resolution of 1440 x 900. Currently I can only select up to 1280 x 800 resolution. I have edited my xorg.conf to include the 1440 x 900 option but I can't select it in my settings.

---

### Post by Wiebelhaus on 2007-10-07
Applications -> Accessories -> Terminal

Code:

> sudo dpkg-reconfigure -phigh xserver-xorg


---

### Post by frank26080115 on 2007-10-07
I did that, I selected the first default option, then the next screen I went to 1440 x 900, pressed space bar so it had a star beside it to indicate that it was in fact selected. I pressed enter and the configuration ends. I reboot my computer, and I went back to 1024 x 768 and lost the 1280 x 800 option. Now I applied my backup xorg.conf file and went back to 1280x800

so your method above does not work

---

### Post by bodhi.zazen on 2007-10-07
See this link : [https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)

You need to manually configure 915 resolution, see these links :

[http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html](http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html)

[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

---

