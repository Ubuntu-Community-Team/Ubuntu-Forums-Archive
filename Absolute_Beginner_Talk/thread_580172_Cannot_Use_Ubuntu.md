---
title: "Cannot Use Ubuntu"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by darkforce898 on 2007-10-18
Ok, I have just decided to put Ubuntu on my computer to dual boot with Windows XP. I made a new partition of 30gigs and downloaded Ubuntu 7.10 64bit. I also have on cd 7.04 normal and 5.1 Install. Here is where the first problem happens.

I boot into the Ubuntu Install CD and choose the first install and the screen flashes and the monitor looses signal. It sits there forever, the computer doesn't turn off and the drive doesn't stop spinning. I tried it in safe graphics mode and it does the same thing. Version 7.04 normal does the same thing.

So the next thing I did was try to install 5.1. It worked and went through the install and I was happy. It rebooted and installed and configured everything and all was well in the world. Until it tried to get to the login screen. I got an xerver error and was dumped back to command line. I figured that this might be the problem with what was happening on the new install so I tried to fix it on 5.1. I did by doing "sudo dpkg-reconfigure xserver-xorg" and choosing the VESA driver instead of ATI. I rebooted the GDM and I managed to get into Ubuntu, YEY!

After having found a fix for 5.1 I tried to apply this to a 7.04 install so I downloaded the alternate cd. I installed with the text installer without a hitch. Rebooted and chose the Ubuntu Normal and it did the same thing as it did during the install, flashed and lost signal. So I booted into the recovery mode to try that command line fix that worked for 5.1.

It booted to the command line and I was excited to try the fix but my keyboard wasn't working. I have a USB Compaq Multimedia Keyboard. I unplugged it and plugged it back in and I got this error, "usb 1-1: device descriptor read/all, error -62". I went and got a PS/2 keyboard and it worked so I did "sudo dpkg-reconfigure xserver-xorg" and configured it. Again I got my hopes dashed when I tried to log in and got the same problem.

Can anyone help me here?

---

### Post by chuckyp on 2007-10-18
What type of ati card do you have?  If you don't know lspci in a terminal will tell you.

---

### Post by darkforce898 on 2007-10-18
I have an ATI Radeon x800 GT

I just tried installing 7.10 with the alternate CD and my keyboard wouldn't work in the menus.

---

### Post by darkforce898 on 2007-10-18
Bump?

---

### Post by Hobo Joe on 2007-10-18
In the alternate install CD it asks a lot of questions about the keyboard, are you sure you answered them all right?

---

