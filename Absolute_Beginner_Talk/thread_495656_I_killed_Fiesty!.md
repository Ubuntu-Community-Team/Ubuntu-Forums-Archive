---
title: "I killed Fiesty!"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Mr_Bond_UK on 2007-07-08
Afternoon, all,
  Right im my infinate wisdom i decided to uninstalkl the restricted driver for my graphics card in fiesty
Now im not getting any GUI. Ive got an ATI 9500. How do i get the driver back on?

---

### Post by starcraft.man on 2007-07-08
> **Mr_Bond_UK said:**
> Afternoon, all,
  Right I'm my infinite wisdom i decided to uninstall the restricted driver for my graphics card in fiesty
Now I'm not getting any GUI. Ive got an ATI 9500. How do i get the driver back on?

Ok, easy fix. Follow along and I'll guide ya through an easy fix. :)

1) Reboot the machine and at the GRUB menu (where you see the kernels) pick to boot recovery mode, should be second option.

2) When ya get to the screen you'll be logged in as root. Now enter this:

```
sudo nano /etc/X11/xorg.conf
```

3) The nano editor will pop up, its just a text editor that works in the terminal. Scroll down the pages with the 4 arrow keys of your keyboard. Find this section:

Section "Device"
    Identifier     "nVidia Corporation NV40 [GeForce 6800 GT]"
    Driver         [COLOR="Blue"]"nvidia"[/COLOR]
......
EndSection

In your case the driver/card will read ATI. Change this entry to [COLOR="Blue"]"vesa"[/COLOR] please. Vesa of course are the very generic drivers that work with almost anything, when in doubt you can always use them.

4) With change made, push Ctrl + O to save then push enter to save over the original (the little entry asks you where to save, by default it is the original destination). Push Ctrl + X to exit the editor.

5) Now reboot the machine with this command and boot normally:

```
sudo reboot
```

6) Lastly, reinstall drivers as you did before and please don't remove them unless you edit your driver in future.

For more on the terminal, [Linux Command]("http://www.linuxcommand.org/"). If you got any questions, feel free :).

---

### Post by luisromangz on 2007-07-08
Yes, you should fall back to the vesa drivers as the previous poster said, but there is no need to reboot the system, you can simply use startx in the command line to see if everything is working fine.

---

### Post by starcraft.man on 2007-07-08
> **luisromangz said:**
> Yes, you should fall back to the vesa drivers as the previous poster said, but there is no need to reboot the system, you can simply use startx in the command line to see if everything is working fine.

I know, I just have this strange preference to recommend rebooting instead, I dunno why :p. So ya, whichever you prefer Mr. Bond.

---

### Post by Mr_Bond_UK on 2007-07-08
Right, just tried that, but there is no /etc/X11/xorg.conf

any other ideas?

---

### Post by mikewhatever on 2007-07-08
:twisted:When is the funeral?

---

### Post by Mr_Bond_UK on 2007-07-08
Was thinking a week tuesday

---

### Post by masterd on 2007-07-08
Try to install the driver directly from the console with
 ```
sudo apt-get install xorg-driver-fglrx
```

This installs the binary driver for ATI cards and supports hardware accelerated OpenGL.. I think this is one one you deleted..

---

