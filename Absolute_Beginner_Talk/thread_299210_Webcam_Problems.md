---
title: "Webcam Problems"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by Mike_SMD on 2006-11-13
Hello everybody,
I just bought a Logitech Quickcam Communicate STX.
I'm using Ubuntu 6.06.1 LTS on an old Athlon processor.

I was told that it would be a simple matter of plugging the webcam in and then having it work. Unfortunately this isn't the case.

I tried downloading Easycam2 as it's supposed to install the correct drivers, but it doesn't even recognize that a webcam has been attached to the system. I have absolutely no idea what to try next, and yes... I've been looking through the posts but as usual most of it seems to be in greek (or english if you're not a bilingual greek). I'd really appreciate it if somebody could point me to a bare-bones-non-computer-geek version of some instructions. Otherwise I'm lost.

Thanks for any help that you can offer,

Mike.

---

### Post by PPAAUULL on 2006-11-13
It should pick it up I am not sure why not. is the driver installer for windows or linux?

---

### Post by Mike_SMD on 2006-11-13
Ahh, the disk that came with it is a windows install disk.

Do go on...


Mike.

---

### Post by Mike_SMD on 2006-11-13
How would I check and see if there's a driver installed for this cam? Or, on that note, do you have any idea where I might find a driver and some instructions on how to install it?

Thanks,,
Mike.

---

### Post by Mike_SMD on 2006-11-13
Sorry to flood this but i thought some more info might help, here is the result of typing "lsusb" in at the command prompt...

mike@mike-desktop:~$ lsusb
Bus 001 Device 002: ID 046d:08d7 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

Now, the only usb device I have plugged in right now is the webcam, can I assume from this that the computer is at *least* recognizing that one is hooked up?

Thanks again.

Mike.

---

### Post by Mike_SMD on 2006-11-13
Update!

I followed the advice of a fellow on this thread ([http://ubuntuforums.org/showthread.php?t=205782](http://ubuntuforums.org/showthread.php?t=205782)) and now I can get a result using the program 'camorama'. I followed these instructions...

>hi! just wanted to say that thanks to this thread and mostly the link you >gave, I could perfectly install my logitech quickcam express.
>don't really know how... but first i tried the debian package >[http://packages.debian.org/unstable/misc/spca5xx-source](http://packages.debian.org/unstable/misc/spca5xx-source) in that page and >nothing showed up on vlc capture or amsn. but then i downloaded the source >[http://mxhaard.free.fr/spca50x/Downl...0060925.tar.gz](http://mxhaard.free.fr/spca50x/Downl...0060925.tar.gz) and compiled it doing >"sudo ./gspca_build" and everything went ok now i can see my webcam working >in vlc and amsn in Ubuntu Dapper 6.06

Something's happening now at least.
I'll keep you posted.


Mike.

---

