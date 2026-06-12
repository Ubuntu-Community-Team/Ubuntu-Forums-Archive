---
title: "Change the boot screen"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by Lanc1988 on 2007-12-15
I have installed ubuntu 7.10 on my computer, vista is on one hard drive and ubuntu is on another. I noticed that ubuntu pretty much made it the default OS so it always loads when I restart, which is fine for me. But I want to install ubuntu 7.10 on my family computer also. It also has two hard drives, one has vista on it now and the other is empty but when I install ubuntu on the empty one it is going to always boot ubuntu by default.

So how can I edit the boot screen order so that vista will be the default OS. Also is there a way to change the timeout time?

---

### Post by taurus on 2007-12-15
You can change the boot order from Ubuntu to windows in /boot/grub/menu.lst.

```
gksudo gedit /boot/grub/menu.lst
```
I believe right now the **default** is set to 0 so you need to change it to 3 or whatever the entry for your windows is.  Remember, you count each _title_ as 1 and you start counting from 0.

---

### Post by wormser on 2007-12-15
The /boot/grub/menu.lst file has the options you want to edit.

```
gksudo gedit /boot/grub/menu.lst
```

To change the time out edit this section.

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10
```

Edit the following section for default boot.  You will have to go to the bottom of the file where the different boot options are.  Starting at 0 count to the one you want to boot.  Put that number where the default is now 0.

> # You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0


---

### Post by Lanc1988 on 2007-12-15
Ok, so I have three ubuntu ones.. do they all count as 1 or is each one separate which would mean that the vista is considered '3'?

also.. if i want to change the order that they are listed in can I just cut and paste the windows vista one to before the ubuntu ones?

and finally.. can i either delete or hide the ubuntu recovery mode and memtest entries? just want to try to keep things simple since its on a family computer.

---

### Post by taurus on 2007-12-15
Each _title_ is counted as 1.  So if windows is the fourth one, then you would put 3 in the default option at the top to have windows boot automatically after an amount of time.

And if you want to hide both recovery mode and memtest+, just put a # in front of those lines including the titles.  But if you do that, then windows would now become 1 since you would have only two entries, one for Ubuntu and one for windows.

```
default   1
```

---

### Post by Lanc1988 on 2007-12-15
ok, thanks for all the help

---

