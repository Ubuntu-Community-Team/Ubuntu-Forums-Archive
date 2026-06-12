---
title: "VGA out doesn't work with Fiesty need it for presentation today!"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by lizardbliz420 on 2007-07-10
So I have a HP Pavilion Dv4000 CTO notebook computer.  Before I switched to  i could press Fn F4 and it would send video out. Now it doesn't work. Is there some other way to get my computer to do video out?

---

### Post by dmfield on 2007-07-10
Looed at [https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/33045 which mentions]("https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/33045")

seems might be a bug?

if you exit /etc/X11/xorg.conf can you change the lines

Section "Device"
Identifier "Card0"
** Driver "vesa"**
BoardName "unknown"


 Change just this one line as follows
 

Section "Device"
Identifier "Card0"
** Driver "i810"**
BoardName "unknown"

---

### Post by lizardbliz420 on 2007-07-10
> if you exit /etc/X11/xorg.conf can you change the lines

Section "Device"
Identifier "Card0"
Driver "vesa"
BoardName "unknown"


Thanks for the help but 1 its not giving me permission to edit the file and two the file says

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
```

and not board name should i still configure it as you suggest?

---

### Post by Nekiruhs on 2007-07-10
> **lizardbliz420 said:**
> Thanks for the help but 1 its not giving me permission to edit the file and two the file says

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
```

and not board name should i still configure it as you suggest?
Press Alt + F2 and type gksudo gedit /etc/X11/xorg.conf He means change where it says "vesa" to "i810"

---

### Post by Outrunner on 2007-07-10
> **lizardbliz420 said:**
> Thanks for the help but 1 its not giving me permission to edit the file and two the file says

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
```

and not board name should i still configure it as you suggest?

For permissions edit it like this
```

gksudo gedit /etc/X11/xorg.conf

```

And what do you mean by 'board name'?

---

### Post by lizardbliz420 on 2007-07-10
the board name is in your original post

> if you exit /etc/X11/xorg.conf can you change the lines

Section "Device"
Identifier "Card0"
Driver "vesa"
BoardName "unknown"


Change just this one line as follows


Section "Device"
Identifier "Card0"
Driver "i810"
BoardName "unknown"

i tried switching to i810 and it didn't help... any other ideas?

---

### Post by dmfield on 2007-07-11
You might try this, it was for another issue, but might resolve yours..
> 
Go to System->Administration->Synaptic and do a search for 915resoluion (search it with no spaces)

install that package, reboot and that should be the end of your resolution problem :smile:. It was made specifically to help correct issues with the intel chipsets.

Other than that, i'm sorry, i'm out of ideas.. I don't have any other experience with intel video cards, more with ATI and NVIDIA

---

### Post by sab0403 on 2007-07-11
You have an intel chipset? What is the output of the following command:```
lspci |grep VGA
```?

---

### Post by sab0403 on 2007-07-11
Oh well... I'm off to do some actual work soon... you know, the one that pays the bills... :)

Anyway, I tried (succesfully) to [add a second monitor]("http://ubuntuforums.org/showthread.php?t=497136"), both using a second desktop and using an expanded desktop... perhaps that might help you... tinker with the settings. I'm sure using the "clone" option would render you something like what you want. Also, try using a lower resolution since you want to use it with a projector (or so I understand), perhaps to 640x480, on the second monitor.

---

