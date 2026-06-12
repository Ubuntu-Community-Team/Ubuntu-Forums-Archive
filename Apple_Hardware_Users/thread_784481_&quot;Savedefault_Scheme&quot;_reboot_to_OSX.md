---
title: "&quot;Savedefault Scheme&quot; reboot to OSX"
date: 2008-05-06
forum: Apple Hardware Users
---

### Post by meg23 on 2008-05-06
Anyone know how to edit this script to make it work with OS X and yaboot? The feisty disk starts up by default on a PPC with two hard drives (OS X and Ubuntu).

[http://robotics.caltech.edu/~klk/linux.html](http://robotics.caltech.edu/~klk/linux.html) 

> 
"Do you use grub as your bootloader. Your "default" boot option is probably some Linux kernel. For some reason or another you'd like to reboot into windows, but you always forget that you need to stick around so you can select Windows from the grub menu. You get really annoyed like I do when you forget this and have to reboot again. I wrote this simple script to tell grub to set the default to the Windows option on the next boot."

> #!/bin/sh 

# a simple script to reboot into windows once without user
# intervention.  Assumes that the menu listing corresponding to
# windows at least has "win" in the title.  If it doesn't, you can
# change the WINSTRING variable below.

WINSTRING=win
GRUBMENU=/boot/grub/menu.lst

let "WINNUM = `grep title $GRUBMENU | grep -in $WINSTRING | cut -d: -f1` - 1"
#echo "num is $WINNUM"
/sbin/grub --device-map=/boot/grub/device.map --batch <<FOO
savedefault --default=$WINNUM --once
quit
FOO
/usr/bin/reboot


---

