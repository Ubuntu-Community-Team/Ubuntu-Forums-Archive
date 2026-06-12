---
title: "Install Freezes"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Trank07 on 2007-10-26
I am trying to install Gutsy on a unused hard drive in my computer and dual boot vista and ubuntu.  But when I boot from the CD-Rom, it loads and then I select "Install Ubuntu" then another window pops up and loads the kernel. It is the scree after that with "Ubuntu" at the top and a loading bar is where it freezes.

System Specs:

Gigabyte 965P-DS3
Intel Core2 CPU 6400 @ 2.3GHz
4.00 GB Memory
NVIDIA GeForce 8800 GTS

---

### Post by jualin on 2007-10-26
try the option of "Check CD for defects" and also, try the option of the "Safe Graphics mode". When I tried to install Gutsy last week, my computer would not load the live cd unless I would use the Safe Graphics option. Also, other times I have tried to install Ubuntu if the CD has any scratches or dust the loading bar would freeze. However after burning Ubuntu in a new Cd the problem would go away. Hope it helps.

---

### Post by Trank07 on 2007-10-26
It is a new CD and I used it to install Ubuntu on my mac and it worked just fine, so I would assume it is a hardware issue with my desktop.

---

### Post by Trank07 on 2007-10-27
Downloaded the alternate desktop .iso and tried it but the install hangs after i select "Install in text-line mode" with a cursor flashing in the corner.

---

### Post by Drool Thingy on 2007-10-28
I had a similar problem due to a conflict with my integrated Intel graphics hardware and my nVidia card even though the onboard video had been disabled.  If this setup sounds similar to yours, you might need to  re-enable your onboard video, install Ubuntu using that, and then boot up Ubuntu from your harddisk to make the changes you'll need to get your other grafx card working.

After booting go into the directory /etc/X11 and load the xorg.conf file (make a backup!).  Edit the videocard section of your xorg.conf file so that the driver is "vesa" and put a hashmark (#) in front of the PCIbus statement for your current videocard.

After doing that add these two lines to the bottom of the file "blacklist" which is located in the /etc/modprobe.d folder

blacklist agpgart
blacklist intel_agp

save the file and reboot.  Change back to your non-integrated video card and Ubuntu should boot.

---

