---
title: "I've finally decided to face my fears"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by colercoaster on 2007-08-14
Yes, that's right. I've decided to face my fears and venture away from the safe world of Windows (well,   Windows was never really **safe** to say, but I have decided to hop on board and give this wonderful operating system a go.

So far, it's been a bit of a hassle, but I expected this as a first time Linux user. To be honest, I was scared to death of all the errors I feared I would encounter...but there has only been really one difficult one I have come across. I built my machine specifically for gaming, but I've decided my time for games is coming to and end and I should perhaps concentrate living in the now. This is well and all, but the 8800 GTS card I bought is giving me some issues. I've read that I'm supposed to use specialized nVIDIA drivers...but everytime I install them it seems my xserver refuses to load at startup. So I reconfigured and used the standard nv drivers and they seem to be working fine.

There is one other issue in this, I can't use the desktop effects and this is rather troublesome to me. I also feel like because I'm running the standard drivers that I might not be getting as good of video rendering that I should be?


If anyone could offer some advice/suggestions I would be more than happy to give them a try. They hopefully don't resort to me reinstalling this OS as I've done it several times now.


Oh, and this is my intro to the Ubuntu community! I hope to be joining the open-source community for awhile and hope to make some new friends in the process :D

Cheers!
Cole

---

### Post by Kingsley on 2007-08-14
Hey, welcome to Ubuntu. Are you using 64-bit Ubuntu? This topic may help you out. 

[http://ubuntuforums.org/showthread.php?t=496103](http://ubuntuforums.org/showthread.php?t=496103)

Have fun.

---

### Post by reylafo on 2007-08-14
enable nvidia drivers at System-Administration-Restricted Driver Management.

visit and save the Ubuntu-Feisty Guide at: [www.ubuntuguide.org](www.ubuntuguide.org)  for more details.

welcome :guitar:

---

### Post by colercoaster on 2007-08-14
Thanks guys, and no I am not using the 64 bit version of Ubuntu..sticking with 32 bit even though I could be using 64 bit.

I'll give your suggestion a try, hopefully I can log back in :(

---

### Post by colercoaster on 2007-08-14
Hmm, to no avail...

I've mastered the dpkg-reconfigure xserver-xorg command on the positive side..

I have no clue how I am to fix this, I've tried all the methods of installing the driver...I guess it isn't that important.

---

### Post by irish_flu on 2007-08-15
You're correct that your problem with "Desktop Effects" and such is because of the driver you're using.  It doesn't support the features necessary to do such sweet things.

I'm guessing (guessing is the important word here) that you're having problems because your card isn't supported in the *version* of the NVidia drivers you're getting through the Ubuntu repositories.

If that is the case (and I think it's likely) you're gonna want to get and use the drivers available directly from Nvidia, in order to get the newest version.

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Check out this page for instructions (note, I have not used these myself and cannot vouch for them):
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

Good luck, my friend!

---

### Post by Brightbelt on 2007-08-15
Hi, 
Welcome to Linux. Here's another possibility in case other options fail - it's a 3rd party freeware driver install program called 'Envy'. More than a few people have said that this program worked when nothing else would.

And it worked for me several times with an ATI-1650 when nothing else would (It does both ATI and NVIDIA installs - you choose it in the interface).

Here's the link: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)  

Good Luck,
Frank B.

---

### Post by misfitpierce on 2007-08-15
Welcome to Ubuntu and Linux... I hope you will learn it well and learn to love it... Remember a closed mind coming into an open source world will take you nowhere. And remember to ask questions here if you got a question its what we the community are here for. Enjoy :)

[http://ubuntuvideo.com](http://ubuntuvideo.com) - Useful video tutorials etc.

---

### Post by RomeReactor on 2007-08-15
Hi. **colercoaster**, what's the driver that gets installed by enabling "Restricted Divers" on your system? Please search in Synaptic for **nvidia** and tell us which driver is installed. If it is **nvidia-glx**, you might want to try uninstalling it and using **nvidia-glx-new** instead.

And as **irish_flu** pointed out, the **nv** driver doesn't have direct rendering capabilities.

**EDIT**: [According]("http://ubuntuforums.org/showthread.php?t=478331") [to these]("http://ubuntuforums.org/showthread.php?t=497264") [threads]("http://ubuntuforums.org/showthread.php?t=468353"), the **nvidia-glx-new** package found through Synaptic (version 1.0.9755) is missing an X server module needed for the 8800 GTS; the driver found in nVidia's site (version 100.14.11) works properly, so you'll want to install that, either by [downloading the driver]("http://www.nvidia.com/object/linux_display_ia32_100.14.11.html") like **irish_flu** said or using [Envy]("http://albertomilone.com/nvidia_scripts1.html"), as **Brightbelt** suggested.

---

### Post by colercoaster on 2007-08-15
I thank you all for your help and your welcoming me to the community.

I am trying the Envy route now, here's to hoping :)

Much thanks.


*EDIT*


YAY! Drivers installed and working, not sure why I am only getting 50 Hz now, but I'm not that worried :)

Now to learn Desktop Effects.
Once again, thanks to everyone :)

---

### Post by ubuntuforums on 2007-08-15
It's weird, on my other system, I installed ATI drivers for my 9600xt with Envy, and it says I'm getting 50Hz, but my monitor menu says 100Hz.  I assume that the monitor is right as my eyes aren't hurting, and the screen doesn't flicker whatsoever.

Sort of offtopic: I'm so happy, I got Counter Strike Source and Battlefield 2 both working with Cedega.  :)

---

### Post by RomeReactor on 2007-08-15
> **colercoaster said:**
> I thank you all for your help and your welcoming me to the community.

I am trying the Envy route now, here's to hoping :)

Much thanks.


*EDIT*


YAY! Drivers installed and working, not sure why I am only getting 50 Hz now, but I'm not that worried :)

Now to learn Desktop Effects.
Once again, thanks to everyone :)

I suggest you install **gnome-compiz-manager** to manage your Desktop Effects; look for it in Synaptic. Or to install from the terminal:
```
sudo apt-get install gnome-compiz-manager
```
Once it's installed, you'll find it in "System->Preferences->GL Desktop".

---

### Post by colercoaster on 2007-08-15
> **ubuntuforums said:**
> It's weird, on my other system, I installed ATI drivers for my 9600xt with Envy, and it says I'm getting 50Hz, but my monitor menu says 100Hz.  I assume that the monitor is right as my eyes aren't hurting, and the screen doesn't flicker whatsoever.

Sort of offtopic: I'm so happy, I got Counter Strike Source and Battlefield 2 both working with Cedega.  :)

On this note: How does Source run? I could always use a little FPS action here and there..too bad Cedega costs money monthly :(

---

