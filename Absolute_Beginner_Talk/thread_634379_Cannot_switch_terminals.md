---
title: "Cannot switch terminals"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by lamalex on 2007-12-07
I'm unable to switch terminals, I'd like to be able to use my tty1 and so on, but when I hit control+alt+fX, I just see flashing lines of colour. I'm thinking it has something to do with the fglrx graphics driver, but does anyone have a solution?

---

### Post by mgmiller on 2007-12-07
I suspect you may need to change the resolution during the boot process to make the tty screens display properly.  I had a similar problem with an ATI video card a while back and this did the trick for me.  Here is a nice lengthy How To:

How to change the resolution during the graphical boot:

You need to edit /boot/grub/menu.lst and add vga=771 or 788 or 792 
to the end of the line for the kernel you are booting.

First make a backup of the old one:

```
sudo cp /boot/grub/menu.lst menu.lst.backup
```

Then edit the file:
```

sudo gedit /boot/grub/menu.lst
```

Once you have the vga= number you like, add it to the automagic line options 
in the additional options area so it carries through to kernel updates. 
This is in /boot/grub/menu.lst as shown below, where I have selected vga=786,
which will set the boot screen to 640x480 24 bit color:

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=786

Finally, to append the change to all kernel lines, run the following: 
 
```
 sudo update-grub 
```

To know which vga= number to use, consult this handy chart:

640x480 800x600 1024x768 1280x1024
......768...........771.............773...........775.................256 colors
......784...........787.............790...........793.................(8 bit)
......785...........788.............791...........794.................(16 bit)
......786...........789.............792...........795.................(24 bit)


good luck.....

---

### Post by lamalex on 2007-12-09
no dice :( I tried every one of those options but none of them are the right one. Is there a way to force it to another mode other than VGA? It's kind of annoying to HAVE to use X, when half the time I  don't even need to.

---

### Post by mgmiller on 2007-12-09
Have you tried changing from the fglrx to the ati driver? or for that matter, try using vesa.  If it works with one of those, then maybe there is a command that should be in xorg.conf so the fglrx can also work with tty1.

That being said, I didn't think the driver in xorg.conf was even used outside the x environment.

During post and during a normal boot, if you hit escape to exit the graphical boot screen, does your display work correctly?  If so, at what point in the boot does the display corrupt before x kicks in?

---

### Post by lamalex on 2007-12-09
With the ati driver I can switch terminals, however I don't get 3d acceleration with it. In a normal boot I can see the plain output just fine, everything displays right, however once I'm in X, I can't leave it for a basic terminal. Now I'm playing with switching to the radeon frame buffer from the vesafb. If anyone has any experience with radeonfb on ubuntu, some help would be appreciated.

---

### Post by lamalex on 2007-12-09
no luck with the radeon frame buffer. I loaded the radeonfb module to see if that would help, hasn't seemed to make a differece, although my boot splash is clearer than it used to be...

---

