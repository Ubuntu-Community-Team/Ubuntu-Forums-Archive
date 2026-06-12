---
title: "X Server Issue, no idea what to do."
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by Booj2600 on 2007-09-07
Hey guys!  I had recently installed Ubuntu version 7.04 onto my computer.  However, whenever I tried to run it, a message saying:

"Failed to start the X server (Your graphical interface).  It is likely it is not set-up correctly.  Would you like to view th X server output to diagnose the problem?"

Then it kicks me to a login screen, command line prompt, like a Unix system.

Unable to find a way around this, I simply formatted the partition and reinstalled the same version.  Lo-and-behold, the error message that does not die has come back to bite me again.  I really do not understand how the xorg file could not be set up correctly (I assume this is the file it needs to be correct?), as I have no even so much as opened it in read-only mode.

In any case, this is very irritating..  Any help would be greatly appreciated.  Thanks!

---

### Post by Anicka on 2007-09-07
Log in and run the command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` If you have a non-standard keyboard (anything but a US) or anything else that isn't default, you will have to change that later or leave out the flag -phigh. If you don't know the good answer for a question given by the program, choose the default If it doesn't help, you might need to install drivers for you graphic card, but that I know very little about.

---

### Post by BrendanM on 2007-09-07
When you first install, Ubuntu tries to autoconfigure xorg.conf (which is the configuration file which controls the GUI)  to fit your hardware. Sometimes it fails at that. Supposedly the next version will be better.

In the meantime, if you post some information about your video hardware, we can try to help you figure out how to correctly setup xorg.conf.  Also, I'd like to suggest using "nano" as your text-mode editor (You'll need an editor to edit xorg, once we figure out how to fix it.) Lots of people on here are going to tell you that vi or emacs are better, but for a beginner, I think nano is much simpler.

---

### Post by Anicka on 2007-09-07
Take a look on this guide [http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html) It pretty much covers the procedure of getting the xserver to work properly.

---

### Post by ajgreeny on 2007-09-07
Did the live CD boot into a GUI as it should?  If so you could try copying the xorg.conf file from that to a usb flash disk and then replace your installed system's xorg.conf file with that one.  If it works for the live CD I don't see why it wouldn't on an installation of the same OS.

---

### Post by Booj2600 on 2007-09-07
Alright, did the "sudo dpkg-reconfigure ..." thing.  Gave me two screens, a driver one and a screen resolution one.  Did "startx", which says there was a fatal screen error, or something to that effect.  No dice.  Did the guide, same thing happened.  

I have an EVga 8800GTX graphics card, in an NVidia 680i motherboard.  That's the hardware I'm packing.  Do I need to do something involving installing drivers now?  What's the next round of advice?  

I could try the live CD thing, but what are the chances of that working?  I'd like to keep that as a last ditch thing, because it seems like if I changed anything, then it just wouldn't work again.

Thanks again!

---

### Post by ajgreeny on 2007-09-08
Your xorg.conf file is no use at the moment so will it matter if the live CD version is also no use?  Just keep a renamed copy of the original file by logging in using the cli that you can get with:-
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

Now boot into the live CD and copy the xorg.conf file from that to your home folder on the hard disk, which you will need to mount first of course.  Now boot back into your installed version and hopefully you will get a gui appear.

Good luck!

---

### Post by Booj2600 on 2007-09-09
Alright guys.  I some how got my GUI back.  I loaded a former configuration of the xorg file.  Anyway, what should I do to ensure this will always work?  Should I install the NVIDIA drivers, somehow?  Or what?  

Thanks guys!

---

### Post by Booj2600 on 2007-09-09
Nope, I lied.  I don't understand.  Now that file doesn't work either.  I really feel bad about this..  I really do want to like Ubuntu.  I especially like the theory behind it.  But..  I'm really not sure if its worth this much work.  Oh, and the live CD copying idea didn't work either.  :(

---

### Post by pequod on 2007-09-10
Dang.  I am having the exact same problem, trying to install Ubuntu on a Dell XPS M140 laptop.  It says something to the effect of "yes, I know you have a screen, but I officially refuse to use it or acknowledge that it exists"  I will try "sudo dpkg-reconfigure xserver-xorg", but something tells me that this will not help.  Also, since I am trying to work off of a live CD, even if I did edit the xconf file, will it let me save it?  Likely not.  

Is there a way to edit the file using pico, save it to my c drive, and then somehow 'point' my Ubuntu live cd boot to that file?

Bleh.  This is preemptive beginner talk, but I will be back no doubt.  I think I will try to install it on an external hard drive for now, then edit the file.

---

### Post by ajgreeny on 2007-09-10
Hi pequod.  You are right there is absolutely no point doint the "sudo dpkg-reconfigure xserver-xorg" whilst running the live CD.  Everything you do will be lost unless you save the file to a usb flash or something similar, and then what?  If your live CD gives you a gui, you have no need to run the command anyway.  You could also try copying the xorg.conf from your live cd system and copying that to the hard disk install, as I suggested in the first place, but no-one has tried that so far so it may not work for you.  Worth a try though.

---

