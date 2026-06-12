---
title: "How do I un-update my system?"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by conteur on 2007-04-12
Today's kernel updates hosed up my system. It's funny, I was just pontificating about the seemingly daily security updates to our XP systems at work, and how they are constantly breaking our software installations, and when I get home, my Linux laptop is sick as a dog. I first suspected the updates when the Ubuntu Splash screen started showing up again. I have an Inspiron 2500 laptop, and was getting annoyed by the flashing dots and lines on the screen during startup and shutdown. I rectified the problem by setting the /boot/grub/menu.lst  to boot quiet. Today the splash screen is back. Next obvious difference: No sound! When I mouse click the volume control (which now has a line through it) I get a message:

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

I don't want to remove the control, I want the sound to work.  And finally, the wireless network is messed up. I can see the network but the computer won't connect to it. When I enter the boot menu and select the previous kernel,  Ubuntu, kernel 2.6.17-10-generic, the sound and network start working again. But those pesky dots and lines are back.  Any help would be appreciated. Thanks in advance.

---

### Post by jem7v on 2007-04-12
What version/release of Ubuntu are you running?

---

### Post by conteur on 2007-04-12
Ubuntu Edgy 6.10

---

### Post by wormser on 2007-04-12
Just boot into the older kernel.  When you turn your computer on the Grub screen appears.  Press the down arrow to the older kernel.

You can edit Grub to make the working kernel default.  Just change the **default** number to the working one.  Just remember that 0 is the first entry.  It is located at:

/boot/grub/menu.lst

---

### Post by conteur on 2007-04-12
Thanks.

---

### Post by beefcurry on 2007-04-13
that dosn't ultimately solve the problem if you want to use the newer kernel. Anyway to fix this?

---

### Post by wataboutbob on 2007-04-13
yes, I know what you mean, but for me, it was only the sound that was shot. Which was fixed after a couple of restarts - don't ask me how or why *shrug*

Others who had the same problem, had to recompile the latest alsa drivers and it worked for them.

EDIT: 

here's the thread which solves the issue

[http://ubuntuforums.org/showthread.php?t=406676](http://ubuntuforums.org/showthread.php?t=406676)

---

### Post by Jonam on 2007-04-13
I had exactly the same problem. the Grub menu.lst got completely messed up with the recent kernel update. 

I found out in a roundabout way (see [http://ubuntuforums.org/showthread.php?t=403746](http://ubuntuforums.org/showthread.php?t=403746)) that the menu.lst file is updated with the kernel updates to a set of default values contained in the same menu.lst file. If you set the default values correctly, then kernel updates are no problem.

The only other thing that got messed up for me was that the swap space on the harddisk disappeared and I had to manually fix it. There must be other files that get changed during kernel updates but I have no idea what they are.

Jonam

---

### Post by Shinoda on 2007-04-14
If you don't want to compile ALSA yourself, try reinstalling it:```
sudo aptitude purge linux-sound-base alsa-base alsa-utils
sudo aptitude install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop
```(replace [FONT=Courier New]ubuntu-desktop[/FONT] with [FONT=Courier New]xubuntu-desktop[/FONT] if you're running Xubuntu) and reboot.

If you do or have to, follow e.g. [these]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#ALSA_driver_Compilation") instructions or the ones at the thread wataboutbob mentioned.

---

### Post by macogw on 2007-04-14
Kernel updates are generally to add new drivers to the thing, so if you don't have a non-working piece of hardware to begin with, you don't need kernel updates to constantly happen.  In Synaptic, you can lock the kernel version number to keep it from upgrading at all.

---

