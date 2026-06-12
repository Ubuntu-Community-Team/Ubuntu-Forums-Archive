---
title: "A Few Quick Q's About GRUB"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Chadwick17 on 2007-08-18
Hello Everyone - 

    First I will say that I tried running Ubuntu as the only OS on my comp earlier this year, while Ubuntu was great I need to run specific programs (SketchUp, AutoCAD, etc.) so I needed Windows for that reason. Anyway, so now I am back again with a new laptop that is running Windows Vista and Ubuntu 7.04.

My first question is how do I get GRUB to boot my Vista partition by default? I opened the menu.lst file, and I kind of understood it, but wasn't sure enough to change anything without toasting the booting sequence. 

Second: Is there a way for me to lose all those Kernel updates in GRUB? It gets kind of confusing after X updates...

Third: This one is a bit superficial, but is there a graphical version of GRUB and not something that is just text based? I hate to bring up other OSes, but a good friend of mine had bought a mac laptop and it popped up a screen on boot that had the OSX, Linux and Windows logo to choose from. Again, obviously this isn't necessary but it would look nice nonetheless....

Again thanks for everyone's help! This is one of the best user communities I've ever come across. I'm trying to stick with Ubuntu for good -  I really want to get comfortable with it (and Linux in general). I think some general info books would help too (Ubuntu Bible, Ubunut Hacks, etc).

Thanks in advance!

---

### Post by RaZer0r on 2007-08-18
the boot order is simply changable by changing the order of the menu.lst....
So just put
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

above the kernel loading parts ;)

(offcource, it might look a bit different on your system, but you get the clue)

---

### Post by overdrank on 2007-08-18
> **Chadwick17 said:**
> Hello Everyone - 

    First I will say that I tried running Ubuntu as the only OS on my comp earlier this year, while Ubuntu was great I need to run specific programs (SketchUp, AutoCAD, etc.) so I needed Windows for that reason. Anyway, so now I am back again with a new laptop that is running Windows Vista and Ubuntu 7.04.

My first question is how do I get GRUB to boot my Vista partition by default? I opened the menu.lst file, and I kind of understood it, but wasn't sure enough to change anything without toasting the booting sequence. 

Second: Is there a way for me to lose all those Kernel updates in GRUB? It gets kind of confusing after X updates...

Third: This one is a bit superficial, but is there a graphical version of GRUB and not something that is just text based? I hate to bring up other OSes, but a good friend of mine had bought a mac laptop and it popped up a screen on boot that had the OSX, Linux and Windows logo to choose from. Again, obviously this isn't necessary but it would look nice nonetheless....

Again thanks for everyone's help! This is one of the best user communities I've ever come across. I'm trying to stick with Ubuntu for good -  I really want to get comfortable with it (and Linux in general). I think some general info books would help too (Ubuntu Bible, Ubunut Hacks, etc).

Thanks in advance!

HI this link has alot of great info
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Good luck!

---

### Post by Chadwick17 on 2007-08-18
Thanks for the quick replies. That explains it clearly. From browsing around I found this link:

[http://ubuntuforums.org/showthread.php?t=295524]("http://ubuntuforums.org/showthread.php?t=295524")

This looks like pretty good. I had downloaded the live CD for Fedora 7 as well and saw some things there that I liked (the ability to change the boot preference from a GUI within was one). Ultimately I decided to return to Ubuntu (I've heard upgrading Fedora is a pain).

Also, excuse me if it doesn't seem like I know what I am talking about - I am not too new to Linux, but lack the experience of using it regularly. 

Thanks again!

---

### Post by CowzRule on 2007-08-18
The first thing you want to do is get rid of all the extra kernel entries. First in the terminal put:```
gksudo gedit /boot/menu.lst
```Look for this section```
## controls how many kernels should be put into the menu.lst 
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all
```Change the last line from "all" to "1". save the file and close it. Now back in the terminal put:```
sudo update-grub
``` Now you can go in and select what os you want to boot as default. Reopen menu.lst and look for this section:```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0
``` Change the last lines from "0" to the the number of the item you want to be default. To find that number, starting with 0, count the number of entries at the bottom of the file. Here's mine:```

title		Ubuntu, kernel 2.6.20-16-generic **[color=red]<--- #0[/color]**
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7f9e7b63-becf-4491-adf5-41becc23e41d ro vga=792 splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) **[color=red]<--- #1[/color]**
lock
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7f9e7b63-becf-4491-adf5-41becc23e41d ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+ **[color=red]<--- #2[/color]**
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems: **[color=red]<--- #3[/color]**
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional **[color=red]<--- #4[/color]**
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```Basically you're counting the number of time "title" is listed. So if I wanted to have Windows XP be my default OS at boot I would change the "0" to "4".

---

### Post by Chadwick17 on 2007-08-18
Thanks for laying out the text way of editing that for me...I feel like this is the way best way to learn Linux is through file editing and command line but after having used Windows for so long I always tend to fall back onto GUIs that people have made (like the one I posted above). 

Still, I do appreciate seeing the guts, so to speak...

---

### Post by CowzRule on 2007-08-18
> **Chadwick17 said:**
> 
Third: This one is a bit superficial, but is there a graphical version of GRUB and not something that is just text based? I hate to bring up other OSes, but a good friend of mine had bought a mac laptop and it popped up a screen on boot that had the OSX, Linux and Windows logo to choose from. Again, obviously this isn't necessary but it would look nice nonetheless....

I believe all grub will do is display a wallpaper type image. You can use any png type picture you want, however when it's converted the picture is resized to 640x480 and only 14 colors.
To do it you might need to install imagemagick.```
sudo apt-get install imagemagick
```Then get the picture you want, rename it to wallpaper.png and save it in your home folder. Now open the terminal and put```
convert -resize 640x480 -colors 14 wallpaper.png splash.xpm && gzip splash.xpm
```Then copy it to the /boot/grub folder```
sudo cp splash.xpm.gz /boot/grub
```Then finally ```
sudo update-grub
``` and reboot to see it.

---

