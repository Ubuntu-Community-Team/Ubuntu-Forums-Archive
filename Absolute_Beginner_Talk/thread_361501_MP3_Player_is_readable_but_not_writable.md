---
title: "MP3 Player is readable but not writable"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by scwinn on 2007-02-14
I have an MPIO MP3 player 2 gig. It is 25% full. When I plug it in Rhythmbox fires up  as it should. I see the player. I see the files on it. I can copy them. But I cannot write to the device even if I change the write permissions in the "properties" combo box. Why not.??

I have other players that work just fine.

---

### Post by xboxbman on 2007-02-14
try changing the perimssion in terminal after mounting it.  I find the permission box in desktop doesn't always work.  Infact most of the time it doesn't.  But good old dependable terminal does.

sudo chmod 777 /media/usb_drive

should do the trick.  Substitute usb_drive with whatever the mp3 player mounts to.

---

### Post by konst88 on 2007-02-14
What is the file system on the device? If it NTFS you can't write on it without installing additional software.

---

### Post by scwinn on 2007-02-14
Good question. It is FAT (yuck!)

---

### Post by sympeltun on 2007-02-14
If it's FAT then you can simply copy the Mp3's and paste it into the mp3 player (like copy pasting it to another harddrive) once you copy, right click on the mp3 player icon(on the desktop) and eject it, once it ejects you can disconnect.

I use the same method of transfering songs using windows and also ubuntu, both work flawlessly. (for me atleast)

i hope this helps

---

### Post by scwinn on 2007-02-14
That does not work. The message I get is "Cannot copy to device. The device is full." Under windows it is 25% full. Under the properties tag in UBUNTU it is also 25% full.

HELP

---

