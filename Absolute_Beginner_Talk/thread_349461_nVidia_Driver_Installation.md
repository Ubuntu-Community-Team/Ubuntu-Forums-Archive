---
title: "nVidia Driver Installation"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by edwardLS on 2007-01-30
With my PNY GeForce 6200 adapter and the ViewSonic VX2235wm Monitor I have been for a few weeks attempting to get the nvidia driver installed.  I have had spotty success based upon my belief that seeing the 'nvidia splash screen' just prior to login indicated successful installation, and not seeing it indicated something was not right.  
To ensure each attempt was not corrupted by the previous attempt, I have made each attempt on a fresh install from my CD which I made from a downloaded ISO image, and the CD passed muster on media check.  In this period of time I have attempted various methods of installing the nvidia drivers.  I have used the Synaptic search/find/install method, I have used the 'envy' method, I have used Method 1 from [http://albertomilone.com/latest_nvidia_udsf.html](http://albertomilone.com/latest_nvidia_udsf.html), and I have attempted to install the 'Bleeding Edge Drivers using [http://albertomilone.com/instructions.html](http://albertomilone.com/instructions.html) as a guide.  I have attempted each of these methods more than once, and in all those attempts I have seen the nVidia Splash Screen only two time.  In each of those times, the subsequent reboot put me back to having no splash screen, and the display being incorrect in resolution and positioning on the monitor.
Nearing the end of my patience last evening I installed Ubuntu from CD, enabled the universe and multiverse repositories, and ignored the indication that software updates were available.  I then followed the guide [http://albertomilone.com/latest_nvidia_udsf.html](http://albertomilone.com/latest_nvidia_udsf.html) Method 1 carefully and watched carefully for error messages.  Very near the end of the procedure I seen a message on the monitor indicating that the 'splash screen' could not be found; however, I now have ??what I believe?? to be the nvidia driver installed based upon the fact that the resolution is set correctly and the positioning of the display is correct on the monitor.  Each reboot brings me back to a correct resolution and position, but I do not see the nvidia splash screen. 
Questions:
1. Is not the splash screen packed into the nvidia-glx package?
2. What is the name of the splash screen and where is it stored?
3. When I now do the software updates that I ignored, will I lose my correct resolution and position?
Any and all comments, suggestions are welcome which may help with resolution of this issue.

My apologies for such a lengthly post.

---

### Post by arochester on 2007-01-30
I have used Envy as well. The Nvidia splash screen does not show. It can be switched off. To findout if you have acceleration input into Konsole Teminal Program> glxinfo | grep direct
If it says yes, it's working. A more graphic way is to input> glxgears

---

### Post by edwardLS on 2007-01-31
Thanks 'arochester', that helped me out a lot.  Armed with this information I was able to install the very latest nVidia driver last evening, configure it, and test it with your suggestions.   With the display now working properly I can move on to learning more in my quest to avoid "Vista".  Thanks again.

---

