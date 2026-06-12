---
title: "Disconnecting A Usb Flash Drive"
date: 2005-11-04
forum: Absolute Beginner Talk
---

### Post by lexor on 2005-11-04
I was reading that when you disconnect a USB flash drive you just dont pull it out of the USB slot but must first diconnect the hardware first cause if you dont you may destroy the flash drive as there is still power running to the device.

In Linux is it just a case of unmounting the device or is there more involved, what I mean is when you unmout does all power that gos to the USB drive stop.

thx

---

### Post by Kapre on 2005-11-04
[QUOTE=lexor]I was reading that when you disconnect a USB flash drive you just dont pull it out of the USB slot but must first diconnect the hardware first cause if you dont you may destroy the flash drive as there is still power running to the device.

In Linux is it just a case of unmounting the device or is there more involved, what I mean is when you unmout does all power that gos to the USB drive stop.

thx[/QUOTE]

lexor - What I'm doing is just making sure that device is unmounted before I take it off (this is my MP3 USB).

K

---

### Post by lexor on 2005-11-04
It is sure wise to do so.

One of the guys I work with had a USB pen drive attached to Windows and just pulled it out the next time he tryed to plug it in it was gone/broken only fit for the bin.

I didnt know much about it myself, flash USB pen drives are seen as the modern day floppy drive you just taken it out and put it back in no problems.

I have 2 128mb pen drives and a mp3 player pen drive myself, I used to do the same just uplug and replug now I have second thoughts about it at least before I unmount it first.

---

### Post by mcduck on 2005-11-04
Power isn't  the real problem, USB connector is designed so that it connects/disconnects power the right way. That's why you can connect those flash drives even when your computer is running.

The reason for unmounting is that Linux buffers reads and write operations. So when you copy something to your flash drive, it doesn't mean that the data is actualy writen to the drive. Linux writes it there when the buffer gets full (or you unmount the drive), and if you unplug the drive before that you lose your files.

By the way, unmounting USB drives doesn't cut power from connector, USB ports output 5V when the computer is powered. So if you have some mp3-player that charges from USB, you can unmount it and still leave it connected to charge it's battery..

---

### Post by lexor on 2005-11-04
Its rather a shame if say you have a ipod and pay a few hundred pounds for it and then you may get a voltage spike and destroy the device.

I dont know about the ipod manual but for my own USB drives no such information  about connecting it only when power is off is listed.

So what you are saying is that USB always have +5v running it is just your bad luck if it gets a voltage spike on the device and breaks if by someone dont shuting down the system and then disconnecting the device.

---

### Post by mcduck on 2005-11-04
[QUOTE=lexor]It is sure wise to do so.
One of the guys I work with had a USB pen drive attached to Windows and just pulled it out the next time he tryed to plug it in it was gone/broken only fit for the bin.
[/QUOTE]
They can easily be fixed with linux. First switch off USB drive's automounting (from System/Preferences/remowable drives and media) If you don't do this Linux will have a real hard time trying to mount that drive ;)

Plug the drive, don't mount it but run 'fdisk /dev/sda'  (or where your usb drive is mounted), delete existing partition(s) and create a new FAT or VFAT(FAT32) partition.

---

### Post by lexor on 2005-11-04
Thanks for the info on that, I'll pass on the info or even get the pen drive and see if it can be sorted for the guy.

---

