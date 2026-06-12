---
title: "[SOLVED] Screen goes into power save mode at boot"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by schneiderman on 2007-09-01
Hi all,
I recently installed Ubuntu 7.04 64 bit PC onto my computer and have been having a strange problem. When I try to boot into the GUI, my screen goes into power save mode, as if it had been disconnected from the computer. I can boot into recovery mode with no problems. I have tried several suggestions posted on this site including setting the default driver to vesa, running dpkg-reconfigure xserver-xorg and installing the Nvidia driver with no luck. My system specs

Intel Q6600 quad core
evga GeForce 8800 GTX
Asus Striker Extreme
4 gb ddr2 800 mhz

I am somewhat familiar with linux but new to Ubuntu so explicit instructions would be greatly appreciated.

Thank you

---

### Post by SOULRiDER on 2007-09-01
Does it happen when GDM loads or when you actually log in?

---

### Post by overdrank on 2007-09-01
> **schneiderman said:**
> Hi all,
I recently installed Ubuntu 7.04 64 bit PC onto my computer and have been having a strange problem. When I try to boot into the GUI, my screen goes into power save mode, as if it had been disconnected from the computer. I can boot into recovery mode with no problems. I have tried several suggestions posted on this site including setting the default driver to vesa, running dpkg-reconfigure xserver-xorg and installing the Nvidia driver with no luck. My system specs

Intel Q6600 quad core
evga GeForce 8800 GTX
Asus Striker Extreme
4 gb ddr2 800 mhz

I am somewhat familiar with linux but new to Ubuntu so explicit instructions would be greatly appreciated.

Thank you

HI and welcome have you seen this thread
[http://ubuntuforums.org/showthread.php?t=524913&highlight=GeForce+8800+GTX](http://ubuntuforums.org/showthread.php?t=524913&highlight=GeForce+8800+GTX)
Hope this helps and good luck!

---

### Post by schneiderman on 2007-09-01
it happens as soon as you choose the option from the dual boot screen. I see the message that the kernel is loading but then the screen goes blank.

---

### Post by SOULRiDER on 2007-09-01
Uhm, maybe theres some power save daemon starting up? Im not sure where daemons are defined in Ubuntu though.

---

### Post by schneiderman on 2007-09-01
> **overdrank said:**
> HI and welcome have you seen this thread
[http://ubuntuforums.org/showthread.php?t=524913&highlight=GeForce+8800+GTX](http://ubuntuforums.org/showthread.php?t=524913&highlight=GeForce+8800+GTX)
Hope this helps and good luck!

I didn't see that thread. I will take a look through it. Thanks a lot.

---

### Post by schneiderman on 2007-09-01
A new update. I can get into the GUI by running
sudo dpkg-reconfigure -phigh xserver-xorg
and resetting the video driver to vesa and the screen resolution to my monitors native resolution. However, after restarting, the screen once again goes into power save mode. I have to do the whole procedure over again to get into the gui.

---

### Post by schneiderman on 2007-09-01
> **schneiderman said:**
> I didn't see that thread. I will take a look through it. Thanks a lot.

Ok, I tried all those suggestions and the problem still persists. I get a message "Failed to start X server" After reading the error output, I get "API mismatch" and "Failed to initialize the NVIDIA kernel module"

In addition, I can no longer access a GUI interface even through recovery mode

---

### Post by arai on 2007-09-01
i have the same problem, yet to be resolved.

the thread is here

[http://ubuntuforums.org/showthread.php?t=539308]("http://ubuntuforums.org/showthread.php?t=539308")

---

### Post by schneiderman on 2007-09-02
OK, I managed to fix my problem. It turns out that usplash was causing the problem. I removed usplash using the command

sudo apt-get remove usplash

my system works fine now a reinstall and running this command. I am going to install the drivers for my card now.

---

### Post by arai on 2007-09-02
> OK, I managed to fix my problem. It turns out that usplash was causing the problem. I removed usplash using the command

sudo apt-get remove usplash

schneiderman, it fixed mine too. thankz.

---

### Post by Johnny M on 2008-01-15
Hi - my screen has just started going into power saving mode - I swopped screens and same thing happened.

Tried to reload ubuntu - feisty but again screen went blank

Any ideas?  hard to put code in with blank screen

Did the children press a wrong button closing down..!?

thanks Johnny

---

