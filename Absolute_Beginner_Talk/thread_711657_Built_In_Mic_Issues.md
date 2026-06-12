---
title: "Built In Mic Issues"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by CommoAnimal on 2008-02-29
I have an Asus C90S Laptop and just installed Ubuntu 2 days ago, everything is working great except for my built in web cam and mic.  I dont really care about the webcam at this time, just want my mic working so i can use vent. Vent works fine for me, I can hear everyone else, i just cant use my mic, ive tried sound recorder and nothing there.

Codec: Realtek ALC883
Codec: Generic 1543 Si3054
 
thats what i got from the cat /proc/asound/card0/codec#* | grep Codec
command. 

anyone got a fix? thanks.

---

### Post by ramjet_1953 on 2008-02-29
Have you right clicked on the sound icon on the top toolbar and then opened the volume control?

If not, do it and click on edit>preferences
Make sure that Microphone and Microphone Capture are ticked.
Now click on the Switches Tab and select either Microphone Capture, or Mix. Whichever works for you.
Click on the Recording Tab and make sure that the sliders are at least three quarters up. Also, make sure that the buttons below the sliders do no have an X through them. Click to activate, if necessary.

Hope this helps,

Roger 8)

---

### Post by CommoAnimal on 2008-02-29
oh man i feel like such a nub, but im still learning this OS... THANKS!!! awesome, everything is now working, you rock!

---

