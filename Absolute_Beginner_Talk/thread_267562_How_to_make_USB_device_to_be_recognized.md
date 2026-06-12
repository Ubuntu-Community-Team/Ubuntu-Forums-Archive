---
title: "How to make USB device to be recognized?"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by i-m-p on 2006-09-28
Does anyone know?
or Does kodak usb reader never work with Linux?

There must be some way to do it. I think.

---

### Post by orb9220 on 2006-09-28
usb devices are mounted in /media folder I believe and are automatically mounted.

---

### Post by i-m-p on 2006-09-29
Quote
"usb devices are mounted in /media folder I believe and are automatically mounted."

I believe so. However when I plug my "Kodak USB Card Reader" nothing happenes.

I checked storage tab on System>Preferences>Removable Drives.

I dit also this.
:~$ sudo mount -t vfat /dev/sda1 /mnt
mount: special device /dev/sda1 does not exist

Yet no luck.

Anyone? Maybe the problem is Kodak. I suspect. Any Idea?
Does anyone using Kodak usb card reader?

---

### Post by i-m-p on 2006-09-29
Hello, Anyone?

---

### Post by tatimmer on 2006-09-29
Type the following into a terminal then plug in your device.  You should get some feedback if the device is detected.  

"tail -f /var/log/messages"


On my system it will produce no message for a floppy disc indicating my floppies can not be auto mounted.  

You can also research hal, hald, udev, dbus and gnome-volume-manager. Also look at the output of "lshal" after the device is plugged in.

---

### Post by i-m-p on 2006-09-29
Cheers,
Oops, It looks like device is actually recognized. When I type-tail -f /var/log/messages- It says among other things.

[17181770.564000] Driver 'sd' needs updati ng - please use bus_type methods
This one might be the key to solve the problem. Do you know what I can do?

> You can also research hal, hald, udev, dbus and gnome-volume-manager. Also look at the output of "lshal" after the device is plugged in.
I tried some it produce very long text.

Thank you

---

### Post by bodhi.zazen on 2006-09-29
[[color=blue]This is what you seek[/color]](http://usbat2.sourceforge.net/)

You need the kernel source:```
sudo aptitude install linux-tree
```

[[color=blue]FAQ[/color]](http://usbat2.sourceforge.net/faq.html)

---

### Post by i-m-p on 2006-09-29
Thanks, It seems,,however, I have it already.
Here's the result of
sudo aptitude install linux-tree

Couldn't find any package whose name or description matched "linux-tree"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

I wonder what the last line says....

I plugged a usb mouse to the same usb socket and it works.

---

### Post by bodhi.zazen on 2006-09-29
sudo aptitude install linux-tree-'uname -r'

---

### Post by i-m-p on 2006-09-30
> sudo aptitude install linux-tree-'uname -r'

I don't understand the last part 'uname -r'.
This is  a planet novice. Nevertheless I pasted. That's all I could do.

> Couldn't find any package whose name or description matched "linux-tree-uname -r"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

Thank you. I really appreciate your effort to help me out.

---

### Post by K.Mandla on 2006-09-30
Make sure you keep the ` marks around the uname -r.

---

### Post by i-m-p on 2006-09-30
Ok I see. I just have to paste this.

> sudo aptitude install linux-tree-'uname -r'

Result.

> Couldn't find any package whose name or description matched "linux-tree-uname -r"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


---

### Post by i-m-p on 2006-09-30
Man, I can not give up on this yet.
Any suggestions?

---

### Post by apkolev on 2006-09-30
Hi!

I am new to Linux but this is what I know: 

type "***uname -r***" in the terminal window and you will get the version of your distribution. should look like this: 2.6.15-27-386 (this is mine). 

then just append this result to the comant repalcing 'uname -r' with it. maybe there is a reason that they put in those `` but it is not working for me. mo here how the commant looks like when I write:

> sudo aptitude install linux-tree-2.6.15-27-386

hope that helps!

oops... I get the same response the the comand as you do. have a look at this [link]("http://brion.inria.fr/anla/package_info?id=47547"). Thele is a list of different versions of the package. Try installing the one that corresponds to your version, namely the output of "uname -r"

Edit 1:
I tried the Debian package search and I get it only for the testing version for kernels 2.6.16, 17 and 18. mine is 15 so i have no idea what to do.

Does anyone has an idea?

---

### Post by i-m-p on 2006-09-30
Cheers,
Yes mine too is a 2.6.15-27-386.

> sudo aptitude install linux-tree-2.6.15-27-386

However result was the same.
> Couldn't find any package whose name or description matched "linux-tree-2.6.15-27-386"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

Thanks for you support though.

There should be someone out there.

---

### Post by i-m-p on 2006-09-30
I try once again. Man, it should work.

Thanks for your support

---

