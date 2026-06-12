---
title: "Default Boot To OS X"
date: 2009-03-15
forum: Apple Hardware Users
---

### Post by Unix-Man on 2009-03-15
Hello, i just finished getting all the Bugs worked out of my Ubuntu 7.10 and OS X 10.5 dual boot. 

Now when i press my Power Button it boots to Linux. I can still hold Option and boot on the OS X partition but i would prefer it boot to OS X default anybody know how to do this? 


Thanks Unix-Man

---

### Post by cyberdork33 on 2009-03-16
what machine? Intel or PowerPC?

---

### Post by Unix-Man on 2009-03-17
PowerBook G4 15' 1.5Ghz 512 RAM 60GB HD


 PowerBook = Power PC

---

### Post by tiresia on 2009-03-17
You must edit the file /etc/yaboot.conf
```
sudo nano /etc/yaboot.conf
```
After the first block (after the line macosx=...) add the option
```
defaultos=macosx
```
Exit (ctr-X) and say Yes to save the change
Update the bootloader (yaboot) with
```
sudo ybin -v
```
For more info you can read this short howto
[http://ubuntuforums.org/showthread.php?t=994882](http://ubuntuforums.org/showthread.php?t=994882)



Do you need to press Opt to get to MacOSX?
At the first Yaboot prompt, you should get a list of the installed OS's.
If it is not so, post here the file /etc/yaboot.conf

---

