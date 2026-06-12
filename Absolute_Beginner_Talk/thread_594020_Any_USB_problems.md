---
title: "Any USB problems?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by JayeD on 2007-10-27
I've set up a second harddrive on my laptop with ubuntu and have the intention to convert over to linux for daily use and use windows on my laptop and main rig as mainly gaming platforms.

The thing is I work on quite a few pcs, all windows other than my laptop, and carry my data around on a 2GB USB key.

How is the functionality of mounting and unmounting usb keys on linux? Is there anything I should know? Windows has the simple plug it in, unmount it, pull it out. Is it this simple on linux? 

The data is important and used regularly so I need it to be stable. I can back it up but if I need to back it up everytime before I put it into the linux pc then it will really obstruct my work.

TIA

---

### Post by dje on 2007-10-27
USB drives work very well, just plug it in and it mounts automatically with an icon on your desktop and is just like windows to remove them, you right click on the USBs icon on the desktop and select 'Unmount volume' or 'Eject volume'. Alternatively you can open a terminal and do:
```
eject /media/USB DRIVE LABEL
```
obviously replace USB DRIVE LABEL with the actual label of your device (the name of the icon on your desktop). hth ;)

---

### Post by Rinzwind on 2007-10-27
USB sticks work flawlessly for me.
I have 2 "cruzers" and an USB bluetooth dongle for my phone and camera (needed some additional software but after that it worked perfectly).

I am still fighting with my PCCARD Bluetooth (it worked under feisty but I can't seem to retrace what I did for it to get it to work).

---

