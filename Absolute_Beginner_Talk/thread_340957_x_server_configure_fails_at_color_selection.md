---
title: "x server configure fails at color selection"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by eshen on 2007-01-17
Hi everyone first post :D 
anyway I am trying to install ubuntu 6.06 and it gave me  the graphical error message. So look online and find what i have to do ```
sudo dpkg-reconfigure xserver-xorg
``` and it sems to work... Until i have to select color depth (or something like that, I have a bad memory) where I have to pick 24 bit 16 bit, and so on I chooose 24 bit and it shows the terminal (I think thats what it's called I'm new, remember?) at the bottom I can't see what i am typing but I can see something like an error (Remember I have a terrible memory. I'll go back and do it again to see the error and write it down and post later) so I try again and choose 16 bit... nothing ](*,). So I am asking you, how do to fix this error?

---

### Post by eshen on 2007-01-18
Ok here is the error ```
xserver-xorg postinst warning overwriting possibly-customised configuration file; backup in /etc/x11/xorg.conf.2996911725531
```

---

### Post by chick penguin on 2007-01-18
I am new as well and having similar problems. Here is a thread that may have some infor for you. 
Re: broken xserver-xorg
[http://www.ubuntuforums.org/showthread.php?t=340081](http://www.ubuntuforums.org/showthread.php?t=340081)

you might try the command as noted in that thread:
sudo /etc/init.d/gdm restart
after you have selected the bit depth. I was having the same problem at the same point. I can also only see half a line.
Perhaps you might get a few ideas from the thread. 
Welcome to the forum.

---

### Post by riven0 on 2007-01-18
> **eshen said:**
> Ok here is the error ```
xserver-xorg postinst warning overwriting possibly-customised configuration file; backup in /etc/x11/xorg.conf.2996911725531
```

:lol: I don't know why everyone assumes that's an error message. It's quite normal; xserver is just telling you it's making a backup of your old xorg.conf before replacing it. So just go ahead an choose 16bit, and then reboot with **sudo shutdown -r now**

---

### Post by eshen on 2007-01-18
> **riven0 said:**
> :lol: I don't know why everyone assumes that's an error message. It's quite normal; xserver is just telling you it's making a backup of your old xorg.conf before replacing it. So just go ahead an choose 16bit, and then reboot with **sudo shutdown -r now**
:D Thanks I'll try that now and get back to you.

---

### Post by eshen on 2007-01-18
It's still not working It gives ne the x-server error.

---

### Post by riven0 on 2007-01-18
Alright, when you did the reconfiguration, did you leave the memory option blank for autodetection? And did you let it autodetect the Hz and vertical refresh rate, instead of putting in your own values? 

Oh, and what kind of graphics card do you have?

---

### Post by eshen on 2007-01-18
Yes those where auto detected. ATI RADEON X800 XL.

---

### Post by riven0 on 2007-01-18
Okay, when you do the reconfiguration this time, try choosing **Vesa** as your graphics driver and see if it makes any difference. This is just to try to get your graphical display up and running. If it works, we can try installing the official drivers for your card.

---

### Post by eshen on 2007-01-18
Ok i'll get right on that. Thanks for being helpful :D

---

### Post by eshen on 2007-01-18
*sigh* It still isn't working.

---

### Post by riven0 on 2007-01-18
Alright, so as a last option, let's try re-installing the xserver and then the official drivers. So, at terminal type this:

> sudo apt-get install --reinstall xserver-xorg

Then, try: **startx**

If it still gives you an error, let's continue with the official driver. Make sure you've got the commercial repositories enabled. Then do this:

> sudo apt-get install xorg-driver-fglrx

And then:

> sudo aticonfig --initial

And, finally:

> sudo aticonfig --overlay-type=Xv

Then do the reboot: **sudo shutdown -r now**

BTW, is xserver giving you any specific message? Something related to XGL, maybe?

---

### Post by eshen on 2007-01-18
It does not give me anything related to xgl.
I tried```
sudo apt-get install --reinstall xserver-xorg
``` but i couldnt connect to the internet.:confused:

---

### Post by riven0 on 2007-01-18
> **eshen said:**
> It does not give me anything related to xgl.
I tried```
sudo apt-get install --reinstall xserver-xorg
``` but i couldnt connect to the internet.:confused:

:neutral: Uh oh, not connected? Can you try:

> dig google.com

And see what your results are? Were you able to get on the net before? Also, you don't happen to have a Broadcom wireless card, do you?

---

### Post by eshen on 2007-01-18
I'l get on that after I take some Alka-Seltzer (My stomache hurts). Oh and I do not have a Broadcom wireless card.

---

