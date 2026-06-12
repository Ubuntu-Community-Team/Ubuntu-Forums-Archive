---
title: "Need Help With Graphics Card."
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by gRiMgRaVy014 on 2006-04-23
I'm trying to get my Nvidia Geforce 5500 FX graphcis card to boot into ubuntu , however when I try to it never starts freezes in the cmd line. Please Help.
I'm booting with the live cd because I want to be sure that my card will work.

---

### Post by johnc4510 on 2006-04-23
I have the exact same card and have been using it for over a year on Ubuntu Breezy and now Dapper.The driver you need is glx. From the command line:
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

I don't know about from the live cd before install, but after install this worked perfect for me more than once

---

### Post by nalmeth on 2006-04-23
At what point during boot does it stall?
It may be a different problem, because NVIDIA is well supported in Linux.
Can you give us some output of an error message, or point out just when the boot fails?

---

### Post by gRiMgRaVy014 on 2006-04-23
Well it gives no error just when normal text is coming up when ubuntu is loading it stops flowing text and goes to a blank page with a unscore not blinking.

---

### Post by Resurrection on 2006-04-24
Yes I have the same problem.  I am used to the Ubuntu boot sequence.  After Grub, Ubuntu (Breezy with all the latests updates) starts to boot up.  I.e. the splash screen that says ubuntu on it and the scrolling text messages as the system boots "Setting the system clock, ALSA 0, ALSA 1...." all the usual stuff.

Then things go wrong.  

Heres what I did, I installed the card, booted into windows and the card works fine.  Installed the Nvidia drivers for WinXP.  

Then expecting to be able to boot in Ubuntu and then install the proper drivers, I rebooted.  Like I said before, all the usual boot messages, and it stops at a black screen with a cursor not blinking in the top left corner.  This is normally where you would get the Login manager (or is it the screen that shows Nautilus and what not starting up first?  Can't remember all of a sudden).  

Switching the video cable to the old reliable on board graphics port doesn't work at this point as I only get a black screen.  So basically the problem is that Ubuntu doesn't know what to do with the graphics card to even give you a command prompt or the lowest resolution setting.  But it won't use the on board graphics either.  If I pull the card, things work fine again.

I would have expected ubuntu to fully boot and me to login, and then to have a very low resolution until I was able to install the drivers.

Are my expectations wrong?

Edit:  Should have searched first:  [http://ubuntuforums.org/showthread.php?t=143561&highlight=geforce+5500]("http://ubuntuforums.org/showthread.php?t=143561&highlight=geforce+5500")

Think I will give that a shot.

---

### Post by Resurrection on 2006-04-24
Ok, got it working, thanks to the other thread that I provided the link to.

What I did:

1)With power off, removed the Nvidia card.
2)Powered on, with monitor connected to on-board video
3)Installed Nvidia drivers:
> 
sudo apt-get install nvidia-glx nvidia-kernel-common

4)Then edited the xorg.conf:
> sudo nano /etc/X11/xorg.conf
Under Section "Device"
> 
Section "Device"
        Identifier      "Intel Corporation 82810E DC-133 CGC [Chipset Graphics$
Driver          "nvidia"
#       BusID           "PCI:0:1:0"
EndSection
5)Then shutdown, installed card and cable, and restarted

System booted into Ubuntu without any further issues.

Now my only question is,
Is there any kind of a settings manager for my card, sort of like how you get a separate manager for Nvidia cards under Windows besides the OS one?  Nevermind, again answered my own question, did 
> sudo apt-get install nvidia-settings
Then after it installed, typed nvidia-settings in terminal and a nice control panel pops up.

Edit:  One more question:  In the device manager, My card shows up as Unknown.  Is this a problem?

---

