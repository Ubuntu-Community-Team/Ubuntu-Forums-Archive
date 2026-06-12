---
title: "Cedega Setup Problems"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by The Browncoat Cat on 2007-09-17
Excuse my ignorance, but I am having great problems getting Cedega to do anything on my system. My system is as follows:[LIST]
[*]CPU Pentium D 915 Processor Dual Core (2.8Ghz)
[*]Memory 1024 Mb (533Mhz)
[*]NVidia GeForce 7300 Turbocache 256Mhz Graphics Card[/LIST]
When I run Cedega, only the "Mount" option is available.  Running the System Test tells me that the "Open GL Drivers are not set up correctly".

I think the root of the problem is I cannot get NVidia Accelerated Graphics driver from the "Restricted Drivers Manager" to work.  I believe I need this driver in order to get the graphics on my machine working.

Any help in resolving these problems, so that I can get Cedega running and be able to play *Guild Wars* would be greatly appreciated.

---

### Post by Matthew Wiebelhaus on 2007-09-17
What errors do you get when you try to enable the driver?

---

### Post by luptinpitman on 2007-09-17
I personally run World Of Warcraft through Cedega and I feel your pain.  My problems were specific to the ATI card I tried to use for 6 months.

Once I dropped in an nVidia card I used a program called ENVY to load the proprietary nVidia drivers and all problems were solved.

Some people advise against using this program (not sure about all the technicalities people have problems with) but it has worked for me and quite a few others.  Might give it a shot while waiting for the graphics manufacturers to open-source their drivers.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Once you get your 3d acceleration fixed you will simply insert the install CD and then "mount" it in cedega.  You will then be able to run install.exe or setup.exe or whatever just as you would under window$ :)

---

### Post by The Browncoat Cat on 2007-09-18
> **Matthew Wiebelhaus said:**
> What errors do you get when you try to enable the driver?

When I reboot the computer, the X-Server will not start, leading to no GUI.  It seems that any change to the xorg.conf file stops X-Server from running, and I have to restore the default version of the xorg.conf file I have backed up

---

### Post by frodon on 2007-09-18
> **The Browncoat Cat said:**
> Running the System Test tells me that the "Open GL Drivers are not set up correctly".At the time when i used cedega this test always answered me that despites i had correctly installed my drivers, besides i never got any problems to run my game with good performances so i would just ignore this message, i think the problem is more about the cedega test than your system (if you are sure to have well installed your drivers).

If i was you i would stop to pay for cedega and just use wine, guild wars is well supported by wine though you have to perform some wine tweaks explained here :
[http://appdb.winehq.org/appview.php?iVersionId=7530](http://appdb.winehq.org/appview.php?iVersionId=7530)

---

### Post by The Browncoat Cat on 2007-09-18
> **luptinpitman said:**
> I personally run World Of Warcraft through Cedega and I feel your pain.  My problems were specific to the ATI card I tried to use for 6 months.

Once I dropped in an nVidia card I used a program called ENVY to load the proprietary nVidia drivers and all problems were solved.

Some people advise against using this program (not sure about all the technicalities people have problems with) but it has worked for me and quite a few others.  Might give it a shot while waiting for the graphics manufacturers to open-source their drivers.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Once you get your 3d acceleration fixed you will simply insert the install CD and then "mount" it in cedega.  You will then be able to run install.exe or setup.exe or whatever just as you would under window$ :)

Thanks for the advice. I downloaded Envy, it installed itself, found the right driver, installed it, and when I rebooted, the nVidia logo flashed across my screen. Running the Cedega System tests was successful this time.  I will have a go at installing *Guild Wars* tonight.

---

