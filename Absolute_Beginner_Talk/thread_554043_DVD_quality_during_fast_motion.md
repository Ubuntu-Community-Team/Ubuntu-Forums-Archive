---
title: "DVD quality during fast motion"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by gubemton on 2007-09-18
Hi I have recently installed Ubuntu and the LinuxMCE package on top of Ubuntu. When I insert a DVD into the DVD drive and play it, the DVD plays fine during scenes where there isnt much motion. If the scene changes to something with a lot of motion, say a camera panning across a large field or something similar, I get some choppiness, and the panning isnt fluid like it should be. I believe that LinuxMCE uses Xine to play DVDs. I get this problem even when I play the DVD after copying it to the harddrive.

My hardware specs are as follows:
Asus M2NPV-VM
AMD Athlon 64 X2 5200+
Onboard graphics (Nvidia Geforce 6150)
2 GB DDR2 Corsair RAM


Thanks for your feedback!

---

### Post by jrasmussen0 on 2007-09-18
Do you get the same issue when running 'mplayer -vo xv dvd://'?  You might have to set the track number after dvd://.  Like dvd://5 for track 5.

What does 'glxinfo | grep render' give you?  I want to make sure that you are using the restricted nvidia video driver and use the 3D acceleration for the 2D output.

---

### Post by gubemton on 2007-09-18
> **jrasmussen0 said:**
> Do you get the same issue when running 'mplayer -vo xv dvd://'?  You might have to set the track number after dvd://.  Like dvd://5 for track 5.

What does 'glxinfo | grep render' give you?  I want to make sure that you are using the restricted nvidia video driver and use the 3D acceleration for the 2D output.

glxinfo | grep render gives me:
direct rendering: Yes
OpenGL renderer string: GeForce 6150/PCI/SSE2/3DNOW!
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,


When i play it in mplayer i still get the problem. Also, sometimes during fast motion it looks like the top half of the screen is shifted to teh left or right a few pixels and youget a line in the middle of the screen. This lasts for a fraction of a second and continues to happen whenever there is fast motion. I have never seen either of these problems when playing the DVD on a standalone DVD player.

Also it may help to know that I am connecting my computer to a 47 inch LCD HDTV using HDMI/DVI connection.

---

