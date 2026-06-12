---
title: "What did the newer versions do to break the video?"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by -Ghost9- on 2007-07-20
Right now I have ubuntu 6.06 loaded on my system, because that's the only one that will work after install. I've tried both the later versions of ubuntu, but the video crashes each time. With 6.10, I managed to get it to work after going command line and dealing with the video driver repos, but it was a big pain and the functionality was limited. I tried 7.04, and after install, it went straight to a black screen and did nothing. 

I had to use the alternate install CDs for 7.04 and 6.10, but 6.06 works with the live CD. Yes I am using an ati card(x850xt). 

So my question is, what are they doing in these recent versions that decidedly doesn't like ATI? Are they ever going to get real ati support?

---

### Post by FleetAdmiral74 on 2007-07-20
Well ATi is still doing pretty shitty, so I don't see more support from their end.

And referring to your Feisty problem, when you boot up do you see the list of OS's you can boot into? If you choose the recovery mode, it puts you right into a root command line, and then maybe you can get it up and running until you can access the GUI drivers options and what not, like Envy. Well I suppose you don't even need the gui for Envy, you might want to check it out. I never have got it to work, but apparently it helps for a lot of people.

---

### Post by -Ghost9- on 2007-07-20
> **FleetAdmiral74 said:**
> Well ATi is still doing pretty shitty, so I don't see more support from their end.

And referring to your Feisty problem, when you boot up do you see the list of OS's you can boot into? If you choose the recovery mode, it puts you right into a root command line, and then maybe you can get it up and running until you can access the GUI drivers options and what not, like Envy. Well I suppose you don't even need the gui for Envy, you might want to check it out. I never have got it to work, but apparently it helps for a lot of people.

No list. I didn't dual boot, i just wiped the drive and installed ubuntu. It would show me the ubuntu loading screen and then the monitor would lose signal, say off mode in 5 seconds, and then shut off, but the computer was still running so it seemed to be just the video that went out.

---

### Post by Malta paul on 2007-07-20
+1 for Envy here is the link [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) It should install ATI drivers for you.  Another good reference is: [http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)
Good luck  :)

---

### Post by -Ghost9- on 2007-07-21
i tried envy to install the ati drivers. It does in fact install the drivers, but in turn seems to break all of the 3d functionality.

Right now I managed to get 7.04 installed and the desktop effects with the shadows, wobbles, and cube desktop are working. Now I tried installing the ati drivers and it broke it. I couldn't figure out what to do so I ended up reinstalling the OS as it seemed easier. But now that the desktop is working, no 3D apps seem to be working. I tried running 3d chess and got this message:

"Your system does not have the required software to enable 3D mode. Please contact your system administrator and ask them to install the OpenGL Python bindings and the GtkGLExt Python bindings."

is there something else to use besides envy? I figured since the desktop effects are working that maybe the drivers would work for 3d apps.

---

