---
title: "1680x1050 resolution frustration"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by jchan2 on 2007-11-15
This is my first time using Ubuntu/Linux and for the past 6+ hours I've been trying to figure out how to set my screen resolution to 1680x1050. Overall, it's been pretty confusing and frustrating.

I'm currently using 7.04 Feisty Fawn with an NVidia Geforce 6800 LE graphics card. I looked through ubuntu forums how to set this resolution, and came across many fragmented threads on how to do it: modifying xconfig.org file (which I did, didn't work), downloaded latest patch for Linux ([link]("http://www.nvidia.com/object/linux_display_ia32_100.14.19.html")) and only to be confounded how to install it. I found this [link]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") from a thread, and then found this one [here]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html") which is supposed to work 100% of the time....But now I'm confused which instructions to follow. Yeah, you can probably see how overwhelmed I'm feeling now...and I still haven't found a solution to changing my resolution to 1680x1050.

So, I'd like to start fresh by creating this post to prevent anymore confusion for myself and maybe get some straight answers you guys. Please be patient, and remember you're talking to someone who's never used Linux before. 


1) First of all, do I even need to download the latest NVidia driver for Linux? I'm assuming the generic driver that came with 7.04 Feisty Fawn has a limitation of what resolution I can set.

2) If so, how do I install it *exactly*? Please be as detailed as possible.

3) What else do I need to do?

4) Is it required for me to re-edit the xconfig.org file?


Thanks for taking the time to read this.

---

### Post by kpkeerthi on 2007-11-15
Now I'm confused. Do you mean that you now have nvidia driver installed and got the resolution working?

---

### Post by jchan2 on 2007-11-15
Sorry, I forgot to mention that I haven't been able to install the latest graphics driver nor have I been able to set my resolution to 1680x1050.

---

### Post by kpkeerthi on 2007-11-15
This is the recommended way to install nvidia binary driver:
```

[Enabled Restricted Devices Manager]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nVidia_drivers_in_7.04").

```

In the terminal...
```

gksudo nvidia-settings

```

... and then change the resolution. If you are happy, press "Save to Xorg.conf" button. This should save your setting so it is restored next time you boot.

---

### Post by alienexplorers on 2007-11-15
Try running the ENVY script to load your driver.  Then open the terminal and run:
> gksudo nvidia-settings  This will allow you to select your resolution / refresh rate.

---

### Post by kpkeerthi on 2007-11-15
If you have envy installed. launch it and make sure you "Uninstall the nvidia driver" before you install it using the restricted device manager.

---

### Post by jchan2 on 2007-11-15
kpkeerthi, your suggestion worked.  OMG, I love you.

LOL, not in the wrong way, but thanks, it worked. I wonder why this suggestion wasn't found mentioned in the threads..... :confused:

---

### Post by kpkeerthi on 2007-11-15
Glad it worked for you.

---

### Post by jchan2 on 2007-11-15
just wondering, is there a way to access 'gksudo nvidia-settings' using the GUI instead of using the terminal? probably would be easier for people to change resolutions on their own...

---

### Post by NotTheMessiah on 2007-11-15
You can probably add it to the main menu...but it's a good question why isn't it in the menu in the first place?

---

### Post by alienexplorers on 2007-11-15
You can create a short cut on your desktop.  This way you just click on it, enter your password, and away you go.  This is how I run nvidia-settings on my system.

---

