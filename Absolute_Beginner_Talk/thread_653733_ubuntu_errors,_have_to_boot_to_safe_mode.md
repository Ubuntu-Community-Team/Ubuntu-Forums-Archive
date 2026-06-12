---
title: "ubuntu errors, have to boot to safe mode"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by steve_sandy on 2007-12-30
Downloaded the 7.10 iso to HDD, then burnt to CD

Booted with it, sometimes it booted right into the ubuntu desktop and could find my sata drives, at other times I get errors like:

(Initramfs) [   68.416638] USB 1-1: Device not accepting address 2, error -71

Searched for this, but not make much sense, often a reboot worked. Installed it on a slave drive and got stuck at 90%, so gave up on it. Tried it this morning and was in safe mode as normal boot dumped me into dos with the above error and lots of help options and nothing else :(

Tried to reinstall the package, it stuck at 46% for an hour, so gave up on it. Rebooted into XP to find I had no net connection as the ethernet cable was unplugged, check it had been put back in ok and rebooted, same result, since it was plugged in could not understand it

First system restore ie before starting the install and still not working, second system restore from yesterday and still borked. Got a laptop which confirmed the connector was fine, ie laptop got online ok

Powered off totally and unplugged the linux slave drive - had tried to format it with partition magic which had recognised it, but could not find it any more, despite the linux cd finding it ok

XP now works...

Might try it again, using a usb razer mouse, got a ps2 plugged in and a ps2 keyboard, plus printer etc on usb

any suggestions ?

the linux drive was a 10 GB and 27 GB partition but Linux reported it as one drive, originally it set itself up as ext3 and swap it that means much, is it better to keep as 2 partitions or merge into single partition ?

system specs:-
Asrock Mobo K7VT4A PRO
160 GB IDE boot drive (2 partitions)
2x 150 GB SATA 1 drives
1x 40 GB IDE slave drive for linux

Nvidia Geforce 7600 GT, 256 MB AGP card
razer mouse
2 x 1 GB DDR333 Ram

---

### Post by blueridgedog on 2007-12-30
Initramfs is attempting to create a file system in memory that is mounted.  I would boot on the Ubuntu CD and run the memory test option.

Given the "funky" state of your ethernet cable, you may want to pull a fresh ISO and burn it as well.

---

