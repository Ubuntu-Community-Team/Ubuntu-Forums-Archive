---
title: "Problems starting up Ubuntu"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by britonk on 2007-04-03
Hi,

I am new to Ubuntu and Linux for that matter but seems Microsoft seem to have lost the plot I think it's time to find a new OS.

I want to run Ubuntu from the CD to try it out. Unfortunately I seem to have some graphics related problems. The splash screen doesn't display properly (it's B&W and not all the pixels are being displayed) and even after that I just get some vertical lines over the whole screen rather than the GUI. 

I have tried editing the startup options to disable the splash screen and also removed the 1024768 option for screen res but it didn't work and I don't really know what I am doing.

I am using the AMD 64 6.10 desktop ISO and the CD seems to be burnt correctly no problems there.

As I have said I am a complete beginner so if anyone can suggest anything I would be very grateful and sorry if the solution is, in fact, obvious. My hardware config is:

ASUS M2V Motherboard
AMD 64 dual core 4200+ CPU
2GB DDR2 RAM
Nvidia GeForce 7600GT 256MB graphics

Thanks in advance

---

### Post by Sammi on 2007-04-03
First off, if you're new to Ubuntu then I strongly suggest using the excellent, well written, and simple ubuntu beginner guides found on this page: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

I don't really know much, but to me at glance your system specs seem to be compatible with Ubuntu.

---

### Post by britonk on 2007-04-03
Thanks that is a good beginners guide but for the time being doesn't seem to tell me how to get round this problem. I have had *some* success with "Knoppix" by typing the following command on bootup:

xmodule=vesa

From what I can gather this forces graphics into "vesa" mode? Is this right and can I do this in Ubuntu?

---

### Post by Sammi on 2007-04-03
Did a search on the forum and found something similar to what worked for you in Knoppix: [http://ubuntuforums.org/showthread.php?t=399670](http://ubuntuforums.org/showthread.php?t=399670)

>  -At the boot screen where it says the following: Start or Install Ubuntu, run in safe graphics mode, Check CD, boot first hard disk, memtest etc etc (see this link for awesome guide with pics: ([https://wiki.ubuntu.com/EdgyKnownIssues/5961](https://wiki.ubuntu.com/EdgyKnownIssues/5961), follow the guide BUT also delete "quite" and add these options if that guide alone didn't work. irqpoll noapic nolapic. so the final end of the line would be: .............../ram rw irqpoll noapic nolapic -- break=bottom (NOTE: the "dots" just represent the begining of the boot line that doesn't need changing). There are also other options that may work if these didn't. you can also try: 
acpi=off
pci=irqroute
xmodule=vesa
vga=normal
vga=771
pci=irqroute
framebuffer=falseThis guy is being a bit unclear, I think, but it seems like he's trying to say that one needs to press F6 when at the boot menu on the Live CD, where you will have the opportunity to add one of those lines to them command. you said that xmodule=vesa worked in Knoppix, so try that.


I also found this one who seems to have solved the same problem you're having: [http://ubuntuforums.org/showthread.php?t=330118](http://ubuntuforums.org/showthread.php?t=330118)

> I managed to find a solution :grin: :grin: 

Seems to be some issues with the nVidia drivers, so you do this:

1. Hit f6 on the menu, delete quiet splash from the boot parameter line, and add single. Single stops it loading x and a load more crap.

2. Once booted, type pico /etc/X11/xorg.conf. Find your video card, and change driver "nv" to "vesa".

3. Save (ctrl - o), exit pico (ctrl - x), then type startx. This starts x using the VESA drivers for video.

== Only do the rest if you want to load nvidia drivers for accelerated graphics / better performance (may as well).

4. Once ubuntu loads up, goto programs -> accessories -> terminal. Type /usr/sbin/synaptic into the terminal to start synaptic package manager.

5. Now following these instructions:

[https://help.ubuntu.com/community/Bi...t=%28nvidia%29]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29")

(I'm doing this from memory, but you will get the gist of what I mean).

In repository prefs, make sure all boxes are ticked (ie restricted packages are available). Close, click reload, wait.

6. Back in the terminal, type uname -r to see your kernel version, it's 2.6.17-10-generic.

7. Click search in synaptic, enter: linux-restricted-module. Select the correct one for the above set of numbers, you might have to right click on it and press upgrade/reinstall, but make sure you do it.

8. Now search for nVidia. Find nVidia glx and select install.

9. Press apply in synaptic.

10. Terminal again. Type nvidia-xconfig.

11. Press ctrl-alt-backspace to kill x, enter startx to restart x, and bam :smile:

---

### Post by britonk on 2007-04-04
Thanks so much! The second option (changing the xorg.conf file) seems to work but it's running at 640X480. I can't seem tp find a way of changing this in the interface - is there something I need to add after startx to get a better screen res?

Thanks again!

   Brian

---

