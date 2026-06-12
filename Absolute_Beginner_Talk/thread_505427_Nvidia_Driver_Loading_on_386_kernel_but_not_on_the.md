---
title: "Nvidia Driver Loading on 386 kernel but not on the 686 kernel"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by toolazy2work on 2007-07-20
I recently upgraded to the 686 kernel for my intel p4, to see if there was a performance difference.  When Ubuntu 6.06 Dapper was loading, it gave me an error stating that the Nvidia driver was not loaded.  I was wondering how to load the Nvidia driver so that X would start.  Thx in advance.

---

### Post by SPQQKY on 2007-07-20
I just had this issue. Do you have Envy installed?

---

### Post by Seisen on 2007-07-20
The same way you installed it on the 386 kernel. Actually everytime your kernel gets upgraded you will most likely have to reinstall you video drivers.

---

### Post by toolazy2work on 2007-07-20
No, I do not have envy installed, and the first time i loaded ubuntu, it loaded X using a generic driver.  That is why I am kinda lost.  Do i have to do an apt-get to get the driver again?

---

### Post by toolazy2work on 2007-07-20
I just tried to restart and do a sudo dpkg-reconfigure xserver-xorg, and i went through the setup, and it still didnt load.  Just extra info for you guys, if you need anything else, let me know.  And thx for the replies.

---

### Post by Malta paul on 2007-07-20
Hi, As stated above you will have to install your Nvidia Drivers again. If I were you I would use Envy, it great.
here is the link: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
Have fun ;)

---

### Post by toolazy2work on 2007-07-20
ok, the installation for envy keeps closing on me for some reason, but oh well.  I tried to uninstall and reinstall the nvidia-glx package via apt-get, and that didnt work.  Do you think that if I run "sudo nvidia-glx-config enable", it will fix the problem?

---

### Post by Seisen on 2007-07-20
How did you install you nvidia driver before?

---

### Post by toolazy2work on 2007-07-20
I figured it out.  I thought that synaptic would automatically install the restricted modules.  I guess it didnt.  I installed them and now my box is up and running.  Thank you all for the help as it is much appreciated.

---

