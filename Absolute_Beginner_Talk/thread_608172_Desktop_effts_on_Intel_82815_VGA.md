---
title: "Desktop effts on Intel 82815 VGA"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Da King on 2007-11-09
Hi..wel i have been searching all this forum for a better answer to my problem about to to get my Intel 82815 graphic card to work on my Gusty 7.10. the ram is 32mb and it had 3D features with ma old windows XP....so how do i get compiz fusion to work on it.. i always get AIGLX present and XGL not present..what does that mean...pc freezez in the border too(seem to be a common prob) when i run the compiz-fusion. if i dont get compiz to work, is looking glass a great alternative to use? cos all the spec it needs goes with my vga.

---

### Post by Maestro23 on 2007-11-09
Check the Intel Hardware secton of the Compiz wiki, should help.

[http://wiki.compiz-fusion.org/Hardware/Intel](http://wiki.compiz-fusion.org/Hardware/Intel)

---

### Post by Da King on 2007-11-09
i had checked it earlier with the AIGLX option..its said ppl using feisty or above should the whole thing..i didnt know where to put the last two codes at
> Starting Compiz Fusion

Once you have completed the above step and restarted your X server (Either by logging out or rebooting), you can start compiz like this:

LIBGL_ALWAYS_INDIRECT=1 INTEL_BATCH=1 compiz --replace --indirect-rendering --sm-disable ccp &
 

It's a handful to type, so you might want to make an executable script which contains that command, or use one of the provided startup managers such as Compiz-Manager or Compiz Fusion Icon to handle adding all this for you.

You can also create an Autostart , so that Compiz Fusion will be launched when you log in...

or shod i just follow everything they said?

i still donno which option to take where AIGLX or XGL cos ma card says AIGLX present and XGL not present. 

i tried installing Xorg-server and i get this error from my synaptic manager
>           Depends: libglitz-glx1  but it is not installable
                      Depends: libglitz1 

---

