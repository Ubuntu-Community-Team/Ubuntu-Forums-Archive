---
title: "Video Card Error - Getting back to the GUI"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by dpack on 2006-02-13
Running version 5.10.

I had a Matrox AGP video card installed but at random the whole screen would just go black. The monitor never goes into standby mode, it just goes black. The only way out was to kill the power to the machine. I took the Matrox out and installed a ATI Rage PCI video card. Now, when I boot Ubuntu I am booted to the command line interface.

I remember in Mandrake there was a command I could type in and it brought up a config screen where I could tell it what video card to use, what screen resolution to use, and at what color depth. I'd like to know if Ubuntu has a similar command? Or is there another way I can get Ubuntu to detect and configre the ATI card I have installed so I can get the GUI back.

---

### Post by o_fortuna on 2006-02-13
[QUOTE=dpack]Running version 5.10.

I had a Matrox AGP video card installed but at random the whole screen would just go black. The monitor never goes into standby mode, it just goes black. The only way out was to kill the power to the machine. I took the Matrox out and installed a ATI Rage PCI video card. Now, when I boot Ubuntu I am booted to the command line interface.

I remember in Mandrake there was a command I could type in and it brought up a config screen where I could tell it what video card to use, what screen resolution to use, and at what color depth. I'd like to know if Ubuntu has a similar command? Or is there another way I can get Ubuntu to detect and configre the ATI card I have installed so I can get the GUI back.[/QUOTE]
Try to type this into the terminal:
```
sudo dpkg-reconfigure xserver-xorg
```
This should help you find the right card. (You'll have to answer a lot of questions too; don't worry, read carefully and accept the default).

---

### Post by dpack on 2006-02-14
Thanks man! I'm back in business now. Saving this snippet of code for future reference!

---

### Post by amopresunto on 2006-02-15
Thank you for the post.  I had a similar issue - my old Nvidia card was failing, so I replaced it with a new ATI Radeon 7000.  I had an existing install of Breezy Badger.  After the card change, Ubuntu was not booting properly due to the card change.

Thanks to your advice, I booted in Recovery Mode, logged on as root, then entered the "dpkg-reconfigure xserver-xorg" command.  (I did not have to do the 'sudo' because I was already logged on as root.)

Thanks for your expert advice.  My system is now up and running with the new card.

---

