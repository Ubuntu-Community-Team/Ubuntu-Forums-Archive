---
title: "nVidia Board/Graphics Drivers"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by sirgogo on 2007-09-29
Hello all:

I'm a bit new at ubuntu forums, so I wasn't sure where to post this (but I think this is the right place).

Heres my problem: I have a nVidia nForce 4 series GeForce 6100 / n405. Everything was working smoothly since my fresh Ubuntu install about 3 weeks ago. Ubuntu recognized my nVidia on board card and installed generic "nvidia" drivers. Seeking to get my computer to a "gaming" stage, I decided to install the new nVidia drivers for my card. When I did so I, by accident, installed the GeForce 6100 PCIE drivers (not the GeForce 6100 / n405). As a result, the "X" was corrupted and was not able to start. After several hours of forum searching on my other computer, I was able to uninstall the nVidia drivers and install select generic "nv" drivers that allowed me to start the "X" and have a graphical interface (finally!).
However: my *old* nVidia drivers (that came with Ubuntu) were replaced by the new (wrong) ones I downloaded. I looked on the nvidia site and found that my system is not yet supported (motherboard).

My Dilemma: I am stuck with "nv" drivers that do not support open gl, or any other graphical effects (including screen saver) and do not know where to find the *original* drivers that came with Ubuntu or, better yet, drivers for my specific motherboard.

Any ideas as to where to find them?

Also, is the nVidia "Linux AMD6/EM64T" drivers compatible with my system? Because I couldn't find any info (or I just plain suck at looking for things) on the website.

Thanks a lot.

(Running 7.04 Feisty Fawn)

---

### Post by mridkash on 2007-09-30
Try using ubuntu restricted drivers manager, in my case it automatically uninstalled the wrong version and installed the correct.version.

system>administration>restricted drivers manager

---

### Post by sirgogo on 2007-09-30
Hey, thanks for the post.

Unfortunately when I do that it reports back with an error saying "Your hardware does not need any restricted drivers." I think this is because I am using a "nv" driver rather than a nvidia driver. Is there any other way to obtain a suitable driver?

Thanks again.

---

