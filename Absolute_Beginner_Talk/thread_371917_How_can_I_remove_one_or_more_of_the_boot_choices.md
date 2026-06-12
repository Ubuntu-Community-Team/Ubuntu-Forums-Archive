---
title: "How can I remove one or more of the boot choices ?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by almasry on 2007-02-27
How can I  edit the boot screen in Ubuntu to remove one or two of the choices ,,, say , i want to remove the "Other booting system from the boot screen " to hide  my XP from the boot loader ...
How can I do this  ? , I think there is some file like boot.ini in IS ..
thanks in advance

---

### Post by Quillz on 2007-02-27
You edit the GRUB file, which is in /boot/grub, IIRC.

---

### Post by aidanr on 2007-02-27
/boot/grub/menu.lst

---

### Post by TonKi on 2007-02-27
It is /boot/grub/menu.lst

To remove kernel lines, remove the kernel in your package manager

---

### Post by almasry on 2007-02-27
thank u guys 
But what do u mean by removing kernel lines 
I have 4 lines like this in the menu :
Ubuntu kernel 2.6 -17- 11  generic
Ubuntu kernel 2.6 -17- 11  generic (recovery)
Ubuntu kernel 2.6 -17- 10  generic
Ubuntu kernel 2.6 -17- 10  generic (recovery)

what to remove ?  should i remove the old kernel first ???

---

### Post by ajgreeny on 2007-02-27
You will need to do this as root so in a terminal type:-
gksudo gedit /boot/grub/menu.lst

Now edit the bottom part of the file where the list is showing by putting a # at the start of the lines of the lines with "title" at the beginning that you don't want to show, like this:-


# This is a divider, added to separate the menu items below from the Debian
# ones.
#title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
#title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


Now save the file and next time you start up these entries for windows will not be there.

I do wonder, however, why you want to do this.  If you still have windows on your hard disk, surely it makes sense to keep it for emergencies; I have occasionally broken my Ubuntu installation and without windows to fall back on I would have been well and truly stuffed.  If you comment out the grub entries with # you will not be able to boot into windows easily until you re-edit the menu.lst file back to what it was.  A good idea?  I'm not sure it is.  By all means comment out the older linux kernel entries once you know the new one is working OK, (or uninstall them in synaptic if you prefer), just to shorten the list, but think again about windows if you ever want to double boot.

---

### Post by TonKi on 2007-02-28
Yes, you can remove the older kernel, IF the newer works fine. You can do it with
```
sudo apt-get remove linux-image-2.6.17-10-generic
```
Assuming you have the generic kernel installed

---

