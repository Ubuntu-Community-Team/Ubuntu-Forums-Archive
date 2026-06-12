---
title: "installing nvidia driver"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2006-08-15
hello, im trying to install the last nvidia driver for linux (downloaded from [www.nvidia.com)](www.nvidia.com)). ok, ive downloaded it (it has .run extension, ive heard this is a kinda .sfx on wind0z) and after that ive done in terminal the next command lines:
 cd mydir
 sh nvidiadriver.run
now, after extracting i get this error:

  ERROR: You appear to be running an X server; please exit X before installing.  For further
         details, please see the section INSTALLING THE NVIDIA DRIVER in the README available
         on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

does anyone knows why, and how do i solve this problem? thanx

---

### Post by Klaidas on 2006-08-15
Weel, you should exit the X server :) Boot you PC in recovery mode for that, or > sudo /etc/init.d/gdm stop
As for installing the driver in general, you could use [http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

---

### Post by Jagot on 2006-08-15
Is there any reason you're not using the nVidia drivers in the repositories?

---

### Post by the_nomad on 2006-08-15
sorry im new to linux and i dunno even whats that... but i'd be very tankful if you would tell me.

---

### Post by Klaidas on 2006-08-15
The driver or the resposity? :)

---

### Post by tseliot on 2006-08-15
> **the_nomad said:**
> sorry im new to linux and i dunno even whats that... but i'd be very tankful if you would tell me.

Follow Method 1 of this guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

### Post by the_nomad on 2006-08-15
thanx alot ppl! i successfully installed the driver... thanx again! :tongue:

---

