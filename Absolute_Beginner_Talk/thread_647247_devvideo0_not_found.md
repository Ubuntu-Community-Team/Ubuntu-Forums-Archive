---
title: "/dev/video0 not found??"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by tony.morse on 2007-12-22
Hi, my logitech webcam was working fin until I instaled a tv card, now wherever I try to use the webcam I get device /dev/video0 not found.  So I guess (having had a look at some other posts) that I now have 2 video devices so I need to reconfigure my device list?

err... can someone tell me how to do this?  I followed some other links but they didn't work and were for breezy anyway...

---

### Post by tony.morse on 2007-12-22
Ok, now it seems I don't have any /dev/video0 or /dev/video1 or /dev/video anything???
so how do I make this file?

---

### Post by tony.morse on 2007-12-23
Right, I've made dev/video0 by following other links but still no luck, it says to many symbolic links or something, and camorama and skype both say can't find dev/video0???
please please please help, I want my webcam working on Christmas day

---

### Post by frankos44 on 2008-01-13
I got Gutsy running on Shuttle SB83G5M main computer and Toshiba Equium laptop.

/dev/video0 exists on the Shuttle and the webcam works OK.

/dev/video0 does not exist on the Toshiba and the webcam does not work.

The same is true for both PC line and Logitech webcam's

I am investigating this and let you know what I find assuming I can fix it of course. Meanwhile if anyone else has had similar problems and managed to work round this I would be interested to know.

---

### Post by frankos44 on 2008-01-13
OK, this is what i found:

Step 1
$ lsusb
There was no mention of webcam

Step 2
I tried a different USB port and lsusb listed my webcam. I since discovered that the USB port is defective, strangely i never tried the USB at the rear of the laptop before.

Step 3
$ camorama
This gave me the error message "Could not connect to /dev/video0"

but
$ sudo camorama worked OK so this was a simple case of permissions.

Step 4
To fix this I created a group called video and added myself to this group and restarted the computer.

Now the webcam woks OK with camorama and kopete messenger. pigdin does not support webcam but I understand it will do in the future.

Regards Frankos

---

