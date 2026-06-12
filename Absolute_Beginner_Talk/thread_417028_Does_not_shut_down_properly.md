---
title: "Does not shut down properly"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Arjunus on 2007-04-21
Hi,

When I hit shut down in my ubuntu (fiesty fawn), it kills all the processes turns but gets stuck at the last line. 

"will now halt"

I am then forced to manually press the power button to kill the power. Also when I hit the power button while in the operating system it just cuts the power instead off a proper software shut down. Any ideas anyone?

---

### Post by jalbatros on 2007-04-22
Hi, I had the same problem, and Saint Google helps me.
Here you have the solution that works in my PC, may be in yours too ...

1. Edit /etc/modules with "$ sudo gedit /etc/modules" and add a new line: "apm power_off=1"

2. Edit  Grub menu with "$ sudo gedit /boot/grub/menu.lst" and look for the line with the kernel option you use normally (Ubuntu, kernel 2.6.20-15-generic in my own), at the end of this line add "acpi=off apm=power_off", without quotes of course.

3. Now you have to restart your PC in order that changes take effect.

Try it, good luck.

---

### Post by Arjunus on 2007-04-23
hi Jalbatros,

apologies but you are dealing with a complete n00b here! I went into the terminal and opened the modules with gedit but where do i add the line? 

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp

this is what I see...

---

### Post by jalbatros on 2007-04-24
Your file should be like follow:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
apm power_off=1



and for the grub menu add "acpi=off apm=power_off" at the line beggining with "kernel 2.6.XX-generic ...."

It should work.

Regards.

---

### Post by jalbatros on 2007-04-24
I mean, in grub menu add "acpi=off apm=power_off" at the end of the line beggining with "kernel 2.6.XX-generic ....", it shows:

kernel 2.6.XX-generic .................... acpi=off apm=power_off

Regards again

---

### Post by Arjunus on 2007-04-24
I have inserted those two lines but nothing seems to happen.

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic acpi=off apm=power_off
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=01ab15d2-057c-4b22-9652-182a67f9fff5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

Thats the screenshot from GRUB. and heres the line I pasted in /etc.

# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
apm power_off=1

I do not know what I have done wrong but it doesnt seem to have worked. When I hit restart it still hangs at the last line and I have to maually power out. Any more suggestions? Thanks anyway!

---

### Post by jalbatros on 2007-04-24
You have put the options "acpi=off apm=power_off" in the wrong line. Here your have my lines for /boot/grub/menu.lst file:

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=8ca2f840-3c6e-40e0-8578-b92c5a4d560b ro quiet splash acpi=off apm=power_off
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault


Sorry for any misunderstanding, good luck.

---

### Post by jerrylamos on 2007-04-24
The "acpi=off apm=power_off" goes at the end of the "kernel" line just after "quiet splash".  Note this is one very long line with no breaks.  It will likely wrap over to the next line.

The "title" line is just a comment line that comes up on boot so you know what to pick.

I haven't tried this workaround yet but it's edited in.

Thanks, Jerry

---

### Post by Arjunus on 2007-04-25
i hav inserted the line like you guys said but to no avail! my computer still hangs on the shut down screen. is there any other code i need to edit? 

anymore ideas?

---

### Post by kyphi on 2007-04-25
You could try reseating your RAM modules, i.e. take them out and reinsert them.  Make sure that the top and bottom locking tabs are in the correct place.

---

### Post by graabein on 2007-12-30
> **jalbatros said:**
> Hi, I had the same problem, and Saint Google helps me.
Here you have the solution that works in my PC, may be in yours too ...

1. Edit /etc/modules with "$ sudo gedit /etc/modules" and add a new line: "apm power_off=1"

2. Edit  Grub menu with "$ sudo gedit /boot/grub/menu.lst" and look for the line with the kernel option you use normally (Ubuntu, kernel 2.6.20-15-generic in my own), at the end of this line add "acpi=off apm=power_off", without quotes of course.

3. Now you have to restart your PC in order that changes take effect.

Try it, good luck.

I'd been having almost the same problem on Xubuntu 7.10, with the computer hanging after the unload bar was empty, but it did not shut itself off. Doing this solved it for me, big thanks!

---

