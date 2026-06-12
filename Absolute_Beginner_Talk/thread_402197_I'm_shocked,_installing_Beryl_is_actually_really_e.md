---
title: "I'm shocked, installing Beryl is actually really easy!"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Eduardo Serra on 2007-04-05
I'm new to ubuntu, and all i did was follow this simple instructions: [http://doc.gwos.org/index.php/BerylOnEdgy]("http://doc.gwos.org/index.php/BerylOnEdgy")

I'm using Edgy Eft, and i don't even have a Nvidia or anything, just my integrated intel chipset, 64 megs only, and this is as pretty as it gets. I'm just having one problem, when i play a video on VLC it wont show the image, but it will play the sound and stop, pause, forward and everything. What can it be? anyway, i didn't created this thread to ask you guys that, ill take care of that later, i just wanted to let you know how pleased i am to have my 3D cubic desktop installed so easily. ;)

---

### Post by Aurdal on 2007-04-05
Your video problem is likely caused by your video card not supporting the output module VLC is using.

To fix it, open up VLC and go to Settings > Preferences. On the Video tab, select the sub-tab Output Modules and then check the Advanced options checkbox in the bottom-right corner. 

Then select another output module. I don't know which are supported by your video card, but OpenGL is likely to be supported. If not I suggest X11 or XVideo. :)

---

### Post by Eduardo Serra on 2007-04-05
I'll try but i don't it's that, because i did watched videos before i installed beryl

---

### Post by TheMono on 2007-04-05
Then try setting the ouput module in VLC to X11 instead of XV, which is the most likely to cause problems. Do other players give an image?

---

### Post by Eduardo Serra on 2007-04-05
thanks, actually this did the job. Thanks you two guys!

---

