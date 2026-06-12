---
title: "Cannot run Ubuntu Live CD with a 9600GT"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by xWhiplash on 2008-03-10
As soon as I installed my EVGA 9600GT, Ubuntu Live CD wont work, it will go into safe graphics mode instead of the desktop.  How can I fix this?

---

### Post by neurostu on 2008-03-10
The liveCD does not contain all the drivers for all the possible video cards. If you want to use your video card with the live cd you should look into making your own live cd with the video drivers on it. (I'm not sure HOW to do this, but I'm pretty sure you can).

Also if you are really going to be using ubuntu a lot its probably going to be worth it to just install ubuntu, during which ubuntu will download the right drivers to your HDD.

---

### Post by xWhiplash on 2008-03-10
How would I install while in safe graphics mode?

---

### Post by Madman6510 on 2008-03-10
When the boot screen for the CD comes up, pick "Install in safe driver mode", or something of the like.

---

### Post by por100pre1 on 2008-03-11
> **Madman6510 said:**
> When the boot screen for the CD comes up, pick "Install in safe driver mode", or something of the like.

Yes, xWhiplash, that card is newer than Ubuntu Gutsy. You'll likely need to install the Nvidia driver once you install Ubuntu. [Envy]("http://albertomilone.com/nvidia_scripts1.html") can help, well, I hope so...

---

### Post by Meatshield on 2008-03-11
What you have to do is install Ubuntu on your hard drive, then go into Ubuntu (which hopefully will boot without safe mode) and go to the "Restricted Driver Manger" and turn on the drivers (assuming they show up).

---

### Post by LeAstrale on 2008-03-11
> **Meatshield said:**
> What you have to do is install Ubuntu on your hard drive, then go into Ubuntu (which hopefully will boot without safe mode) and go to the "Restricted Driver Manger" and turn on the drivers (assuming they show up).


AFAIK the above is NOT TRUE for the 9xxx series of nvidia cards or the 88xx series for that matter. The only thing that seems to work for people is installing the driver from nvidia.com (you have to reinstall everytime you update your kernel) which means that you need to be sure you have the latest updates before installing the graphics driver.. 

as far as booting the normal livecd you need to set your card to use the vesa driver before you will have any luck at all.


please ask in this thread if you need further help doing the above

/Astral-1

---

### Post by xWhiplash on 2008-03-11
So if I cannot use the GUI, how can I go to nvidia.com to get them?  Should I burn them onto a CD or something then run it?

---

### Post by PmDematagoda on 2008-03-11
> **xWhiplash said:**
> So if I cannot use the GUI, how can I go to nvidia.com to get them?  Should I burn them onto a CD or something then run it?

You can use wget to get the driver directly to the currently working directory.

But first of all you need to install Ubuntu.

---

### Post by neurostu on 2008-03-11
When you install Ubuntu it will use the VESA driver until the appropriate driver becomes available, so you will have a GUI.  You won't need be working with only the command line.  

So again the first step is to install Ubuntu onto your HDD then post back here...

---

### Post by Neo0351 on 2008-03-11
I'm running a Leadtek 9600GT and I am able to boot into the GUI with a gutsy live cd.  when the live cd askes how to boot, I selected the graphics safe mode instead of the normal boot.  Sometimes it works, sometimes it doesnt.  I found it easier to use my old 7300LE to install, then set up everything I use, then install the latest nvidia driver, the best seems to be the 171.06.

---

### Post by LeAstrale on 2008-03-12
i would suggest installing from the alternate install disc and then afterwards use the vesa driver until you've downloaded the official nvidia drivers.

---

