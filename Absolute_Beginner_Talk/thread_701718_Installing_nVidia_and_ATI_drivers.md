---
title: "Installing nVidia and ATI drivers"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by elchico04 on 2008-02-19
Okay so here is my situation. I am transitioning from XP cause its not stable at all and on XP I had a 3 monitor setup with 2 graphics cards.

I downloaded the nVidia drivers from their site and tried to install them but the installer gave me an error saying that it couldn't find the root for the "kernel-source". I have no idea what that is.

I'm so confused. I don't even know if I should be installing that driver.


also my main monitor's native resoultion is 1360x768. In installing the driver the right move to being able to use that resolution as well?

---

### Post by markitect on 2008-02-19
If your on the current version look for the restricted drivers, enabling them should give you a fairly recent nvidia driver.

Otherwise make sure you have 'build-essential' installed, this should get you to a point you can do any required driver building.
sudo apt-get install build-essential

also to get your odd resolution you may have to add an entry in xorg.conf  search around for some good example files.

---

### Post by elchico04 on 2008-02-19
where do I find these restricted drivers?

I installed the build-essentials package.

i also installed linux-headers-2.6.15-23-amd64-generic

i ran the installer with that in the command line to use it as my kernel source. Am I correct in doing that? When I tried installing again I got farther and I saw a progress bar but I got to an error before it could finish.

ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s).

am I using the wrong kernel source? What went wrong?

---

### Post by markitect on 2008-02-19
type in `uname -a` and make sure the headers you download match the version your using.

to make sure the configuration is right:
Copy the currently used configuration from /boot/config-2.6.???.etc to .config and used make old_config

Finally make sure you are using the right version of gcc, dont recall off hand, but I think ubuntu kernel is compiled on gcc 4.something.

---

### Post by elchico04 on 2008-02-19
thanks for your help!!! I finally got the drivers installed and it also installed a utility to control the graphics card so I have my widescreen resolution as well.

I had the wrong kernel-source installed ](*,)


Now my next problem. (sigh)

I installed the ati driver (much easier) but it didn't do anything. Is there some special step to activate the second graphics card?

When I try to open the ATi catalyst control center (configuring app fro ATI cards) it gives me the error "no ATi graphics driver detected"

:(

---

### Post by markitect on 2008-02-19
You'll need to have both drivers loaded in xorg.conf.  Then youll need at least two screen, one for each card. Beyond that I'm not sure how much help i can be.

---

### Post by elchico04 on 2008-02-20
You are helping a lot. Don't worry.

I just tried to boot into ubuntu again and the X server couldn't load. It said something about their being no screens! So I imagine that it tried to load the ATi driver and not the nVidia ones. So hopefully I just need to configure the ATi driver to have some screens setup onto it.

---

