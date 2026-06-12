---
title: "How do I install a new video card?"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by seeknowsage on 2007-05-12
I am a complete linux newbie, but I have Ubuntu v6.04 installed just the way I like it (Beryl, etc.). I want to remove an ATI 9700 Pro video card and replace it with an NVIDIA 6800gt. Are there any straight-forward guides out there that explain how to do this? Is it even possible (without, of course, completely screwing my system up ;)?

While I am asking...does anyone know if a 9700 pro will run at 1680x1050 on an Acer AL2216 monitor?

---

### Post by starcraft.man on 2007-05-12
> **seeknowsage said:**
> I am a complete linux newbie, but I have Ubuntu v6.04 installed just the way I like it (Beryl, etc.). I want to remove an ATI 9700 Pro video card and replace it with an NVIDIA 6800gt. Are there any straight-forward guides out there that explain how to do this? Is it even possible (without, of course, completely screwing my system up ;)?

While I am asking...does anyone know if a 9700 pro will run at 1680x1050 on an Acer AL2216 monitor?

 
YAY, good choice, I like my 6800 GT too :D

Well, hmmm, ya you will have quite a few steps now...

1) If you have beryl in your sessions, disable it. Should be a box on the line, so turn off beryl-manager and emerald --replace.

2) Then, right click on the beryl icon, I assume it will be in your tray and select window manager > Metacity. Then right click again and select window decorator and switch it to GTK.

3) Open up the Terminal (Alt+F2 then type in "gnome-terminal" and enter) and then type in this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup222

```

then

```
gksudo gedit /etc/X11/xorg.conf
```

Then scroll down to your driver entry, and next to driver, switch it to "vesa" instead of "ATI" I believe thats the generic one, nv is just for nvidia.

4)Then reboot, just make sure that beryl isn't loading and everything is correct. If thats successful and everything is working, power off the PC and swap in your new card. I believe should detect fine and proper and boot up correctly with the vesa drivers. 

5) Now your gonna install your NVidia drivers, go here and use [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") . Download and install the 0.9.3 debian, double click on it, install. Go to Applications > System Tools > Envy. Select automatically install Nvidia drivers, answer yes to any prompts and then reboot at the end of it.

6) Now that your booted back up into Ubuntu with your Nvidia drivers, you can proceed to uninstall your ATI drivers, by whatever means you used to install them. They are just left overs and taking up space. Then you can go back in sessions and recheck beryl and emerald to load at startup and reboot.

7) Back to working. Have fun again :)

Thats it I think, I believe I covered everything that you have to do/that could go wrong. Any questions just post back :)

Oh and I know nothing about ATI cards. Good luck swapping. Now that I think of it, you may wanna just remove the ATI drivers automatically with envy before putting in the nvidia drivers, up to you. I don't think the order of removing the ati to installing new drivers makes any difference.

OH! And as to your last question, I dunno, I'm an nvidia man, through and through.

Thats it, have a nice day and good luck. And yes, that took me a bit to write, I was multitasking :)

---

### Post by seeknowsage on 2007-05-13
Thank you very much for your response! I'll admit, my question was a bit preemptive as it will still be a few days before I am able to replace my card. (I loved ATI for the longest while, especially when NVIDIA was sucking it up, but man, is their support for Linux HORRIBLE! Hopefully the recent announcement that they'll strive for better open source support will help a lot!) Anyways, I'll let you know how it goes. Thanks again!

---

