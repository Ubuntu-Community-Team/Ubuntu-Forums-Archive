---
title: "CD Tray won't open.... GRUB won't show Windows anymore?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by tonycm1 on 2007-07-07
Alright, I have 2 problems which occured at the same time

I didn't use my laptop for about a month but when I was about to head out to the road and grabbed my laptop (which is a Dell Inspiron 1300 with Ubuntu / Windows on it) the GRUB menu that originally loads up does not have Windows as an option there anymore.... 

Also, when I load Ubuntu like I normally do, my DVD/CD tray doesn't open when I click on the button to open it.... as far as I can see, Ubuntu is telling me there's nothing in the tray but I don't know how this happened

I'm desperate for help... anyone got any tips?

---

### Post by p_quarles on 2007-07-07
I had something similar happen at one point. The installation CD was inside, and even though I had it set to boot from the hard drive first, it wouldn't let me eject the CD. The solution was to go the BIOS at bootup, and then the CD ejected fine.

If that doesn't work, it's probably another problem I've encountered in the past: the broken CD drive. Those things just don't last forever.

---

### Post by tartarian on 2007-07-07
If you can boot into Ubuntu and there's like an icon of a cd on your desktop, then you should be able to right click and press eject.
This might sound stupid, but is there like a hole on the side of your cd drive? Because there's one on my computer and if you press the button in the hole with a pin then the ed tray has to open. 
As to the windows thing, try typing it into google. You'll need to edit a grub configuration file and add the partition of your windows installation on etc etc. I've had that problem before, but the answers are out there!

---

### Post by Sef on 2007-07-07
Read [How to restore grub]("http://doc.gwos.org/index.php/Restore_Grub").

---

### Post by neoguy2012 on 2007-07-07
Hi,

I'm not sure about the CD drive thing, but I think I can help you get windows back in the grub menu:

First, we'll back up the grub menu:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

Then we'll edit it using GNOME's gedit:

```
gksudo gedit /boot/grub/menu.lst
```

I am going to assume that your windows partition is the first partition on your first hard drive.  Add this to the end of the file:

```
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

I just copied that directly from my menu.lst file.  The title doesn't really matter.  You can call it whatever you want (especially if it's not XP Home just for sanity).  Change the root parameter if windows is stashed somewhere else.  Good luck!

---

