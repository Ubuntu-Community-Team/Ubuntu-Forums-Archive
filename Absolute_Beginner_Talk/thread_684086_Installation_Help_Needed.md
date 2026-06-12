---
title: "Installation Help Needed"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by foolio2000 on 2008-01-31
Hi, I made my own Ubuntu 7.10 installation cd burned the image and everything. I can get to the "start-up" screen, but once I click on an option, such as install Ubuntu, the screen goes black and the monitor stops receiving signals.

Using an old 6.06 cd I had lying around I managed to find that the problem was that it was having problems with the video card (XFX GeForce 8400 GS). Any info would be much appreciated. Thank you.

---

### Post by PinkFloyd102489 on 2008-01-31
Try loading the CD in safe graphics mode.

Or if you want, try to alternate CD. Fairly easy to use in my opinion. I used it on my very first install since both of my computers are extremely slow. No point and click, but it's still simple.

---

### Post by Therion on 2008-01-31
When booting form the LiveCD, press F6 for "Other Options" and then delete the words "quiet" and "splash" using the backspace key from the lines of code you'll see.

Press Enter to continue to load the LiveCD and do the install.

Reboot.

When you reboot, you'll need to edit a line in the menu.lst file from this:

kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=c857bb7e-3a7a-414b-9c2d-a25b7c8da565 ro **quiet splash**

To this:

kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=c857bb7e-3a7a-414b-9c2d-a25b7c8da565 ro

Using this line of code in the Terminal:

```
sudo gedit /boot/grub/menu.lst
```

Then I would suggest using [ Envy](http://albertomilone.com/nvidia_scripts1.html)  to install the proper nVidia driver.

---

### Post by foolio2000 on 2008-01-31
Thank you both for your replies.

Starting it in graphics safe mode did not work however.

The other way, I went into "other options" deleted quiet splash and pressed enter. I do not know what was supposed to happen but it went through a bunch of processes and never stopped. When I reboot quiet splash was back in the "other options".

---

