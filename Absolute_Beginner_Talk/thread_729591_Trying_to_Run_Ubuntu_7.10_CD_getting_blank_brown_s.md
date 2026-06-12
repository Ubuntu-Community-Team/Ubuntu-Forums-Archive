---
title: "Trying to Run Ubuntu 7.10 CD getting blank brown screen!?"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by julyderek on 2008-03-20
Hi,

I have been using Windows on all my PC's at home and work till now.  I am fed up with the slow, buggy Windows Vista.

Was just trying to check out this Ubuntu CD ver 7.10 on my Lenovo Laptop which is running Win XP Prof SP 2.  When I boot from this CD - I get the options listed then after I select the "Run / Install" Option, I get the Ubuntu log with the progress bar....then nothing a blank brown screen.

My Laptop configuration is : Lenovo 3000 Series C100 with Intel Celron 1.50Hz processor with 256MB RAM.

Thanks in advance.

Regards,
Derek

---

### Post by kesman on 2008-03-20
There's an option in the boot menu with something like "other boot options" or something, that comes from f6 if I remember correct. It allows you to edit the boot parameters for the selected boot method. Select safe graphics mode, then press f6 and remove the words "quiet" and "splash" from the end of the line. Then press enter. Now you'll able to see what's going on during bootup. If you see error messages, please post them here.

---

### Post by julyderek on 2008-03-20
> **kesman said:**
> There's an option in the boot menu with something like "other boot options" or something, that comes from f6 if I remember correct. It allows you to edit the boot parameters for the selected boot method. Select safe graphics mode, then press f6 and remove the words "quiet" and "splash" from the end of the line. Then press enter. Now you'll able to see what's going on during bootup. If you see error messages, please post them here.

Thanks !

It gets stuck on this last entry

[ 5.172000] squashfs: version 3.2-UBUNTU (2007/07/26) Phillip Lougher

After 5 minutes or so..says running script....

Then a blank brown screen and some sounds...then nothing....

Can't see any error messages as the screen scrolls very fast....

Finally the desktop screen comes up !

I guess if I start it in safe graphics mode...it works !

But it is very slow...is it because I am running it of the CD?

Thanks again for your help...

---

### Post by kesman on 2008-03-20
Yeah it's slow because you are running from cd. After installing, it gets much faster.

---

