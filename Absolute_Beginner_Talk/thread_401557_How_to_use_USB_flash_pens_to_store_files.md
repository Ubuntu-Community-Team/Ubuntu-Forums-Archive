---
title: "How to use USB flash pens to store files?"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by lp_man on 2007-04-04
Hi there! I'm a total linux newbie but so far it suits all my needs perfectly! What I'm trying to do however which I can't find any guides on how to connect a USB drive and get it to read files (all the search turns up with is how to use a usb pen as a boot disc).

Can anyone give me a clear walk through or link to a guide?

Thanks in advance!

-Will

---

### Post by Gina on 2007-04-04
Plug it in and an icon pops up on the desktop.  It also appears wherever your other disk drives show.  Use it like you would any other drive.  Most are formatted to FAT16 or FAT32 and are completely compatible with Ubuntu/Linux.

They're brilliant for swapping files between operating systems or between computers when setting things up.

---

### Post by raul_ on 2007-04-04
If it doesn't pop up, try opening "Computer" , see if any usb volume is there, right click it, and choose "mount"

---

### Post by drs305 on 2007-04-04
Since you are a newbie, just remember when you are finished with your usb pen drive you must unmount it before removing it from the computer. You can do that by right clicking it and selecting 'unmount' in Nautilus or via the terminal. Not everyone did it in Windows but you must do it in Linux to ensure no data is lost.

---

### Post by lp_man on 2007-04-04
Thanks for the help so far guys! It hadn't come up on the desktop like my cds had, so I went to computer and tried to mount the drive and got this error message:
[http://img133.imageshack.us/img133/5674/screenshotqq7.png](http://img133.imageshack.us/img133/5674/screenshotqq7.png)

I checked the file system on a windows computer and it states that its FAT32, which should work and yet it dosen't. I'm guessing I'm missing some drivers of some kind?

Thanks again for all the help so far!

---

### Post by raul_ on 2007-04-04
My guess is that you probably removed it without unmounting it (in Windows, for example). IMHO the most simple solution is to backup your data and formatting it again.

See if that happens with other pens, or just that one...if that's the only one, then do the above

---

### Post by lp_man on 2007-04-04
It's really quite odd, I've tried it with two different brands of USB pens to no avail. The light just keeps flashing on and off on the pen with no data being transfered. I've tried in several different ports as well.

I've noticed I have a 'Floppy drive' and a 'Floppy 1' where there is only one floppy drive in my pc, but when you insert a usb pen to a windows computer it brings up an additional drive for password etc. I've never used that feature but I'm trying to be spesific as it has really got me scratching my head!

---

### Post by lp_man on 2007-04-05
Sorry to bump this thread but the usb pens just refuse to work, I've backed up onto a different computer, how do I go about formatting the drive? 

Thanks in advance!

Edit; I tried booting the pc with the USB pen in and behold! It came up and worked, I unmounted and tried to use another one, didn;t work, put the other back in and tried to mount same error message again! Anyone know whats wrong?

---

