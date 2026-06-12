---
title: "Screen fades to white"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2008-01-08
Can anyone please help.

I've installed 7.10 fine. Md5 checked out, no errors on disk, I boot up and install. Now I take the disk out and try to reboot and the screen fades to white. Please, please help. This is not my computer and I've been wrestllng with this for two weeks now. Please help. Thanks

---

### Post by bwhite82 on 2008-01-08
Well it seems that your graphics hardware isn't configured properly. You'll have to do some command line work from safe mode:

Type the following after logged-in (safe mode):
> 
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

Then:
> nano /etc/X11/xorg.conf

This will open your graphics hardware configuration file. Press the down arrow on your keyboard to scroll through the file until you find:

> Section "Device"
	Identifier	"Generic Video Card"
        Driver          "fglrx"

You need to change whatever YOU have in the quotation marks for Driver to: vesa

Then hit: CTRL+X, then "y" for yes, then hit enter to save the file. After its saved type:
> 
startx

...to see if it works. If so, you'll at least have a graphical desktop from which you can come back on here to the forums and/or wiki to find out how to properly configure your card.

-Cheers

---

### Post by hwg43 on 2008-01-26
I had the same thing happen.  BUT, if I wait a couple minutes, I do eventually get the login screen.

It is annoying, but not fatal.  But I would like to figure out how to fix it.  It must have something to do with a video mode.

I'm using a laptop with 1024 x 768 screen resolution.  I tried adding vga=0x317 to the 'kernel' line in /boot/grub/menu.lst   That didn't help.

Any other ideas?

hwg

---

