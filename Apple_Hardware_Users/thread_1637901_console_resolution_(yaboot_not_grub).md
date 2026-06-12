---
title: "console resolution (yaboot not grub)"
date: 2010-12-05
forum: Apple Hardware Users
---

### Post by giannimaria on 2010-12-05
hi everybody, and thanks for considering this post

my computer is an iMac PowerPC G4, i.e. yaboot, not grub

i don't install full-fledged ubuntu releases; instead, i netboot, install the base system, then download the minimum i need; i don't use a display manager

ubuntu 9.10 didn't incur this problem; it affects both 10.4 and 10.10 (may it be connected with plymouth ?):

         console resolution is 800x600, whereas my display is 1024x768

is there a way for fixing that?, thanks again

---

### Post by barbaGNU on 2010-12-06
do you only need to fix console resolution by yaboot?
If the answer is yes then add to your  kernel option (e.g. for a radeon based machine) something like this:
    ```
video=radeonfb:1024x768
```

---

### Post by giannimaria on 2010-12-07
> **barbaGNU said:**
> do you only need to fix console resolution by yaboot?
If the answer is yes then add to your  kernel option (e.g. for a radeon based machine) something like this:
    ```
video=radeonfb:1024x768
```

first, thanks for helping

this is what i get
    ```
lspci | grep -i vga
0000:00:10.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX with AGP8X (Mac)] (rev a2)

cat /etc/yaboot.conf 
 ...
image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"
```

do i have to edit the `append' lines? if so, `video=' what?

after that, `man yaboot.conf' states that on PowerMacs you must run the ybin command each time you modify /etc/yaboot.conf:
do i need to pass any specific option?

thanks again


*edit*

must be due to this:

```
$ dmesg | grep "frame buffer" ;echo; cat /proc/fb
[    0.099262] Console: switching to colour frame buffer device 128x48
[    0.111535] fb0: Open Firmware frame buffer device on /pci@f0000000/NVDA,Parent@10/NVDA,Display-A@0
[   15.382762] Console: switching to colour frame buffer device 90x36
[   16.408869] fb0: nouveaufb frame buffer device

0 nouveaufb
```

as nouveaufb takes over from offb 128x48 drops to 90x36

any idea?, thanks


*edit2*

SOLVED with this:
```
append="video=1024x768"
```
then ```
sudo ybin -v
```

easier than expected; i just RTFM and searched the internet
a bit before proceeding

thanks for your precious advice

---

