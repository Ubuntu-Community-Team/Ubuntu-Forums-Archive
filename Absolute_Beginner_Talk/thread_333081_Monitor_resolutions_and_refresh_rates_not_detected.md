---
title: "Monitor resolutions and refresh rates not detected!"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Amadeo on 2007-01-06
So, this is my first Ubuntu install, and also my first Linux install in many years.  I'm a very inexperienced user, but I do tend to know hardware relatively well.  

I have an Nvidia 6600GT AGP video card and an old Hitachi SuperScan Elite 802 monitor ( [http://www.monitorworld.com/Monitors/nsahitachi/superscanelite802cm802u.html](http://www.monitorworld.com/Monitors/nsahitachi/superscanelite802cm802u.html) ).   Not all of my supported resolutions are available within Gnome, and the only refresh rate I can choose is 60Hz.  I would like to use a default of 85Hz on all my supported resolutions.

First thing I imagine I need to do is update my video drivers.  I began to follow the documentation I found on it, but it seems outdated, because some of the options don't seem to be available in Synaptic...either that or I'm blind!  

I have a Pentium 4 2.26GHz processor and 768MB PC2100 DDR (will be 1GB once my broken stick is returned).  

Any help would be greatly appreciated!

---

### Post by Amadeo on 2007-01-06
I should add that I've been following the guide found on: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

The problem is, the linux-restricted-module part confuses me.  As stated before, I have a Pentium 4 2.26GHz, which I guess can be considered as a 686 processor.  The linux-restricted-modules available for my processor are 368 or 686.  That part seems simple enough, until you read the 686 notes which say: Obsoleted by linux-restricted-modules-generic.  So my only real choice is the 386 package...yet I already have linux-restricted-modules-generic installed...what am I supposed to be doing here? Very confused...

---

### Post by quartzy on 2007-01-06
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29) (Edgy)

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29) (Dapper)

Maybe? (I don't have a nvidia so I don't really know)

---

### Post by Amadeo on 2007-01-06
Thanks! That seems to have worked.  I was wondering if I could just skip the first step, and I guess I can.  

Now the only problem is, my monitor resolutions and refresh rates are still not being supported.  I'm stuck at 75Hz across the few that are actually shown.

---

### Post by quartzy on 2007-01-06
[This]("http://ubuntuforums.org/showthread.php?t=83973") HOWTO may help you.

---

