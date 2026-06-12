---
title: "Can't import pictures from camera"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by AriciU on 2007-06-20
Cam is a Canon IXUS SD10. I connect it, Ubuntu finds it fine. If i go to kcontrol / peripherals / camera and hit TEST it says that everything is ok.

How do i import the pictures from it? Where is the sdcard link supposed to be found? If i hit Information on it it shows me the media card as Drive D but i can't find it anywhere...

---

### Post by atria on 2007-06-20
I'm not sure how the camera works, but do browse to /media and see whether the SD card is mounted there.

Good luck

---

### Post by AriciU on 2007-06-20
There is no sdcard in /media ... only links to my other partitions. Nothing in /mnt either. 

Thing is, when i connect the camera, a konqueror window pops up browsing some files. The folders over there don't contain anything...

I'll attach some pics for better understanding.

Thanks

---

### Post by atria on 2007-06-20
Try doing a 
```
dmesg | tail
```
after plugging in your camera. Look for the location of the SDCard from the output of dmesg and mount it manually with the mount command.

I hope that helps

---

### Post by AriciU on 2007-06-20
I got this... no sdcard though.

---

### Post by atria on 2007-06-20
Sorry but i don't think i can help you any further since i'm not exactly sure how your camera works. Maybe do a search on the forums or wait for someone else to provide further assistance.

In the meantime you might want to read the files using a SD card reader instead, heh.

Good luck

---

### Post by AriciU on 2007-06-20
Fixed it. 

I had to edit the file "/etc/udev/rules.d/45-libgphoto2.rules".

Had to change line 3 from 
> BUS!="usb*", GOTO="libgphoto2_rules_end"
to
> SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"

and add the following line to the end of the file
> SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30fe", MODE="0660", GROUP="plugdev"

Then i restarted it (/etc/init.d/udev restart) and i was able to browse the card and copy photos from it. :)


It is **painfully** slow though while copying and accesing the files. Don't know what's up with that. :(

---

### Post by atria on 2007-06-20
Fantastic, glad it worked for you!
You just taught me something new :D

Thanks for posting the solution here btw, it'll definitely help people with similar problems.

Anyway, how slow is it? It is supposed to be faster?

---

### Post by AriciU on 2007-06-20
Found it using the search tool better :D

Well... 10 pictures (about 8mb) took around 3-4 minutes to copy. I mean, it's slow compared to windows (20 seconds).

---

