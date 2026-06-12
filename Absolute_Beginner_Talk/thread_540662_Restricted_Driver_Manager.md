---
title: "Restricted Driver Manager"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Sho Mitsuharu on 2007-09-01
I've been trying to find a solution to this problem all day, but I have yet to find one so I'm asking for help here.  I have an Inspiron 1520 which I recently installed Ubuntu 7.04 on.  I got everything pretty much working, except a few things.  Using Envy, I was able to get the correct resolution and what not, but then I tried using Compiz, and failed.  Since everything else was sort of working, I figured seeing "Your hardware does not need any restricted drivers" didn't mean anything when I tried opening the restricted drivers manager.  So after hours upon hours of searching for a solution, I am left him stumped.  Does anyone have a fix for this?  Thank you in advanced.

---

### Post by mikaelsnavy on 2007-09-01
What kind of graphics card do you have?

---

### Post by Sho Mitsuharu on 2007-09-01
Ah, sorry. My brain is a little fried right now with all this searching I'm doing.  I have an Nvidia 8600M GT.

---

### Post by SOULRiDER on 2007-09-01
Then you DO need restricted drivers. Im not 100% sure but i believe some cards formt he 8xxx family aren't supported..

EDIT: Didnt envy install the nvidia drivers?

---

### Post by Sho Mitsuharu on 2007-09-01
Envy did install the drivers, but the Restricted Driver Manager isn't recognizing my card still.  This is really frustrating.  I've seen some other people with the same configuration getting it to work, but it won't for meh.

Edit:
The Nvidia X Server Settings even state that it's using the driver version 100.14.11, which was installed by Envy.  What's up with the Restricted Driver Manager?

---

### Post by SOULRiDER on 2007-09-01
Forget about it, its a bit useless AFAIK. Try opening somehting that uses 3D, if it works then the problem with compiz is because your xorg is not 100% correctly configured.

---

### Post by Sho Mitsuharu on 2007-09-01
Hmm...I don't have anything 3D to use as I've only recently installed Feisty.  In my xorg.conf file, it list this:
```
Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection     "Display"
        Depth       1
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    ........

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```
It seems the computer is still not recognizing I have a 8600M GT, or is it just because of the lack of support for the card currently?

---

### Post by SOULRiDER on 2007-09-01
Yes, 3D is working. Im not sure what are the things you have to edit in xorg to get compiz running, but for that you should check the Howto section. I think there are some nvidia commands that will configure it for you though. Open a terminala nd type nvidia and then press tab twice to see all options, i think one of them is called nvidia-glx-enable. I believe that will configure xorg for you so you can use compiz.

Good luck!

---

### Post by Sho Mitsuharu on 2007-09-01
Opening the terminal and typing nvidia just tells me "Command not found."  I have tried Armagetron and it works, but that may not be a good 3D benchmark. xD  Thank you for your help, I really appreciate it.

Edit: nvidia-glx-enable outputs "No manual entry for nvidia-glx-enable"

---

### Post by FuturePilot on 2007-09-01
Post the output of this
```
glxinfo | grep OpenGL
```

---

### Post by Sho Mitsuharu on 2007-09-01
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8600M GT/PCI/SSE2
OpenGL version string: 2.1.1 NVIDIA 100.14.11
OpenGL extensions:

This is so confusing. T_T

---

### Post by FuturePilot on 2007-09-01
Your 3D is working.
The restricted driver manager won't pick this up though. I don't think....
Add these to your Device section. Then log out and restart X (Ctrl+Alt+Backspace) for the changes to take effect. It might make Compiz work


```
 Option          "AddARGBVisuals"        "True"
 Option          "AddARGBGLXVisuals"     "True"
```

---

### Post by Sho Mitsuharu on 2007-09-01
Ah ok.  I guess I'll redo the Compiz stuff.

Edit:
Ok, will do.  Here goes nothing. :)

Edit 2:
D:  Nope, still the same problem.  The window borders disappear.

---

### Post by Sho Mitsuharu on 2007-09-01
Bump.  Is there anyone who's had this problem and has solved it?

---

### Post by SOULRiDER on 2007-09-02
Make sure the Window Decoration plugin is loaded... (i know it sounds stupid but i was killing myself because it wouldnt work and the problem was that the plugin wasnt selected)

---

