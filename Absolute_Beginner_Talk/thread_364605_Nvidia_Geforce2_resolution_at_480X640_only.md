---
title: "Nvidia Geforce2 resolution at 480X640 only"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by yhal on 2007-02-18
Need to make this short and to the point, but I'm in the struggling stage. My Nvidia Geforce2 Vidio card had a resolution of 408X640 resolution only.  I tried all the things I could find here, but of course always not knowing for sure I was doing things right, especially as nothing worked.  I do have it working now, but only out of luck. In the terminal I typed sudo dpkg-reconfigure xserver-xorg, and  used auto configuration for the video card, and then could only get to the DOS type window when restarting.  This time I typed sudo dpkg-reconfigure xserver-xorg again, and at the memory allocation for the Video card I guessed 1000Kb, instead of leaving it blank. and now I have all the resolutions, and everything seems to be working right:-k 
. What is the correct number for the vidio card memory allocation, and maybe what else have I gotten totally wrong.

---

### Post by teaker1s on 2007-02-18
mb x 1024 = correct memory

---

### Post by yhal on 2007-02-18
Thank you, you guys are amazing to get a reply that quickly

---

### Post by teaker1s on 2007-02-18
if you don't require open gl the driver you want is "nv" you need to manually choose settings, for this you need monitor  specs for horizontal and vertical settings. You can manually select resolutions

---

