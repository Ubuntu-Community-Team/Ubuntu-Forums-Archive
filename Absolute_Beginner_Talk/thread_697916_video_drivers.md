---
title: "video drivers"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by bebops_lost on 2008-02-15
I am trying to install Ubuntu onto my laptop (hp tx1314) and have had no end of difficulties.
It seems that the issue is with the display driver. After installation (using text-install) whenever I try to boot into Ubuntu the screen goes white and I have to hard-reset to go back to Vista. 

I have an NVIDIA GeForce display adaptor, and I think I can probably find the right driver for it online, but I have no idea how to integrate that into the Ubuntu installation (i.e. how can I get Ubuntu to 'look in the right place' and use that driver, since it seems to be omitted from Ubuntu's  default list of display drivers)

Alternatively, I've installed EasyBCD, and was hoping to add a Ubuntu entry to this once I installed Ubuntu on my extra partition, will that run Linux as a sort of 'virtual' machine over top of the Vista environment, and if so, will all the vista drivers carry over ?

any help would be hugely appreciated.
thanks:
-B

---

### Post by macogw on 2008-02-15
Exactly what video card is it?  You should be able to hit ctrl+alt+f1 to get to a terminal.  If you type in ```
lspci
``` it should list your hardware, including the model number for your video card.

---

### Post by t0p on 2008-02-15
Have you tried the Restricted Drivers Manager?  It's under **System > Administration > Restricted Drivers Manager**.

---

### Post by bebops_lost on 2008-02-16
Thanks for the help.
my display adapter is NVIDIA GeForce Go 6150.
Unfortunately I cannot access the restricted drivers because I cannot launch Ubuntu at all -not even using the live CD. Attempting to run, or install Ubuntu this way leads to the moniter crashing. 
The only way I can complete installation is by downloading the alternate cd, and using the text-based installer. 
Once that's done, when I try to launch Ubuntu the first time, it gets to the progress bar, and then when that fills up the screen goes blank and then unresponsive. I tried using EasyBCD in the hopes that Vista would load the necessary drivers before handing over control to Ubuntu, but the exact same thing happened. 

My laptop is a tablet so I'm sure that has something to do with the display issues, but if I could just figure out how to get Ubuntu to accomodate the moniter -during installation- then at least I could get the OS to start.
any ideas?
thanks again
-Brendan

---

### Post by JoshuaRL on 2008-02-16
Could you boot into the recovery console?

When Grub is loading, press Esc and go to that option.  You should be at a command line that looks something like:
```

bebops@ubuntucomputer$

```

Once there, run this command to reconfigure your graphics card/screen:
```

dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by bebops_lost on 2008-02-16
I don't get the opportunity to go to recovery mode either.
After I couldn't install ubuntu the first time, I'm now trying to dual-boot with Vista. but after I select Linux from the EasyBCD menu the loading proceeds directly to the progress bar and then the unresponsive screen no matter how many times I hit esc throughout the process.
thanks for trying though! 
any other ideas?

-Brendan

---

### Post by JoshuaRL on 2008-02-16
Yeah.  Try downloading and burning off a copy of SuperGrub.  I would also use the partitioner from the Live CD and erase the Linux partition.  Then try to fix Grub and reinstall.  That should work.

---

### Post by bebops_lost on 2008-02-17
Unfortunately I cannot use any of the features of the live cd, since I have the same display problems any time I try to use it to boot up.
is there any way I can just get Ubuntu to look for the right display drivers during the installation process in text mode?

---

### Post by JoshuaRL on 2008-02-17
Yeah, you should be able to choose the one you want.  That is, if you know what kind of video card you have and what exact driver you need.

I would suggest using the Vesa driver since it should work with just about every video card.  And from there you should be able to fix it with:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
from the terminal in your newly installed system.

---

### Post by bebops_lost on 2008-02-18
[I]I would suggest using the Vesa driver since it should work with just about every video card. And from there you should be able to fix it with:
[code]
sudo dpkg-reconfigure -phigh xserver-xorg
[\code][/I]

ok, thanks for your help, but I really can't implement any command from any terminal at all -not on live cd, not on recovery mode, nada: the blank white screen prevents me from entering any commands that might solve this display problem -kind of a catch 22. 
My precise video card is listed above, and if you think this Vesa driver will work then that's great, but  it has to be packaged into the ubuntu OS **_during installation_** i.e. I have to tell Ubuntu while it's installing, to use this driver, because after it's done installing I won't be able to run the OS to fix any of the problems it has (such as this one)
again, thanks for any help you can offer:
-B

---

### Post by JoshuaRL on 2008-02-18
Yeah, I was saying that you could run that command from a newly installed system running the vesa driver.  I would suggest using the Alternate CD and either pick the vesa driver manually, or select the install in low-graphics mode option from the CD boot menu.

Also, I fixed my code quote.  I put the wrong type of slash in the tag.  :p

---

### Post by bebops_lost on 2008-06-20
just  a heads up for anyone else out there with the same issue:
the new version of Ubuntu "Hardy Heron" or whatever, fixes this issue. The screen now loads up fine. I still haven't got the touch-screen, the webcam, or the wireless card working, but I at least have an operating system that runs, which I can presumably use to fix everything else -so a huge start.
To whichever ubuntu programmer put that fix into the newest version I say "Thank you" -you've saved me countless hours of  frustration.

---

