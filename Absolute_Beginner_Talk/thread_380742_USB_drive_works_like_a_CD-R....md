---
title: "USB drive works like a CD-R..."
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by zerosystem on 2007-03-10
I'm running Dapper, and I'm having this weird phenomenon with my USB drive.

Say I had my 1gb, empty, freshly formatted USB drive plugged in. I would copy a 200mb file to it. the file itself would be fine and Nautilus would show that there would be about 800mb of free space left. But if I go and delete the file, Nautilus would still show 800mb of free space. Pressing f5 to refresh the window doesn't work, ejecting (unmounting) the drive via Ubuntu and then attempting to remount it gives the error:
```
mount: no medium found

mount: no medium found

error: could not execute pmount
```

I've also tried unplugging the drive after unmounting it, and plugging it back in, but it still doesn't free up the unused space. The only solution that seems to work is to format the drive to recover every bit of space, and then copy my data back onto the drive.

Also, I have another usb drive. My Sandisk Cruzer 1gb won't mount, it shows up but I can't do anything with it. I assume it has to do with the U3 application thing?

---

### Post by nayo on 2007-03-10
I dont know thw answer to your question - sorry - but I just want to add that my U3 Cruzer works fine -- it just shows up as 2 different mounted drives, one with the U3 application and the other with my data.  Good luck!

---

### Post by george29 on 2007-03-10
When  you delete a file on your usb stick in nautilus, it gets moved to a folder called .trash on the usb drive. In order to recover the space you need to make sure .trash is empty.

normally with my dapper install all my usb drives automount, when i delete a file it gets sent to .trash. right clicking on the waste bin icon (bottom right of the screen) and then selecting empty waste bin works fine.

to remove the drive /place/computer then right click on the drive and select eject.

---

### Post by Crooksey on 2007-03-10
Im not sure if .trash is always visible.

If you open a terminal and cd into where the drive has been mounted, lets say.. /media/usb

```

$ cd /media/usb
$ ls
.trash
$ cd .trash
$ sudo rm *

```

---

### Post by mike555 on 2007-03-10
Just for everyones info, those Sandisk U3 drives can be cleared of the U3 partion by going to the Sandisk site and downloading a small program to get rid of U3 ... it must be done on a Windows machine , but then you wont get U3 problems on Linux or Mac....

---

### Post by zerosystem on 2007-03-10
Ahh, thanks..

The terminal won't show the trash folder on the usb drive with the command 'ls', but I can now just ctrl+h and delete anything in the folder.

---

