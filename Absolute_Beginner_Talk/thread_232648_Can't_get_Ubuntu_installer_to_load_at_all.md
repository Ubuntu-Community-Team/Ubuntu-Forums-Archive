---
title: "Can't get Ubuntu installer to load at all"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by jreedy88 on 2006-08-09
I'm using the 64-bit version of Ubuntu, as I have an AMD64bit processor.  I boot the CD and go to Start Ubuntu.  It gives me an error saying that X-Serve could not be started, and it crashes to the command line.  I don't know how to configure X-serve to get it to work with my configuration.  I'm using an ATI Sapphire X700.  Then I tried to boot into graphics-safe mode.  I get a "No Signal" message on my screen.  The computer sits blank like that indefinitely.  Any ideas/easy troubleshooting guide?  Possibly the command to get xserve to work correctly?

---

### Post by GuitarHero on 2006-08-09
If you can get to a prompt type sudo dpkg-reconfigure xserver-xorg.  Choose mesa as the driver for now.  It's also possible the burn was corrupt.  Try reburning the iso at a slower speed.  Also you can try using the alternate installer which is text only so you wont have x server problems.

---

### Post by jreedy88 on 2006-08-09
Tried the command, I guess it worked.  I got to set up a few things.  It dumped me back to the command line, where I couldn't get it to try the installer again.  I tried "gdm" and it said only root wants to run gdm, so I tried "sudo gdm" and it said gdm is already running.  Argh.

---

### Post by junglepeanut on 2006-08-09
Try 

startx

I agree since it is ati choose vesa as the option when dpkg-reconfigure. Then once x is running get either fglrx or ati driver. Many posts on this.

---

### Post by jreedy88 on 2006-08-09
After trying the above steps and using startx, it starts the x-server system, but it stops outputting to my monitor.  I get a blank screen then my monitor turns off(auto off after no signal).  Am I missing something in the reconfigure process?

---

### Post by daou on 2006-08-09
If you need to restart the gdm from command line, type
```

sudo /etc/init.d/gdm restart
```
startx loads the x-server but if there is a problem with the gdm or if changes have been made to config options use the restart command instead.

---

### Post by junglepeanut on 2006-08-09
It sounds like x is still crashing. The only other idea I have is what type of monitor do you have? Did you try simple first when you choose monitor options?

---

### Post by junglepeanut on 2006-08-09
I know nothing but also if that doesn't work, some ati cards when running xgl need to have display switched from 0 to 1. This can be searched in the xgl ati threads. I do not believe this has to do with your problem but I don't know how 64bit starts out since the gdm is fairly simple. I can tell you from experience (32bit) I had the same issue you do. I went through the sudo dpkg-reconfigure xserver-xorg so many times it was the first command I learned. (before even cd) In the end I got mine to work, got the fglrx driver, then the ati driver. Crashed my system witht he hard locks for ati and xgl, so I had to go through the whole process again. Once you know exactly your options things work must better. Also if it is a laptop (as mine is) choosing a very high resolution gave me issues. So I start with the simple bottom three, then once I have the drivers installed, I run sudo dpkg.... again and choose my higher resolution.

Ati X700
Intel Centrino 1.73Ghz
Ati working under Breezy and Dapper.

There is a thread on how people got there ati cards to work. It is not a help thread but lists the many ways of getting your ati to work. You may want to seach through that thread for something similar to yours.

---

### Post by junglepeanut on 2006-08-09
Also try installing the correct driver from the command line even though you don't have x yet.

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv 

You may need to rerun sudo dpkg-reconfigure xserver-xorg and choose fglrx now, if you do this.

---

