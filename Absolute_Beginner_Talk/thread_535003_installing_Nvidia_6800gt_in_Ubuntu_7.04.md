---
title: "installing Nvidia 6800gt in Ubuntu 7.04"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by dnagorcka on 2007-08-25
Struggling to install drivers for nvidia 6800GT with feisty fawn on core2 pc with 2g ram.
I've followed Alberto Milones guide to manual installation after using Envy failed, all goes well untill rebooting when xserver simply wont work and im taken to a command prompt.
reinstalling the backup xorg.conf and using the NV driver is all i know how to do.
Please help dont want to be forced back on to windows!

---

### Post by nonewmsgs on 2007-08-25
instead of using NV use nvidia.  do you know how to adjust xorg.conf or start the wizard?

to start the wizard
sudo dpkg-reconfigure -phigh xserver-xorg

you might have to do a 
cd /etc/X11 
first but im not sure

---

### Post by Bout to Snap on 2007-08-25
> **dnagorcka said:**
> Struggling to install drivers for nvidia 6800GT with feisty fawn on core2 pc with 2g ram.
I've followed Alberto Milones guide to manual installation after using Envy failed, all goes well untill rebooting when xserver simply wont work and im taken to a command prompt.
reinstalling the backup xorg.conf and using the NV driver is all i know how to do.
Please help dont want to be forced back on to windows!

I'm having the same prob,but with a much older card i just wanted to test out before i ran out to by a new Nvidia Card for Ubuntu Needless to say i have not found a solution either I cant seem to get the 3D acceleration going for cedega anyhow i hope i dont have to go back to windows either starting to miss my games though.

---

### Post by nonewmsgs on 2007-08-26
bout to snap is your problem only with cadega? are you using a nvidia card?  are you using the proprietary drivers?

---

### Post by ragespot on 2007-08-26
me too got tha same problem with the 6800gt. its look like the driver doesn't not see the card.

please be sure to use a nvidia gpu error.

---

### Post by soaro77 on 2007-10-15
I'm having the same problem with an Nvidia 6800GT. I have tried everything I can think of. I've tried the stock Ubuntu nvidia-glx drivers. I've tried the nvidia-glx-dev drivers. I've tried envy. I had envy remove the old drivers and install the new ones. I removed that . (dot) file in the /lib/linux-restricted-drivers directory that is put and left there from the nvidia-glx-dev install. I have enabled nvidia in the xorg.conf file.

And I still get the blue screen that says my driver doesn't match the kernel version or something to that effect. The only way I can get back into X is to comment out nvidia in xorg.conf and uncomment nv.

I don't know what else to try at this point. I'm so frustrated that I'm about ready to trash this video card go buy a brand new card. But i really shouldn't have to do that. This card is a very good card still and very much should be able to run compiz fusion.

Anyone have any other ideas of what I can try to get the restricted drivers to work with this card?

---

### Post by ragespot on 2007-10-15
Now the new nvidia drivers is working with my GPU
I dont know if ubuntu update they nvidia drivers but the one at [www.nvidia.com](www.nvidia.com)  is working for me now.

---

