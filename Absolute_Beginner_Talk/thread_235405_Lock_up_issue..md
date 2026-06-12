---
title: "Lock up issue."
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by Scintillement on 2006-08-13
At times my machine will *lock up* on me. The odd thing is that when it does this I can still move the mouse and the cursor will move on screen. Once when it happened the music I had playing in workspace 2 continued to play. The keyboard doesn't seem to do anything though.

I am unable to click on anything when this happens and am forced to hold down my power button to restart my laptop.

I don't know how to word this next part but I'll try my best.

When this lock up occurs is there anything I can do short of holding in the power button? I mean if the mouse still moves then it must be noticing something. Maybe only part of it *breaks* when this happens? It just happened to me about 5 minutes ago if that helps at all. I don't know what to do really.

I'm sorry I couldn't word this better, I'm no good at describing things.

---

### Post by junglepeanut on 2006-08-13
I get this occasionally when playing music that used to be on my windows partition.

Most times it can be fixed for me by ctrl+alt+backspace, but it may take a few minutes for my computer to even respond to the command, so I just poweroff now. Or sometimes right when it would happen I could kill the process, but this too took like five minutes for it to recognize.

---

### Post by Scintillement on 2006-08-13
It happens to me without music as well.

Ummm this may sound silly but what does ctrl+Alt+Backspace do? I pressed them and got a black screen so I think I either pressed them again or hit Ctrl+Alt+F7 I don't remember. Next thing I know it's asking me to log in again, Ubuntu that is. I did that without a lock up. So um what does Ctrl+Alt+Backspace do?

---

### Post by petri on 2006-08-13
Ctrl+Alt+Backspace kills your X, the GUI and when you waite a little you come back to the graphical login and can start your session again. 

Allthough nothing was saved so if you were working with Writer for example so the last chances are lost.

I had these lockups with Breezy and that was because of my ATI, what is yours video card?

---

### Post by erik677 on 2006-08-13
> **petri said:**
> Ctrl+Alt+Backspace kills your X, the GUI and when you waite a little you come back to the graphical login and can start your session again. 

Allthough nothing was saved so if you were working with Writer for example so the last chances are lost.

I had these lockups with Breezy and that was because of my ATI, what is yours video card?

I have been having the same problem, locking up randomly.  Sometimes my laptop runs fine for hours, other times it locks up after a couple of minutes.  I havent yet been able to succesfully load ATi drivers for my card (mobility IGP 320) so I think that is the cause of my problem, but strangely it only happens in Gnome, and never happens at all if I use KDE.  I suppose the solution would be to use KDE, but I really wanted to learn to use both desktops.

---

### Post by petri on 2006-08-13
KDE is a little bit more userfriendly than Gnome. Don't get me wrong, Gonme is userfriendly too, it just chooses it's friends more carefully :mrgreen:   

Have you searched howto to your ATI-drivers?

---

### Post by MaximB on 2006-08-13
OK guys...listen up !
I had the same problem 
no ctrl+alt+backspace help
no alt+ctrl+F2 help either

you MUST install your video card PROPERLY !!!
we have lots of guids and "how to..." in this forum
just search for them.

---

### Post by John Q (be) on 2006-08-13
> **MAXDDARK said:**
> OK guys...listen up !
you MUST install your video card PROPERLY !!!


sometimes it can be as easy as changing the "vesa" word into "sis"
search for the graph conf file on you PC/laptop

for my laptop the configuration was default vesa and playing movies was a slideshow. after editing the graf conf file into sis (WITH checking if the correct driver is present!!! wich was the case 4 me)

John

---

### Post by petri on 2006-08-13
Yes, and the easiest way to do this is to type sudo dpkg-reconfigure xserver-xorg in terminal and follow the instructions.

Though I would first search the forum to howtos to your videocard... :rolleyes:

---

### Post by gustl87 on 2006-08-16
hello

i am using an ati m6 - and i got the same strange freezes.

but then i found this on the web^^:

[http://forums.gentoo.org/viewtopic-p-3237995.html](http://forums.gentoo.org/viewtopic-p-3237995.html)

and it worked after some modifications.
so it never freezed again (till now).

so you should use the driver called "ati" and if freezing continues, you might edit it as follows:

```
Section "Device"
        Identifier      "[PUT YOUR CURRENT CARD NAME HERE]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        #Option          "AGPMode" "4"
        #Option          "AGPSize" "16" # default: 8
        Option          "AGPFastWrite" "false" # MUST BE FALSE!!!
        Option          "SWcursor" "true" # MUST BE TRUE!!!
        #Option          "RingSize" "4"
        #Option          "BufferSize" "2"
        Option          "EnablePageFlip" "false" # necessary?
        Option          "EnableDepthMoves" "false" # MUST BE FALSE!!!
        #Option          "RenderAccel" "false"
        #Option          "AccelMethod" "XAA" # or XAA, EXA
        #Option          "DDCMode"
        #Option          "SubPixelOrder" "NONE"
        Option          "ColorTiling" "false" # MUST BE FALSE???
        #Option          "DynamicClocks" "true"
        #Option          "bioshotkeys"   "True"
        #Option          "XAANoOffscreenPixmaps" "true"
EndSection

```

#sorry for my bad english.

---

