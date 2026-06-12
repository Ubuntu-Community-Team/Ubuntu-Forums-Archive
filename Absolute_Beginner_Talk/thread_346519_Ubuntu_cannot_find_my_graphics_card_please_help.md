---
title: "Ubuntu cannot find my graphics card please help"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by RDUBBALO on 2007-01-25
Hello Everyone I am new with Ubuntu and I am looking foward to getting started, but I am having a problem with the install and I havent found this in any other posts. My disk works and I get to the ubuntu start up selection screen, then it starts to go and I get a screen that has a window pop up saying "Failed to start the x server (your graphical interface) It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?" Ok so then i looked there and I have (ww)I810: no matching device section for instance(BusID pci :0:2:0) and (EE) No devices detected Fatal error no screens found. So i guess it isnt picking up the graphics card. Ok I have no idea where to go from here and i see everyone out here is more than helpful so i would appreciate some help. Thank you. I am running a dell dimension E310 and i have a seperate graphics card, PNY 128 mb ddr G-Force fx 5500 pci.

I tried to install the nvidia grafix driver from the terminal. 
Code:
sudo apt-get install nvidia-glxto install it, then
Code:
sudo nvidia-xconfig

Ok this works here after pressin ctrl+alt+f6, but then after the config part it doesnt do anything it say it is installed, but then how do I get ubuntu to start up again. I tried to reboot and it still says its still missing. I need to know what to do after this step here the config code.

---

### Post by BarfBag on 2007-01-25
It could be an error on the CD itself.  Try re-burning the Ubuntu .iso at 12x.

If that doesn't work, try installing it in safe graphics mode.  It's just as easy as the graphical installer - just text based.

Do you happen to know that graphics card you have?

---

### Post by RDUBBALO on 2007-01-25
PNY 128 mb ddr G-Force fx 5500 pci its not the cd it goes throgh just needs to find the graphics card.

---

### Post by BarfBag on 2007-01-25
nVidia Geforce cards have excellent drivers for Linux.  Even the open source drivers (which come with Ubuntu by default) are decent.  It shouldn't be doing what it's doing.

It's very possible that there's an error on the CD.  When you burn at higher speeds, it sometimes skips - which corrupts files.  Like I said before, I suggest re-burning it at 12x.  If it still doesn't work, try installing it in safe graphics mode.

---

### Post by RDUBBALO on 2007-01-25
> **BarfBag said:**
> nVidia Geforce cards have excellent drivers for Linux.  Even the open source drivers (which come with Ubuntu by default) are decent.  It shouldn't be doing what it's doing.

It's very possible that there's an error on the CD.  When you burn at higher speeds, it sometimes skips - which corrupts files.  Like I said before, I suggest re-burning it at 12x.  If it still doesn't work, try installing it in safe graphics mode.

ill try this and get back to you thanks.

---

### Post by meng on 2007-01-25
Try switching to console mode (ctrl-alt-f1 or other f-key should work too) and
sudo dpkg-reconfigure xserver-xorg
and choose the 'nv' driver for your display.

---

### Post by RDUBBALO on 2007-01-25
what about the burn method?

---

### Post by BarfBag on 2007-01-25
> **meng said:**
> Try switching to console mode (ctrl-alt-f1 or other f-key should work too) and
sudo dpkg-reconfigure xserver-xorg
and choose the 'nv' driver for your display.

I don't think this will work.  The live-CD already uses the open source (or "nv") drivers.  He tried installing the official ones, but it since it's only a live-CD - it didn't stick when he rebooted.

---

### Post by RDUBBALO on 2007-01-25
> **meng said:**
> Try switching to console mode (ctrl-alt-f1 or other f-key should work too) and
sudo dpkg-reconfigure xserver-xorg
and choose the 'nv' driver for your display.

the what do i do after this like how do i pick it the how do i start ubuntu back up

---

### Post by RDUBBALO on 2007-01-25
> **BarfBag said:**
> I don't think this will work.  The live-CD already uses the open source (or "nv") drivers.  He tried installing the official ones, but it since it's only a live-CD - it didn't stick when he rebooted.

why didnt it stick when i rebooted

---

### Post by BarfBag on 2007-01-25
> **RDUBBALO said:**
> why didnt it stick when i rebooted

The Ubuntu CD is basically a live-CD.  A live-CD is an OS bootable from the CD.  It stores all changes to your RAM (or memory), and when you reboot your PC - it clears them.  It doesn't stick until you actually install the OS.  They did this so you can try it before you install it and not do anything to your system.

---

### Post by RDUBBALO on 2007-01-25
ok reburning the cd did not work, but the other thing did where i get into the config and pick it after i pick all the things i get back to the command line and i dont know what to do from there

---

### Post by RDUBBALO on 2007-01-25
meaning after i select all my configurations it takes me to the command prompt and how do i get it to start up without rebooting the computer since i will lose all that info. or how can i just go ahead and install it.

---

### Post by BarfBag on 2007-01-25
Wow.  I stand corrected.  Sorry for misleading.  Type (without quotes) "startx"

---

### Post by RDUBBALO on 2007-01-26
WOW thank you sooo much. Yes that worked startx and the other code so change the config. Thank you soo much. Now i am using this ubuntu to send this. This is soo great i love it already. Oh man so here is another question. If i decide to install this will it partition my hard drive and keep all my current files on there?

---

### Post by BarfBag on 2007-01-26
> **RDUBBALO said:**
> WOW thank you sooo much. Yes that worked startx and the other code so change the config. Thank you soo much. Now i am using this ubuntu to send this. This is soo great i love it already. Oh man so here is another question. If i decide to install this will it partition my hard drive and keep all my current files on there?

You have to shrink your Windows partition to make room for Linux.  It's kinda risky - so **be sure** to have your data backed-up.  Defragment your hard drive in Windows.  Then, boot the Ubuntu CD and do what you have to do to get it to run.  Double click on install, and go through the steps until you get to the partition manager.  There should be an option to shrink your Windows partition, and a slider for you to tell it how small.

---

