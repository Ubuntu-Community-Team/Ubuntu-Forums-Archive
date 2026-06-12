---
title: "Had Sound....Lost Sound....Help! (Gutsy)"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by HDave on 2007-11-22
Hi -- Been an avid Ubuntu user now for 6 weeks....

I had sound ever since the initial installation -- up until today.

Today I got my wireless modem working (finally!) and I can't imagine what I did to break sound.  I did a "modprobe usbserial", but I don't know if that has anything to do with it.

The system is recognizing a microphone apparently (as seen on the top panel vol applet)...but there is no playback device.  When I run "aplay -l", I get an empty list of playback devices.

I've been reading up on this issue from other threads and I think Ubuntu is still seeing my hardware device.  Here's what "sudo lshw -C sound" returned:

```
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

```

Can anyone help?  I can't stand the thought of starting over after having made weeks of customizations!!  I am soooooooo close to dumping windows.....

---

### Post by fastTalker on 2007-11-22
try this:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Try the "Getting the ALSA drivers from a *fresh* kernel" section:
[https://help.ubuntu.com/community/SoundTroubleshooting#head-d8ad2bdeea082f749845b766aa82831110042360](https://help.ubuntu.com/community/SoundTroubleshooting#head-d8ad2bdeea082f749845b766aa82831110042360)

---

### Post by HDave on 2007-11-23
I followed the instructions regarding the uninstallation and reinstallation of the alsa stuff....rebooted.

No change.

I also tried the follow the instructions in the other link, but was quickly stumped when I tried modprobe to load my sound drive, but didn't see one for my sound card...82801G (ICH7 Family).

If there is no driver, how did my sound ever work?  Now I am totally confused!! :confused:

---

### Post by Jumpmasterrt on 2007-11-23
This is an intermittent problem for me. It seems that my onboard sound card and aftermarket card alternatly compete for the address. I'm new to Linux but if I have a sound issue I usually just plug it into the other device and voila!

Now, WHY that happens is beyond me.... I just chalk it up to the "ghost in the machine".

---

### Post by HDave on 2007-11-26
Apparently there was a regression in the ubuntu alsa code that broke Intel High Definition Audio (HDA) on many laptops.  The key was to grab the latest also code and compile it.

I (of course) had no idea what to do on this, but I found this web page with simple instructions.  I used method "A".

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")

I should add that following the instructions required me to have my Ubuntu Live CD handy -- which I didn't have on me as I was on the road.  However, I remember that there was a checkbox in the synaptic package manager for loading packages and when I unchecked Ubuntu Live as a repository, it downloaded everything from the internet.  Compiling took about 10 minutes.

---

### Post by master_kernel on 2007-11-26
There's also compiling a new kernel :)........ but that takes a while and probably isn't best for newbies.

---

