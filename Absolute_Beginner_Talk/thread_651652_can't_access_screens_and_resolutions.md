---
title: "can't access screens and resolutions"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by catos_minion on 2007-12-27
just installed 7.10. Can not access Screens and graphics to change the resolution. also i'm using dual monitors. I have an nVidia g-force 6 card. it is set to mirror the default monitor. that works, but even when i could get to the screens and graphics window, i couldn't get the second monitor to show anything but the mirror setting.:confused:

---

### Post by spiderbatdad on 2007-12-27
its actually an application called displayconfig-gtk in synaptic. idk if it is installed by default

---

### Post by catos_minion on 2007-12-27
thank you for your help. i've reinstalled displayconfig-gtk in synaptic and still can not access screens and graphics. any other ideas?

---

### Post by spiderbatdad on 2007-12-27
do you mean the application doesn't exist under System>>Administration>>Screens and Graphics?  or when you click it nothing happens?

---

### Post by catos_minion on 2007-12-27
when I click it, nothing happens....

---

### Post by spiderbatdad on 2007-12-27
you should be prompted for a password. I'm wondering if you are logged in as a user other than admin.

---

### Post by catos_minion on 2007-12-27
actually, after a reboot, it does ask for the password. then nothing happens... and each time i try after that, i don't get the password request either. unless i reboot again.

---

### Post by spiderbatdad on 2007-12-27
I guess what I'm trying to ask is: are you the admin of this system?  Is auto-login enabled?
Or are you logged in as an adduser under. Look into system>>administration>>Users and groups...highlight your name and select properties...then choose the privileges tab.

---

### Post by catos_minion on 2007-12-27
Administer the system is checked. i don't see anything about auto log in. is there somwhere else i should be looking? this is all very new to me. only been in ubuntu for about 20 hours now.

---

### Post by spiderbatdad on 2007-12-27
You would have had to intentional set auto-login so...idk what's going on. I'm wondering if the driver for your graphics card is not being detected...which screens and resoulutions obviously uses. Have you looked in the restricted drivers manager to see that it is all set? also maybe post the output of ```
sudo lshw -C Video
``` if you don't mind.

---

### Post by catos_minion on 2007-12-27
*-display               
       description: VGA compatible controller
       product: NV44 [GeForce 6200 TurboCache(TM)]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

---

### Post by jken146 on 2007-12-27
Type ```
gksu displayconfig-gtk
``` in a terminal and post the output please.

---

### Post by spiderbatdad on 2007-12-27
here's a screenshot of an nvidia tool in synaptic. There are also some driver improvements, but they are mostly for gl rendering. I'm sorry I'm out of ideas.

---

### Post by catos_minion on 2007-12-27
Hello, i have done the following: 
"to reconfigure your X server. You can do that by booting your machine to recovery mode from GRUB menu. Then at the prompt, type dpkg-reconfigure -phigh xserver-xorg Then, reboot with: shutdown -r now....

I am now able to access the screen and graphics window again. but the drivers for the nVidia card are no longer there.
so everything does look better, but i know i need those drivers and i'm not sure how to proceed without running into the same problem again.

thanks again for your help!:)

---

### Post by jken146 on 2007-12-27
```
dpkg-reconfigure xserver-xorg
``` without the -phigh option will let you choose the nvidia driver.

---

### Post by catos_minion on 2007-12-27
whoops.. sorry.. i thought i'd sent this earlier when you asked for it:
  *-display               
       description: VGA compatible controller
       product: NV44 [GeForce 6200 TurboCache(TM)]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

---

### Post by catos_minion on 2007-12-28
thanks again for all your help. greatly appreciated...

---

### Post by catos_minion on 2007-12-28
thanks again for all your help. greatly appreciated...

---

