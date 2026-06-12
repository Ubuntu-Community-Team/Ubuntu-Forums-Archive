---
title: "Nvidea problem"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by SMFS_Usagi on 2007-11-16
I just installed Ubuntu as a secondary operating system on my computer.  The windows works fine so I know that the hardware is ok.  When I bootUbuntu  it  starts ok then the screen gets a lot of blinking colored blocks and I hear a beep which I suspect means that it has booted.  Of course I cannot do anything unless I reboot and go into recover mode.  That boots and works.

So I believe it's a driver problem.  My video card is a Nvidia GeForce4  TI 4200 w/ AGP 8X.  Can anyone help me please?

Usagi

---

### Post by overdrank on 2007-11-16
> **SMFS_Usagi said:**
> I just installed Ubuntu as a secondary operating system on my computer.  The windows works fine so I know that the hardware is ok.  When I bootUbuntu  it  starts ok then the screen gets a lot of blinking colored blocks and I hear a beep which I suspect means that it has booted.  Of course I cannot do anything unless I reboot and go into recover mode.  That boots and works.

So I believe it's a driver problem.  My video card is a Nvidia GeForce4  TI 4200 w/ AGP 8X.  Can anyone help me please?

Usagi

Hi when you boot into recovery mode.enter this command in the terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete reboot  Hope this helps and good luck!

---

### Post by jryprt on 2007-11-16
> **SMFS_Usagi said:**
> I just installed Ubuntu as a secondary operating system on my computer.  The windows works fine so I know that the hardware is ok.  When I bootUbuntu  it  starts ok then the screen gets a lot of blinking colored blocks and I hear a beep which I suspect means that it has booted.  Of course I cannot do anything unless I reboot and go into recover mode.  That boots and works.

So I believe it's a driver problem.  My video card is a Nvidia GeForce4  TI 4200 w/ AGP 8X.  Can anyone help me please?

Usagi

If you have no command line:  Ctrl+Alt+F1 to get a command line.
sudo dpkg-reconfigure xserver-xorg  it will go into a setup most of 
it will be keyboard & stuff when it ask about video drivers use VESA 
There is some info. about sudo dpkg-reconfigure xserver-xorg 
here  [http://ubuntuforums.org/showthread.php?t=568105](http://ubuntuforums.org/showthread.php?t=568105)

---

### Post by SMFS_Usagi on 2007-11-16
I did this:
> sudo dpkg-reconfigure xserver-xorg 
And changed it to vesa.  Now I get a black screen that quickly goes into power-saver mode

Usagi

---

### Post by SMFS_Usagi on 2007-11-16
I did this:
> sudo dpkg-reconfigure xserver-xorg 
Now I get a black screen that quickly goes into power-saver mode

I found here:[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)
that my card, Nvidia GeForce4 TI 4200
is not supported.

What does this mean and now what ?

Usagi

---

