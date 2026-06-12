---
title: "Need help fixing Nvidia driver"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by ripple01 on 2007-03-26
Hi,

I'm brand new to Ubuntu, and I've successfully set up a dual boot with Windows XP. I found some instructions (can't remember where now, sorry) about installing Nvidia drivers and followed them, and something went wrong. Now when I boot, it boots directly to the terminal and says it cant load xwindows. I hit "?" in the terminal and a version screen came up and it said the following:

FATAL: Error running install command for nvidia
(EE) NVIDIA (0): Failed to load the NVIDIA kernel module
(EE) NVIDIA (0): *** Aborting ***
(EE) Screens found, but none have a useable configuration

Does anyone have any suggestions to help me complete this driver installation?

Thanks,
ripple01

---

### Post by gh0st on 2007-03-26
There is a really cool script to setup your Nvidia drivers called Envy. I found it's bailed me out a few times, it's written by Alberto Malone and he does a really great job.

Check it out here: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

It will run in the terminal with a text menu or in a Gnome window. I've found it great when I can't boot the xserver and need to run it from terminal.

I don't think it's in the repos but it's easy enough to install in the terminal, here's what you need to do.

```

wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu3_all.deb

```

To download the Envy deb

```

sudo dpkg -i  envy_0.9.1-0ubuntu3_all.deb

```

To install it

```

envy

```

To run it and follow the menu. 

Hope that works for you, good luck :)

---

