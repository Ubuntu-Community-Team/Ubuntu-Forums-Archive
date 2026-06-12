---
title: "Help Installing Logitech Quickcam"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by deaster2 on 2007-02-19
with the help of this forum, I have been able to install everything that I want,
in Firefox, flash, java, movie players and even a 2nd hard-drive that I can read
and write to. For the life of me, I have read and tried everything that the forum
suggested to install webcam drivers for my Logitech Quickcam.
I can't seem to come up with the right commands to install this driver(which
is the one from reading is the one I need).
Here is the output:
deaster@deaster-desktop:~/gspcav1-20070110$ su
Password: 
root@deaster-desktop:/home/deaster/gspcav1-20070110# make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1
root@deaster-desktop:/home/deaster/gspcav1-20070110# 
What am I doing wrong?

---

### Post by Lderan on 2007-02-19
I haven't been able to get my logitech web cam to work either. It's very strange.
It must like windows too much. :P

---

