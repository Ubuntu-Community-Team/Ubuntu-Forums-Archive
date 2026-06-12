---
title: "how do i edit boot file  (NOOB)"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by timmy toad on 2007-05-14
I am at present dual booting with Ubuntu and Win XP, i can see i can edit the boot menu but it isnt clear what i can chnge and what for.

for example there is a 9 second delay before it defaults to Ubuntu how can i change this 9 seconds ?.

also how can i change the default OS from Ubuntu to XP if it isnt selected within 9 seconds.

tim

---

### Post by pizzutz on 2007-05-14
You can edit the file /boot/grub/menu.lst  That is pretty well documented in the file itself.  You can change the timing and default selections.

---

### Post by Campingman on 2007-05-14
Here you go, everything you ever needed to know about grub
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

---

### Post by lluisanunez on 2007-05-14
Change the value of "timeout" to whatever you want.
Change de value of "default" to the OS you want, note that they are numbered from "0" (the first)

---

### Post by howlin_walleye on 2007-05-14
When the boot menu appears you can use the up/down arrow to navigate to another boot type. In your case, you'd navigate to the Windows XP option.

You can also use the boot screen to edit the boot arguments on the fly. If you don't know why you'd want to do that, then you most likely don't need to do it. 

The menu is derived from a text file on your system, /boot/grub/menu.lst. Its owned by root, so edit it with sudo:

sudo vi /boot/grub/menu.lst

or with gksudo

gksudo gedit /boot/grub/menu.lst


The timeout is specified on a line like this:

timeout 9

Change the "9" to fewer seconds if you wish.


The default boot option is specified with a line that says ...

default 0

Your machine may have a different number than "0". You should change this number to 
the index of Windows XP in the "Automagic kernels list" towards the bottom of the file. Scroll down to a line which says 

### BEGIN AUTOMAGIC KERNELS LIST

From there scroll further until you see a set of "boot stanzas". These are groups of lines which tell grub how to perform a particular boot sequence. The first couple on my machine look like this:

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-28-amd64-generic Default
root            (hd0,0)
kernel          /boot/vmlinuz root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-amd64-generic Default (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz root=/dev/sda1 ro single
initrd          /boot/initrd.img
boot



Again, yours will differ most likely. The important thing is to count them, starting at 0 (zero), and find the number corresponding to Windows XP. Use that number with "default" above. 


Dan

---

### Post by timmy toad on 2007-05-14
thanks lads, that is exactly what i wanted. brill.

tim

---

