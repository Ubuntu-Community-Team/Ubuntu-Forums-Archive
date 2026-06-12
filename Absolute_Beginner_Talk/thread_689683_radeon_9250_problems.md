---
title: "radeon 9250 problems"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by sewercake on 2008-02-06
Hello, I have a computer, running 7.10, and my radeon 9250 card does not seem to work. Right now I am running on integrated graphics, and have no idea how to change that, could anyone help?
I honestly do not know where to start
thanks for the help,



-Sewercake

---

### Post by petersonjacob on 2008-02-06
yeah im thinking your post is showing when you turn the computer on, but then it goes away when ubuntu starts, in that case use your integrated grafix and install a program called envy (google it) and install the latest ati driver, then reboot your computer into recovery mode and type this:

dpkg-reconfigure xserver-xorg

and select the ati driver, it will probably be obvious so look through the list, then keep pressing enter and DONT CHANGE ANYTHING AFTER THIS and once you are back at the terminal type halt or shutdown or whatever to SAFELY shutdown your computer, switch the dvi/vga cable to the dedicated card and try again

if this doesnt work, try disabling the integrated graphics from the boot menu

---

### Post by OffAxis on 2008-02-06
you should start by setting the AGP (or PCI if that's the slot style) as the Primary type in the CMOS setup.
To get there, reboot and hit the 'Delete' key within the first few seconds there of the startup (right after the POST)

---

### Post by petersonjacob on 2008-02-06
Offaxis is right but do that AFTER you reboot so make the agp or pci express slot primary AFTER installing the driver

---

### Post by ddk13 on 2008-02-07
I am having the same problem, however i have windows on one hard drive and ubuntu 7.10 on the other.  I installed the radeon 9250  recently and now i can't load ubuntu.  I have the mythbuntu live cd  i would like to install over my ubuntu but i can't do it.  the live cd starts mythbuntu and i select start or install mythbuntu but then nothing happens.  The start screen shows the green bar going from left to right and when it should be loaded and starting it freezes.

---

