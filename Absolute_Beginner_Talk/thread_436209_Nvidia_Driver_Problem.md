---
title: "Nvidia Driver Problem"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by Red Mystery on 2007-05-07
I just built a new pc with an Nvidia Geforce 7600 GT and I can't get the Nvidia accelerated graphics driver to install.  I currently can't connect to the internet with this new computer because I do not currently have the section of my house where my computer is located wired.  I have also tried to download the Nvidia driver for this video card but i could not get it to install on the new PC (yes, it was a lnux driver not a windows driver).  

Thanks for any help.

---

### Post by Bachstelze on 2007-05-07
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

---

### Post by Nythain on 2007-05-07
so the pc you are trying to install teh nvidia driver on isnt connected to the net right... i would personally try on another computer heading over to:
[http://packages.ubuntu.com](http://packages.ubuntu.com)
then selecting your version of ubuntu, dapper, edgy, feisty etc. and look for the nvidia-glx package, download it, and any dependencies listed for it... then burn the .deb's to a cd.
take them over to the ubuntu machine and in terminal type:
sudo dpkg -i /path/to/nvidia-glx.deb or whatever its called
(also make sure to install any of the depencies it might have had that you might or might not have downloaded first :))
hope that helps

---

