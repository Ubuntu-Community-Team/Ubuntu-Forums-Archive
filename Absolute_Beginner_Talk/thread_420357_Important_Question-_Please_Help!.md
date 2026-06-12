---
title: "Important Question- Please Help!"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Scubastev013 on 2007-04-23
Hey all,

I'm in the process of reinstalling 7.04 to my computer and deleting the 6.10.  I tried to upgrade it, but it went nuts and now I can't get a GUI.  It may have something to do with my Nividia card, but I wouldn't know how to install a driver if there is one or where to get it.  I'm not really a command line kind of person.  If you could help me with that issue, would it boot into its normal GUI so a normal user like me can use it like I did 6.10?


Secondly, i currently have to press F12 on my computer to catch the boot menu to boot into XP.  I'd like to have it default to boot to XP-not to ubuntu.  How can i most easily accomplish that?


Scuba

---

### Post by annda on 2007-04-23
1) when you boot into ubuntu, do you get into command line? if so, log in and issue this command (when asked, use 'nv' as the driver):

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

if not, i suggest booting into recovery mode and typing the above command without sudo.

2) to change the boot order, you need to edit this GRUB configuration file:

/boot/grub/menu.lst

```
sudo nano /boot/grub/menu.lst
```

at the bottom, find which the windows entry is. if it the 3rd, you need to substract 1 (linux starts counting from 0). at the beginning of the file find the line 'default=0' and change 0 to 2.

save (ctrl+o) exit (ctrl+x) and reboot.

---

### Post by Scubastev013 on 2007-04-23
Hey thanks for your help.  I was able to get the video card to agree with the OS :) 

I'm gonna try to tackle the OS boot order next.  I don't really understand the directions though.  I don't want to screw something up really badly and not be able to get to my files on my Windows XP Pro partition.  Could you elaborate a little bit?


Thanks so much in advance!!!!



Scuba

---

### Post by annda on 2007-04-23
if you are not comfortable with making changes on your own, copy and paste the contents of your menu.lst file here.

open it in text editor. it's there:
/boot/grub/menu.lst

---

### Post by Scubastev013 on 2007-04-24
This is the bottom of the menu.lst

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1


What do I need to do?  There are like 6 or 7 entries like that for Ubuntu above it.  Is that normal?

Scuba

---

