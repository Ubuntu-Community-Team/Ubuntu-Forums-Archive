---
title: "X configuration has been altered"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by Kuraboy on 2006-06-04
Hi!

I wanted to type:

sudo nvidia-glx-config enable

but I get the error message:

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.


thnx in advance

---

### Post by divague on 2006-06-27
I was having the same problem, just edit the xorg.conf file like this

$ sudo gedit /etc/X11/xorg.conf

search for: 

     Section "Device"

and change:

    Driver		"nv"

for:

     Driver		"nvidia"

if you don't want the nvidia screen when your computer boots up just add this line

     Option		"NoLogo"

and reboot your computer.

---

