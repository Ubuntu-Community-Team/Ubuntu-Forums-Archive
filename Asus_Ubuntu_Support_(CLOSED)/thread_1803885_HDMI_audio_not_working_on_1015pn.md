---
title: "HDMI audio not working on 1015pn"
date: 2011-07-14
forum: Asus Ubuntu Support (CLOSED)
---

### Post by altoiddealer on 2011-07-14
I'm running Ubuntu 11.04 on Asus Eee PC 1015pn, which I have configured to multi-boot.

The HDMI audio works on my XBMC Live partition... but I cannot find a solution to get the HDMI audio to work on my Ubuntu partition.

This is the "solution" for my exact model taken from [this page]("http://sites.google.com/site/mtrons/howtos/eeepc-1015pn"):

> Get and install the latest nvidia binary drivers from the x-swat ppa [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

open a terminal and type "aplay -l"

you will get a list of Playback devices containing the analog HDA Intel  on card0 and a number of NVidia HDMI devices on card1. Test with aplay  which of the devices is the good one in your case (here it's device 8 on  card 1)
 
 now add your hw device string to pulseaudio
[QUOTE]
"sudo gedit /etc/pulse/default.pa"

load-module module-alsa-sink device=hw:1,8Restart pulseaudio or reboot your system. Now open the sound  Preferences, Hardware Tab and check that the "HDMI Output" profile is  enabled.[/QUOTE]I opened the alsamixer and nothing is muted, so I  thought that maybe the problem is that Intel is listed as the default  soundcard, opposed to Nvidia.

Every guide to change the default  soundcard did not work. They all involved the following commands/configs  which do not exist on my system:

-"sudo asoundconf" returns command not found

-"/etc/modprobe.d/" does not exist, so there is no config to edit.



Thanks in advance!

---

### Post by papibe on 2011-07-14
Have you take a look or [tried ]("http://ubuntuforums.org/showthread.php?t=1741294&highlight=hdmi")this?

Regards.

---

### Post by altoiddealer on 2011-07-14
Nope!  I did not see that... and it worked!

I did not think to try all the different profiles in Step 6~ I had assumed that Digital Stereo Output (HDMI) was the correct one.


Now I have another problem, though.  In the "Output" tab, I have two things listed:

-High Definition Audio Controller
-High Definition Audio Controller Digital Stereo (HDMI) nr 2

The HDMI audio only works when the second one is selected.

However, every time I reboot, it changes back to the first one and the HDMI audio does not work again until I change the setting.

I have already disabled "Internal Audio" under the Hardware tab.


Thanks! and thanks! :D  That was seriously driving me nuts

---

