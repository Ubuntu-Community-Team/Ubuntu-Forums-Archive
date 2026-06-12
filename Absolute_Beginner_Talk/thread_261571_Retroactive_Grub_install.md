---
title: "Retroactive Grub install?"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by Doug0 on 2006-09-20
When I installed Ubuntu on the second HD of my WinXP machine, to be safe about it, I unplugged the primary master (containing windows) and put Ubuntu on the primary slave.  Now I have a machine that normally boots into WinXP, unless I go into BIOS and tell it to boot from the second drive.

Is there some way to re-install Grub now, without in any way affecting the WinXP drive, so I can push one key to get Ubuntu instead?

---

### Post by Drakkor on 2006-09-20
Fastest way to reinstall grub to the mbr of windows to dual boot
OK,boot to the live Ubuntu CD
Open terminal type
Code:

sudo grub

At the grub>prompt enter these commands
Code:

find /boot/grub/stage1

This will return a location like (hd0,1)
still in terminal type
Code:

root (hd?,?)

use the values from the find command
Next enter the command to install grub to the mbr
Code:

setup (hd0)

Enter
Code:

quit

reboot to the hard drive,and you will be given the grub menu to select what you want to boot Ubuntu is default and XP would be at the bottom,just hold down the down arrow key !

---

### Post by b_martinez on 2006-09-20
> **Doug0 said:**
> When I installed Ubuntu on the second HD of my WinXP machine, to be safe about it, I unplugged the primary master (containing windows) and put Ubuntu on the primary slave.  Now I have a machine that normally boots into WinXP, unless I go into BIOS and tell it to boot from the second drive.

Is there some way to re-install Grub now, without in any way affecting the WinXP drive, so I can push one key to get Ubuntu instead?

Or you can set your box to boot from the 2nd hdd and edit grub to read this

title Windows XP
 map (hd0) (hd1)
 map (hd1) (hd0)
 rootnoverify (hd1,0)
 chainloader +1

This re-maps the drives and may work to keep you from "affecting the Win XP drive".
You may not even need the 2 map lines.
hth
Bill

---

### Post by confused57 on 2006-09-20
> **b_martinez said:**
> Or you can set your box to boot from the 2nd hdd and edit grub to read this

title Windows XP
 map (hd0) (hd1)
 map (hd1) (hd0)
 rootnoverify (hd1,0)
 chainloader +1

This re-maps the drives and may work to keep you from "affecting the Win XP drive".
You may not even need the 2 map lines.
hth
Bill

If the above doesn't work, which it should, you could consider this as an option:


[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by gn2 on 2006-09-20
If you would prefer the default boot to be Ubuntu, change the boot order in the BIOS, so that the Ubuntu slave drive boots first, before the XP master drive gets a chance.

I would strongly discourage you from making a grubby mess of your mbr, because unless you a: have a Windows disc (not recovery software) and b: are lucky then you might not be able to fixmbr.

It doesn't always work, and prevention's better than cure.

Grub on my mbr was worse than any Virus I ever got.....
lost the lot.....or would have but for diligent back-up
but still had to re-install XPsp2, which takes ages

---

