---
title: "ubuntu on apple powerbook g4"
date: 2011-04-06
forum: Apple Hardware Users
---

### Post by netopalis45 on 2011-04-06
I recently purchased an Apple Powerbook G4 at auction. It came with Yellow Dog Linux installed on it. I have been trying to install Ubuntu without any success. I have Ubuntu on DVD and USB drive and cannot boot either of them on this machine. When I boot up I get a menu that gives me a list of options for booting, including booting from a CDROM. When I select CDROM, it looks like it is going to and then it takes me back to the menu. I have also tried forcing it to boot from an external drive and that does not work either. What other options do I have to get Ubuntu installed on this machine?

---

### Post by avtolle on 2011-04-06
I assume you are using the ppc version of Ubuntu, so, as to the DVD, does your drive handle DVDs? Ignorance at play here on my part. If so, needs to be a DVD-R, in my experience, burned as an image at the slowest possible speed (2x has always worked for me; 4x usually works).

As to USB boot, [http://sites.google.com/site/shawnhcorey/Home](http://sites.google.com/site/shawnhcorey/Home) has information. Good lucj.

---

### Post by netopalis45 on 2011-04-06
Was not using the PPC version. Never having used it before I didn't even think about it. As far as I can tell it does have a DVD reader though. Will let you know if it works as soon as the .iso finishes downloading. Thanks for the quick response.

---

### Post by netopalis45 on 2011-04-06
Worked perfectly. Now my problem is that it sees the touchpad as a regular mouse and I cannot access the settings for the touchpad. And the right-click menu is mapped to f12 for some reason and I would like to change that if possible. Ideas?

---

### Post by Sijmen on 2011-04-08
Thanks for the link! I tried burning the ISO to CD, but the ISO is to large. I'll give this a try :)

---

### Post by netopalis45 on 2011-04-10
Is it at all possible to install the regular Ubuntu on the G4 instead of the PPC version?

---

### Post by avtolle on 2011-04-12
> **netopalis45 said:**
> Is it at all possible to install the regular Ubuntu on the G4 instead of the PPC version?
Not to my knowledge. It might be possible to run the x86 version under an emulator (QEMU comes to mind), but I don't think you would be happy with it even if it would work (speed, or lack thereof would be one problem). The obvious difference is between the CPUs, and the commands under each. 

Maybe the best answer is no, unless you are able to run XP, e.g., on the G4.

Re: touchpad; I don't have any experience with this. I know there have been threads in this forum in the past on that topic. Best I can offer is a search of the forum. I presume you have looked at the FAQs linked in the first sticky above without success.

---

### Post by cfr42 on 2011-04-13
Are you able to use the trackpad somewhat while booted from the LiveCD? I can't get it to recognise mine at all. I didn't think to try F12, of course, but since I can't even move the pointer with it, I don't suppose that would make much difference.

I found my usb mouse worked better but I can't install ubuntu for regular use without the trackpad working as I usually don't carry a mouse. It didn't seem to recognise the third button and I found the setup confusing as I use the mouse in my left hand, but it did more-or-less work.

The trackpad it just doesn't see at all. Did you do anything special to get yours recognised (even as a mouse)?

---

### Post by pauljwells on 2011-04-14
> **netopalis45 said:**
> Is it at all possible to install the regular Ubuntu on the G4 instead of the PPC version?

No! Absolutely not

---

### Post by netopalis45 on 2011-05-03
Ok. New problem. I have tried installing some things from .deb because I could not find them in the Software Center but when I have the .deb downloaded it says that it has the wrong architecture. I have tried this with both the i386 and AMD 64 but neither of them work. Is there another architecture out there that I have not heard of yet that will work with this or has my computer just gone insane?

---

### Post by pauljwells on 2011-05-03
i386 and AMD64 are both X86 architecture! You need to look for powerpc-specific debs. They are a lot more rare! Inn any case, installing debs directly can lead to dependency problems - it's always best if you can find a repository (or ppa) with the package you want and add that to your sources in synaptic.

Out of interest, what were the packages you were trying to install?

---

### Post by netopalis45 on 2011-05-03
It was xserver-xorg-input-mtrack in an attempt to make the touchpad work properly. Do you happen to know of any alternatives that I could install? Also, when I try to use dmidecode to find out what specific type of hardware I have it says that the command cannot be found and will not allow me to install anything to use that command.

---

### Post by pauljwells on 2011-05-05
I can't help with the trackpad issue, sorry, but if there isn't an easily available deb compiled for powerpc, which seems to be the case, then it probably isn't going to be a simple solution. It's far more likely that you can fix this with a custom xorg.conf - post a new thread...

I can tell you that dmidecode won't work on your machine because it reads BIOS data, and Macs don't have a BIOS!

```
lspci
``` is the nearest equivalent...

---

### Post by netopalis45 on 2011-05-06
I was trying to use dmidecode because I found it on an Ubuntu site detailing how to figure out what specific type of Apple computer you have and some instructions for setting it up properly. The site is [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook). As for the .debs I was trying to install, I found a link to them on another thread and just assumed that they would be compatible with PowerPC because they were in the Apple Users category.

---

### Post by pauljwells on 2011-05-07
> **netopalis45 said:**
> Worked perfectly. Now my problem is that it sees the touchpad as a regular mouse and I cannot access the settings for the touchpad. And the right-click menu is mapped to f12 for some reason and I would like to change that if possible. Ideas?

I did a little bit of searching on this and the first question seems to be: Does the hardware actually support multiple finger gestures? Early G4 trackpads just did mouse and tap-to-click, nothing else.

I found this site, which suggests that if your trackpad is multi-touch then it can be configured as a synaptics device because the drivers are already in the kernel.

[http://www.popies.net/atp/]("http://www.popies.net/atp/")

If you look in /usr/share/X11/xorg.conf.d/ you will find a file called '50-synaptics.conf'

BACK THIS UP!! and then try editing its contents with the settings from the link. Again, I can't actually test any of this and you might break your graphical session if it doesn't work, so be sure to keep the backup copy somewhere where you can copy it back from a text only login.

Be careful!

I seem to remember when I had a G4 PB, I just used a cheap USB mouse and gave up on the trackpad...

---

### Post by pauljwells on 2011-05-07
There is also this on the official help pages, but looks a bit old...

How do I control trackpad behaviour?

Open a new terminal window and run:

sudo aptitude install powerpc-utils

to install the necessary utilities. In Feisty 7.04, this may already be enabled.

To enable tap, run:

sudo trackpad tap

To disable tap, run:

sudo trackpad notap

See

man trackpad

for more details.

---

