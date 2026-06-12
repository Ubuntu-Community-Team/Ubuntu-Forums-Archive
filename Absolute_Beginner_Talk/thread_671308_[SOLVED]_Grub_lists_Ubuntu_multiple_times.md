---
title: "[SOLVED] Grub lists Ubuntu multiple times"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by CidBahamut on 2008-01-18
Ok, this has been building for a while but it finally hit the point where it's irritating.
I have two partitions on my machine. One is Ubuntu(Dapper Drake), the other is windows xp. 

In the Grub bootloader menu Ubuntu(and it's recovery mode) is listed multiple times. I believe it's up to five now and has finally bumped the windows selection off the page so I have to scroll for it. 
This seems to be loosely linked to the semi-automatic updates on Ubuntu, though I don't know what really triggers it. 
Has anyone else encountered this, and is there a way to revert it so Ubuntu only gets shown once?

If any of that was unclear, let me know and I will attempt to elaborate, thank you.

---

### Post by forestpixie on 2008-01-18
as the kernel gets update - new one gets put on menu.lst

you can change with the 
> 
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

part I assume - never been put in the position - yet :)

---

### Post by AlexenderReez on 2008-01-18
```
gksudo gedit /boot/grub/menu.lst
```

see the text file...you should figure out where are line that repeat...delete it..

[COLOR="Red"]or[/COLOR]

(possibility -->think first)
maybe you have install other kernel(makes it become like that...in that case..you need to remove old kernel using synaptic..

---

### Post by eggdeng on 2008-01-18
Grub lists all your available kernels so the list gets longer over time as you install new kernels through the automatic updates. Having older kernels on the list is useful because if, for any reason, you need to boot  into one, you can just choose it from the list. 
You can tell grub to list as many / few kernels as you want by editing your menu.lst. 
```
sudo /boot/grub/menu.lst 
```
You can either use the howmany = n option as explained in the file, or comment out unwanted lines by prefixing a #symbol.
Save and reboot. 
In general, I would be inclined to be careful about installing unneeded kernel updates as they can break your graphics driver among other things.

---

### Post by oldos2er on 2008-01-18
> **eggdeng said:**
> [quote]
```
sudo /boot/grub/menu.lst 
``` Should be "gksudo gedit /boot/grub/menu.lst"

 I'd opt for commenting out the unneeded lines rather than deleting them. They're easier to restore in case you ever need to.

---

### Post by CidBahamut on 2008-01-18
Alright, I opted for commenting lines out and now everything is well in the world. Thank you all for your assistance.

---

