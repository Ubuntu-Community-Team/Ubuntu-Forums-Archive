---
title: "[SOLVED] hwo to fix refresh rate and resolution"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by tjwoosta on 2008-01-11
i am new to ubuntu and i am having problems getting my resolution and refresh rate to the same place it was with windows. 
I am currently running ubuntu on a partitioned section of my drive with vista on the other. With  vista my screen resolution is 1280 x 800 and my refresh rate is 60 hz now with ubuntu i cannot select a resolution higher than 1024 x 768 and my refresh rate is only 30 hz, also i cannot select any visual effects. I have looked through the forums but i have not yet found a solution. If it helps i have mobile intel 965 Express Chipset Family that came with the computer. Please Help!

---

### Post by Pevichaey5 on 2008-01-11
System>>Administration>>Screens and Graphics

in here, choose your monitor type and you may have to play around with the resolution though 

hope that helps

---

### Post by tjwoosta on 2008-01-11
I went to screens and graphics and even here my best option is only 1024 x 768 at 30 hz. So i tried the graphics card tab and here i have two spots to choose a graphics driver the top was set to intel experamental mode setting driver for (and i cant see the rest) and the bottom was set to vesa driver generic. So i changed theese both to intel model 965 but after restarting my computer i could not get the gdm to start and i was at an all black screen. After this i restarted my computer and went to recovery mode. After The text stoped scrolling i typed  

 sudo dpg-reconfigure xserver-xorg
 after reconfiguring i typed 

 Sudo /etc/init.d/gdm start  

it started and now i am back at the destktop but i still cannot change the resolution or the refresh rate on my desktop despite the fact that i just reconfigured it all and in the reconfiguration screen i did choose my correct resolution and refresh rate.
I am now compleatly lost
the only reason i knew what code to type to reconfigure was from a post i had read this morning, It was plain luck that i got the gdm running again

Please if anyone can help me it would be greatly appreciated

---

