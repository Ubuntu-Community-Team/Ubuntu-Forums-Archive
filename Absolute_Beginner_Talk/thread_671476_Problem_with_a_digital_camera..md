---
title: "Problem with a digital camera."
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by nemodot on 2008-01-18
Hi, im having a problem with my new digital camera, a Panasonic Lumix DMC-LZ7.

When i bouht it, and connected to my pc using ubuntu 7.10 there was no problem, but one day, suddently when i plug the usb there was this error:

[IMG]http://img152.imageshack.us/img152/2392/cameravm8.png[/IMG]

In english says "There was an error on the input-output library. Unespecified error, it is not available the description of the error"

What happened?

---

### Post by pytheas22 on 2008-01-18
could the memory on your camera be corrupted?  Maybe you should see if you can plug it into another computer or not.

---

### Post by nemodot on 2008-01-18
Nein, its working well on Windows.

I think the libraries are ****** up. But i dont know how to solve this.

---

### Post by pytheas22 on 2008-01-18
you could take a look at the log file (Synaptic or its backend must keep one but I don't know where it is) and see what updates or other things you installed before the camera stopped working and see if any packages relating to your camera were changed, and then downgrade them to their original versions.  Or you could  pop in the live CD, download all of the updates and see if the camera would work there...although you wouldn't really have *all* the updates if you did that because some wouldn't take effect until after a reboot, which you of course wouldn't be able to do.  But it still might help diagnose the problem if been's caused by an update of a library somewhere.

Other than that, I don't know anything in particular about cameras on Ubuntu, but hopefully somebody else does.

---

### Post by pytheas22 on 2008-01-18
or as an additional thought, try to mount the device as if it were just any other volume...e.g.

```
sudo mount /media/YOURCAMERA /some/mount/point
```

that could get you access to the files on the device

---

### Post by BandD on 2008-01-18
You could try installing (or re-installing) the gphoto2 libraies via Synaptic.  I use gtkam to import photos, I like it better than the defualt Ubuntu photo importer.  You can install that via synaptic as well.

Maybe that will help.

---

### Post by Neobuntu on 2008-03-10
Mass storage with the actual cameras seems to be broken. You can set your camera for PTP (Printer) mode and then setup a program such as Digicam. Plug the cam in as PTP and the Digicam app can set it up automatically in its add camera dialog. You can also remove a card from a camera, put it in a good reader and have mass storage working. 

But what about internal cam memeory? PTP mode will not access the movies in internal memory at all (Olympus did, Panny didn't). 

We really need (internal or card) camera, mass storage fixed. This is the kind of thing that keeps people, sheeple. Let's fix it fast!

Hope the work around helps in the mean time.

---

### Post by Neobuntu on 2008-03-17
Please keep in mind, the Panasonic site states that a format from their camera is somehow different than an on computer (VFAT16 or 32) format. They state the kind of lock-up, unmount and corrupted file (which can also be caused by turning off a FAT files system during a write) that I have seen, can be cause by other than on Camera SD spec formats.

Some camera jocks reformat, to erase. I can imagine a FAT system that is corrupted by turning it off, or less than acceptable format, OR A BAD READER (please note), could be fixed; by an in camera/phone formating. Not on your computer. FYI.  

I also wonder if once one gets to 6GB or greater, which necessitates VFAT32, if this is an automatic slow down (for more VFAT32 overhead) than VFAT16 on SDHC 4GB or less formatted memory cards. No by the way, 2GB is the old FAT16 limit. It's now 4GB with VFAT(16) and the cluster size is automatic, as it is the only one that yields 4GB and VFAT16.

**Edit:** Speed tests on computer show the best results with HC (6GB, 8GB) Flash with the required FAT32 non the less. Faster (or as fast) as any other speed claim so far. BUT,** on your device** it may have a slower time with FAT32. Maybe it's just the access speed; not average write (or read) speed that may slow you down.

---

