---
title: "Determining 3d video"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by robertjastrow on 2007-08-25
How do i determine what video driver is installed/if my video is installed correctly.  I have a ATI Xpress 200m video card and every thing seems to work fine in Ubuntu, but some games that work fine in Suse run very slow in Ubuntu (i.e. Chromium).  Apparently 3d is installed because the 3d games launch, but the performance is odd.

---

### Post by RomeReactor on 2007-08-25
Hi. To find out which video driver you're currently using, open a terminal (Applications->Accessories->Terminal) and enter this:
```
sudo lshw -C display
```
look in the last part (configuration: driver=**x**). To see if you have direct rendering enabled, enter this:
```
glxinfo | grep rendering
```
if it says "No", that would explain the slowness.

---

### Post by robertjastrow on 2007-08-25
Apparently rendering is not enabled (as seen below).  As well I donot see a configuration: driver=x line as well.  Not sure if the lack of the configuration: driver=x is a direct problem.  If not how do I enable rendering?  If it is, how do I fix and then enable rendering?

Thanks.....

_____________________________________________________
user@computer:~$ sudo lshw -C display
Password:
  *-display               
       description: VGA compatible controller
       product: ATI Radeon XPRESS 200M 5955 (PCIE)
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@01:05.0
       version: 00
       size: 256MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       configuration: latency=66 mingnt=8
       resources: iomemory:c0000000-cfffffff ioport:9000-90ff iomemory:b0100000-b010ffff irq:10
user@computer:~$ glxinfo | grep rendering
direct rendering: No
user@computer:~$ 
________________________________________________

---

### Post by nosrednaekim on 2007-08-25
You need to get the fglrx driver.

---

### Post by RomeReactor on 2007-08-25
Read these stickies ([1]("http://ubuntuforums.org/showthread.php?t=414194"), [2]("http://ubuntuforums.org/showthread.php?t=515573"), [3]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")), or try [this thread]("http://ubuntuforums.org/showthread.php?t=204910&highlight=ATI+Xpress+200m") which apparently works for your specific model. Also, try searching the [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=138") section for your card (ATI Xpress 200m).

However, I don't have an ATI card, so you should probably wait for someone who actually uses one to explain to you how to install and enable the drivers.

---

### Post by robertjastrow on 2007-08-26
Thanks for all the help.  Got it working with the directions and assistance supplied.

Love this forum, ya'll are great.

---

