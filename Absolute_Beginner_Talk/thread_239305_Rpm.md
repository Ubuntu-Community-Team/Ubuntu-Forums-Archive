---
title: "Rpm"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by Niloc on 2006-08-19
I downloaded a driver for my printer (Canon LBP 1210) and the zip file contains two 'RPM' files which look like the driver. How do I extract the driver from an RPM file? It seems it is a Red Hat corporate library file but there must be a Ubuntu fix!

---

### Post by aysiu on 2006-08-19
Let's say the RPMs are on your desktop. Paste these commands into the terminal: ```
sudo aptitude update
sudo aptitude install alien
cd ~/Desktop
sudo alien -i *.rpm
```

---

### Post by Niloc on 2006-08-19
Thank you asui, it seems to have worked except where it tried to access the internet which failed because I am still using the Windows machine to do that....

My problem is now that I have placed the RPM files in a folder called 'Canon Printer Driver' and I cannot get to change to that folder, it must be the spaces in the folder name....

---

### Post by Niloc on 2006-08-19
Well it didn't do much good, I followed Aysiu's instructions and all seemed to go well except the printer didn't appear in the 'Printer Connection' screen so the system doesn't seem to be aware of it, I tried another but I am using the USB port so nothing happened, at least you get something with a parallel port even if it is garbage...
There must be some way of getting it working!!

---

### Post by aysiu on 2006-08-19
Unfortunately, I don't know much about printer driver installation, as my printer was autodetected.

All I know is installing RPMs...

**Edit**: [It's not looking good for that printer and Ubuntu](http://lists.freestandards.org/pipermail/printing-user-canon/2005/002223.html).

---

### Post by taurus on 2006-08-19
> **Niloc said:**
> 
My problem is now that I have placed the RPM files in a folder called 'Canon Printer Driver' and I cannot get to change to that folder, it must be the spaces in the folder name....
Try

```

cd "Canon Printer Driver"
-or-
cd Canon\ Printer\ Driver

```

---

