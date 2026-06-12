---
title: "[SOLVED] Kernel Update and ATI"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Stupojohn on 2007-06-25
Since upgrading to 2.6.20-16 from 2.6.20-15 my ATI driver doesn't show up in the Restricted Drivers Manager.  Instead, it simply says "Your hardware does not need any restricted drivers".

Also, 3D games seem to be running slower than before upgrading.  Does this mean I'm using the open-source driver?  Does the thread below have anything to do with my problem? 

[http://ubuntuforums.org/showthread.php?t=465337&highlight=kernel+update+ATI](http://ubuntuforums.org/showthread.php?t=465337&highlight=kernel+update+ATI)

Thanks in advance!

---

### Post by w4ett on 2007-06-25
Check your xorg.conf file...if the driver is ATI you are using the  open source xorg driver.

---

### Post by timberdc on 2007-06-25
Also, you might try Envy.
[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")
(I had the same problem)

---

### Post by Stupojohn on 2007-06-26
Yep, I was using the open source driver.  I didn't know you had to reinstall drivers when you updated your kernel.  I tried Envy and it worked perfectly.  Thanks!

---

### Post by dpar on 2007-06-26
If you don't use the drivers from the repo, they will probably have to be reinstalled for each kernel update.

---

