---
title: "Mac Pro - Resolution problem w/ Feisty"
date: 2007-04-20
forum: Apple Intel Users
---

### Post by evilempire on 2007-04-20
Really liking 7.04 so far on a work Mac. Great stuff so far! I Have run into one problem I haven't been able to fix yet.  


I installed the final 7.04 on a Mac Pro and can't choose any resolution above 1024x768. I added in the NVIDIA driver through the restricted drivers manager and restarted. That gave me more of the lower level resolutions - but still not the 1280x1024 native that my monitor supports. I know the NVIDIA driver installed successfully - because I can now use the desktop effects settings for wobbly windows and such.

Hardware as follows:

Mac Pro -
2x2GHz Core 2 CPUS
2 gigs ram 
NVIDIA 7300 Stock GPU
Dell 1907 FP monitor.


Any advice for enabling the native resolution?

Thanks in advance...

---

### Post by skwid on 2007-04-20
Have you added or checked the xorg.conf for the appropriate 1280x1024 lines ?

---

### Post by ronocdh on 2007-04-20
I think the **sudo dpkg-reconfigure xserver-xorg** command would be useful here. You can manually enable resolutions near the end of the walk-through.

---

### Post by evilempire on 2007-04-21
Thanks ronocdh - I will give that a try when I get into work on Monday. I work in IT - but am new to Linux.... I think I might build a cheap PC and make Ubuntu my main desktop at home for a month or so so I can learn the little details....

---

### Post by sjatkins on 2007-04-22
Just installed Fiesty 64 bit on Mac Pro.  On reboot when the screen normally shows login on orange background I instead get a flickering orange background with no dialog visible at all just flickering orange. This is on a stock Mac Pro with NVIDIA GeForce 7300 GT.  I choose the 1920x1200 resoultion for my Apple 23 inch monitor as per usual during installation.   This is not very happy making.   Back to Sabayon until I hear how to fix this.

---

### Post by tribaal on 2007-04-23
I have the exact same problem - anybody know of a fix?
I installed Ubuntu 7.04 64 bits with bootcamp. Install went fine, the only problem is this flickering orange login screen. Switch in text-mode (ctrl-alt-F1) brings up a messy command-line screen (unreadable).
I'll have to stick to Mac OS X on this machine until I find a fix for this.

What resolution did you guys select in the install's resolution chooser? I'm pretty sure this is related, but I don't know how to fix this?

Thanks a lot!

- trib'

---

### Post by tribaal on 2007-04-23
Hum, ok, so I finally managed to fix this flickering problem:

1. Use the desktop (live) CD, boot into "safe graphics mode".
2. Ubuntu boots and you get to the desktop (even thought the resolution is horrible - deal with it, we'll fix this later.
3. Install with the graphical installer from the live CD's desktop,
4. Reboot. The Desktop should come back, still with the bad screen resolution.
5. Install the Nvidia drivers for your mac's card. I installed Nvidia drivers from Nvidia's website, and it worked a treat (refer to the myriad of manuals you can find on theses forums for this if you don't feel confortable doing it).
6. Hopefully you should now have a Desktop linux installed on your mac pro with a correct screen resolution.

Then if you're not lucky like me you won't be able to make the sound work... but that's a known bug, so hopefully it'll be fixed soon.

Hope this helps.

- trib'

---

### Post by ronocdh on 2007-04-23
> **tribaal said:**
> Hum, ok, so I finally managed to fix this flickering problem:

1. Use the desktop (live) CD, boot into "safe graphics mode".
2. Ubuntu boots and you get to the desktop (even thought the resolution is horrible - deal with it, we'll fix this later.
3. Install with the graphical installer from the live CD's desktop,
4. Reboot. The Desktop should come back, still with the bad screen resolution.
5. Install the Nvidia drivers for your mac's card. I installed Nvidia drivers from Nvidia's website, and it worked a treat (refer to the myriad of manuals you can find on theses forums for this if you don't feel confortable doing it).
6. Hopefully you should now have a Desktop linux installed on your mac pro with a correct screen resolution.

Then if you're not lucky like me you won't be able to make the sound work... but that's a known bug, so hopefully it'll be fixed soon.

Hope this helps.

- trib'
Glad you got this resolved, but you should also take a look at this if you haven't already: [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

---

### Post by evilempire on 2007-04-24
> **ronocdh said:**
> I think the **sudo dpkg-reconfigure xserver-xorg** command would be useful here. You can manually enable resolutions near the end of the walk-through.


I just wanted to report back - this command worked for me . I was able to manually enable 1280x1024 on the Mac Pro (32 Bit edition of Ubuntu).

---

### Post by ronocdh on 2007-04-24
> **evilempire said:**
> I just wanted to report back - this command worked for me . I was able to manually enable 1280x1024 on the Mac Pro (32 Bit edition of Ubuntu).
Excellent! Congratulations and very good to have you here. I find it wonderful that you're, in your position, investigating the technological opportunities of this day and age.

Also, so you know, there's an AMD64 distribution of Ubuntu which would better take advantage of your hardware. I personally run it on my MacBook Pro (Core2 Duo), and I like the performance increase when I'm doing lots of things at once. The common FUD you'll hear about it is the lack of native 64-bit packages for things like Flash, etc., but this issues have largely been overcome by the community. 

There's even a 64-bit forum here; check it out. A gentleman by the name of Kilz should be able to hook you up with what you need via the scripts in his sig. In addition to that, there are many posts about getting JS and Flash up and running in 64-bit Firefox! (Instead of the somewhat easier fix of just running 32-bit Firefox with Flash and JS. That, on principle, is just undesirable!)

So, good luck, and keep us apprised of your experience with Ubuntu!

---

