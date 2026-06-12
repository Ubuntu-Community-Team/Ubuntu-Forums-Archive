---
title: "Screen Resolution"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by Binh on 2006-06-11
I booted Ubuntu from the Live CD and I can't seem to change the screen resolution. It's fixed at 640X480 and it says to change it in the drop down menu but it doesn't drop down!

---

### Post by dermotti on 2006-06-11
hmmm, i would look in /etc/X11/xorg.conf and see what driver X is trying to use.  If its using anythign other than Vesa, change it to Vesa and restart X.

---

### Post by Binh on 2006-06-11
okay, I'm new to linux, so i have no idea how what you're talking about. Is it the fact that I haven't installed linux yet? I'm still "testing" it from the live CD. I don't think I'll install it if the screen resolution is going to stay 640 480 permenantly.

---

### Post by Jason_25 on 2006-06-11
See this post just a few below yours ;-) 

[http://www.ubuntuforums.org/showthread.php?t=194735](http://www.ubuntuforums.org/showthread.php?t=194735)

---

### Post by confused57 on 2006-06-11
See this thread posted about an hour ago:

[http://www.ubuntuforums.org/showthread.php?t=194715](http://www.ubuntuforums.org/showthread.php?t=194715)

sudo dpkg-reconfigure xserver-xorg

will allow you to go in and select what resolutions you want your monitor to display, everything else, you can probably just select the default values.

---

### Post by taurus on 2006-06-11
Click Applications -> Accessories -> Terminal to open a terminal.  Then from that terminal, type
```

sudo gedit /etc/X11/xorg.conf

```
Scroll down where it says 
```

Driver                "nv"

```
and change it to "vesa".  Save it and then hold down <Ctrl><Atl>Backspace at the same time to restart X...

---

### Post by Binh on 2006-06-11
thanks for the quick response. Okay, I did what you said (the vesa thing) and it worked, but now there's another problem. THe screen resolution is good, but there's a permanate image of a mouse pointer in the middle of my screen. I can move my mouse, but the image stays the same, so there's like two mice on the screen. All the desktop icons go under the mouse and changing the backround doesn't work. thanks.

---

### Post by taurus on 2006-06-11
Then maybe you need to look in /etc/X11/xorg.conf again, under the section of Input regarding your mouse then.

---

### Post by Binh on 2006-06-11
Hmm, okay, I'll take care of that after it's done installing. Where am I supposed to get the multibooter from? I didn't see anything about it on the installatin CD.

---

### Post by taurus on 2006-06-11
During the installing, it will ask you if you want to install either GRUB or LILO (bootloader) and where you want to install it.  I would pick GRUB and have it install on MBR...  Just follow the instructions on the screen.

---

### Post by Binh on 2006-06-11
okay, if I made the partition for my windows XP too small, how do I change the size of it?

---

### Post by acorn22 on 2006-06-12
I used this boot disk >[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) and used the program GNU parted which lets you resize partitions without loosing data. look in the documentation. There is a full guid how to do this. It is really easy. when the disk loads, type 'parted' then type 'print' to get a look at your partition table. 

 resizing goes something like ```
resize (partition name) (starting point, like 0 mb) (ending point, like 2GB)
```

or just type 'resize' and it will prompt you for the rest of the info. BACK UP EVERYTHING if you can :) (and read their documentation, too) [http://www.gnu.org/software/parted/manual/parted.html#Running-Parted](http://www.gnu.org/software/parted/manual/parted.html#Running-Parted)

---

