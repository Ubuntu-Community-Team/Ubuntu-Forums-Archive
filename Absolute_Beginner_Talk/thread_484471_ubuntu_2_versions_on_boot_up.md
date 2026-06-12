---
title: "ubuntu 2 versions on boot up"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by manuleka on 2007-06-25
just installed ubuntu and updated it...

when booting up now i have two versions to pick from

the original cd version and the updated one... 

kernel 2.6.20-15 and kernel 2.6.20-16

if i pick the 2.6.20-15 wil it reupdate the kernel again? 

do i just add hash (#) at the beginning of the lines for the older kernel on grub to hide it? is there a way of permanently removing this?

---

### Post by Papi-KB7VGW on 2007-06-25
all I did was add the # to comment out each line.  15 no longer appears on my grub boot screen

---

### Post by w4ett on 2007-06-25
It's pretty much standard to keep a backup kernel in case a future update breaks your system.  If you really want to remove it you can do it in the Synaptic Package Manager.   No, booting from the older kernel will not force an update.

---

### Post by BobCFC on 2007-06-25
EDIT: doh too slow

---

### Post by manuleka on 2007-06-25
so what's up with the Ubuntu, memtest86+

my boot menu is like this

ubuntu 2.6.20-16
ubuntu 2.6.20-16  (recovery mode)
ubuntu 2.6.20-15
ubuntu 2.6.20-15 (recovery mode)
other operating systems
windows vista
windows vista (recovery mode)

i wanna clear out some so i can have a simple boot options

can i remove the memtest? and other operating systems? or is there a way of just putting ubuntu (latest kernel) and vista... and then when press esc or something then the extra options appear?

---

