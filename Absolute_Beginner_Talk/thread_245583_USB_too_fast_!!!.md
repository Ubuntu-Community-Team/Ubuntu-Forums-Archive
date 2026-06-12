---
title: "USB too fast !!!"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-08-28
I have USB2 and it's too damn fast
when I copy mp3 to my mp3 player sansa m250 - some songs don't work right
I think it's b/z my usb
I've tried to make it slower in my bios - but there is an option just to make it faster
how can I slow down my usb driver ?

---

### Post by austin on 2006-08-28
it might be the "eject-problem".

try this:

copy a bundle of songs. Afterwards do NOT eject the usb-disk. Instead open a terminal and type 

mount 

try to find out which is your usb-disk. Likely it is /dev/sda1. If so, type 

sudo umount /dev/sda1

I guess that now you have to wait for some time, because the copy-process was not really finished before. When the terminal comes back to you it really is and your songs are correct.

---

### Post by MaximB on 2006-08-28
well I try that
I copied 50 songs in less then 2 minutes...it was a damn fast I think.

---

### Post by anaconda on 2006-08-28
> **austin said:**
> it might be the "eject-problem".

try this:

copy a bundle of songs. Afterwards do NOT eject the usb-disk. Instead open a terminal and type 

mount 

try to find out which is your usb-disk. Likely it is /dev/sda1. If so, type 

sudo umount /dev/sda1

I guess that now you have to wait for some time, because the copy-process was not really finished before. When the terminal comes back to you it really is and your songs are correct.

Or you could just right-click to the icon of your USB-disk in the desktop and select eject.. which also umounts the usb-drive.

---

### Post by hashimoto on 2006-08-28
You may experience the same phenomena as I do: Nautilus has done all it does and the "Copying files" window closes. Yet, the hardware is still struggling to do its job. I have a iRIver IFP player and when I copy files to the player, Nautilus shows that the file copying has been finished, but the player display shows that the transfer is still on-going. If you remove the player at this point, the songs will not be complete.

---

### Post by austin on 2006-08-28
anaconda: I wish you were right, but unfortunately there could be the "eject-problem" while umount does the job right.

---

### Post by MrHorus on 2006-08-28
> **hashimoto said:**
> You may experience the same phenomena as I do: Nautilus has done all it does and the "Copying files" window closes. Yet, the hardware is still struggling to do its job.

Been there done that - lost quite a bit of data from my iPod from thinking it was finished and not looking for the disc activity icon on the iPod screen.

---

### Post by handy on 2006-08-28
This explains the problems I have had when transfering oggs from Dapper to my GP2X...  & My wife doing the same to her XDA2. (SD cards in both)

Thanks for the info' guys! :cool:

---

