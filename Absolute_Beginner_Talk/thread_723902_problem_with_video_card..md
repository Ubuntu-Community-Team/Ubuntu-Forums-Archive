---
title: "problem with video card."
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by pankirk on 2008-03-14
I installed linux ubuntu 7.10. And everything was fine until I went to system>administration>screens and graphics. From here i clicked on the graphics card tab and changed it from "vesa" to my real graphichs card in the menu below it. And now it seems that each time I boot up my computer, linux starts in "low-graphics" mode... i am unsure what to do now. My card is an nvidia 8800gt 512mb and i would like to get the real drivers for it, but I dont know how to do that because the "restricted drivers" says that I dont need it... But obviously I DO need it because I dont have the right drivers. So, basically how can I get out of this "low-graphics" mode and get back to my 1680 x 1050 mode, and also how can I install my real gfx card drivers? Thanks!

---

### Post by Fred_E _krugar on 2008-03-14
Just go here and let Envy install the drivers for you:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by pankirk on 2008-03-14
Oh thanks! That worked for me :popcorn: but how can I make it so that it goes to 1680 x 1050? Right now the highest it will go to is 1400 x 1050.

---

### Post by Gepetto on 2008-03-14
gksudo nvidia-settings

---

### Post by pankirk on 2008-03-14
Thanks, but when I go to "gksudo nvidia-settings" there is no option for 1680x1050 only 1400x1050. Is there any way that I can make it go to 1680x1050?

---

