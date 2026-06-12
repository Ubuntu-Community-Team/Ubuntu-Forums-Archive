---
title: "Live CD?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Nekiruhs on 2007-05-10
Currently, as my laptop is utterly broken (HD issues not software) I have to run from Live CD to do anything.  Is there a way to make a Custom Xubuntu 7.04 live CD with OpenOffice and Wine? And maybe some of the Games that came with the Gnome CD (Tetravex, Majhonng, Chess, and Sudoku mostly.)

---

### Post by Najand on 2007-05-10
Have a look at:
[http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm](http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm)

---

### Post by jerrylamos on 2007-05-10
What I've done is run CD Live "persistent" with a USB pen drive at least 1 gb.
The drive needs to be formatted ext3, use Gparted for that from System,Administration or download the Gparted from Applications, Add/Remove.  Select the little arrow box in the upper right corner to get your USB drive, unmount it, and format it ext3.  Exit Gparted.
Do Applications, Terminal, e2label /dev/sd?? casper-rw
where sd?? is whatever Gparted saw as a device address

Then reboot CD Live, pushing F6 and adding "persistent" like so:
.... quiet splash persistent

At this point you can install packages, save files, etc. and they will be on your combination of CD Live and USB pen drive so long as you boot "persistent".

Now this works fine for Edgy and Dapper it's busted on Feisty so far.

It takes longer to boot, but once up on some of my systems I forget it's running CD Live "persistent" because it feels like a hard drive install.

Cheers, Jerry

---

### Post by Nekiruhs on 2007-05-10
Thank you Jerrylamos, thats even better than what I was looking for!

---

### Post by Nekiruhs on 2007-05-10
Hmm, all went well until I tried the e2label command:
```
administrator@KBUNTU:~$ e2label /dev/sdf casper -rw
Usage: e2label device [newlabel]
administrator@KBUNTU:~$ e2label /dev/sdf casper-rw
e2label: Bad magic number in super-block while trying to open /dev/sdf
Couldn't find valid filesystem superblock.
```

---

### Post by Nekiruhs on 2007-05-10
Any help???

---

### Post by Najand on 2007-05-10
The flash disk must be formatted as ext3

---

