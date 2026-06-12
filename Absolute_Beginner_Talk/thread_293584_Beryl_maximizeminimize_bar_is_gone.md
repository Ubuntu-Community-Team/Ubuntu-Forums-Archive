---
title: "Beryl maximize/minimize bar is gone"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by DraeLee on 2006-11-05
ok I couldnt find it exactly but if anyone can point me in the right direction that would be cool.  I had installed beryl a while back and everything has been working really well.  All of a sudden the top bar for my menus has disappeared.  I dont know what i did so i was wondering do i need to uninstall and reinstall it or is it just a bug that happens in edgy eft.  thx in advance to all replies

---

### Post by tronica on 2006-11-05
are you talking about the title bar of a window? make sure beryl manager is running.

---

### Post by DraeLee on 2006-11-05
yea its running now and yes its the top of the window where the maximize and minimize is gone

---

### Post by tronica on 2006-11-05
are you using Xgl? if so close beryl and stuff log out, then back in and try launching these 

> beryl-xgl

then 

> beryl-manager

---

### Post by spinflick on 2006-11-05
Similar thing happens to me, I dont loose the bar but I do loose the buttons after a while?

---

### Post by DraeLee on 2006-11-05
ok i did the >  beryl-xgl but everything went white and i had to reboot system so that didnt work either.

---

### Post by tronica on 2006-11-05
ok, I expected that but it was worth a try. are you using Xgl, personaly i think its easier to get aiglx working right.

---

### Post by tronica on 2006-11-05
oh also whats the output when you start beryl-manager from the terminal?

---

### Post by corstar on 2006-11-05
Add this to your "screen" section.

It worked for me.


Option         "AddARGBGLXVisuals" "True"

---

### Post by DraeLee on 2006-11-05
> **corstar said:**
> Add this to your "screen" section.

It worked for me.


Option         "AddARGBGLXVisuals" "True"
 

ill give it a shot bout to reboot now and see

---

### Post by DraeLee on 2006-11-05
hmm it worked.  thank you wonder what the issue was

---

### Post by tvlad on 2007-02-23
I have exactly the same problem, i don't have the minimize/maximize bar anymore. After i enable beryl, it just vanishes, and i believe i have all the option enabled in xorg.conf

I have beryl 2.0 beta2 with 96.xx nvidia drivers.

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Monitor        "AOC Spectrum"
    DefaultDepth    16
    Option         "TripleBuffer" "true"
    Option         "AddARGBGLXVisuals" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "RenderAccel" "True"
    SubSection     "Display"

Any ideas? because it's a nice to play with 3d effects, but i want to be able to move windows and such :)

thanks.

---

