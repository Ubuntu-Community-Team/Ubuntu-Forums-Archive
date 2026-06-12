---
title: "Skipping packages when upgrading with apt-get"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by human39 on 2006-11-05
Hello Everybody, 

First time poster long time linux user but fairly new to Ubuntu and apt.

I run Ubuntu on my MythTV box.  When doing upgades on the box I want it to skip all the kernel related upgrades.  This are mostly because the lirc and ivtv modules that have been added to the kernel.  If I upgrade, they break.

However, the answer has not been clear on how to do this.  With yum, it is a simple addition to the configuration file.  

Could anybody shed some light on this?

Thanks!

---

### Post by bmathis on 2006-11-05
try using ```
sudo dselect
``` in a terminal, this should allow you to choose which software you want apt to update/install. I've never used it through so I'm not exactly sure how it works. :-?

EDIT: I also just found this website which has some good info on it. [http://ccrma.stanford.edu/planetccrma/man/man8/apt-get.8.html]("http://ccrma.stanford.edu/planetccrma/man/man8/apt-get.8.html")

---

### Post by bollix47 on 2006-11-05
You could also go into synaptic and search for your current kernel.  Then highlite your kernel, click on package and select Lock Version.

---

### Post by bmathis on 2006-11-05
That makes since too... I didn't think of that one

---

### Post by superm1 on 2006-11-07
Well a better bet if your upgrading, is to just make sure that the older kernel remains.  Usually the second kernel is installed in *addition* to the first one.

From within the newer kernel, ivtv and lirc modules can be built with module assistant per this guide:

Ivtv:
[https://wiki.ubuntu.com/Install_IVTV_Edgy](https://wiki.ubuntu.com/Install_IVTV_Edgy)


lirc:
[https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)

---

