---
title: "How to make a boot disk?"
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by icetemplaire on 2005-11-12
Please don't say i only need to put the cd rom and bla blah blah, my pc don't boot WHIt ONLY DISK 1.44 MB, NO CDS. So how do i made a ubuntu boot disk?

---

### Post by grim918 on 2005-11-12
floppy diskettes dont have the storage capacity to hold ubuntu on one of them. it would take hundreds of floppies to get the job done. if your computer has usb ports then you can buy a cd-rom that is usb compatible and use that to get ubuntu onto your harddrive.

---

### Post by xequence on 2005-11-12
Grim, Ice means a floppy that starts the CD. Some older computers cant boot from the CD drive so they boot from a floppy, which in turn uses the CD.

And im sorry but I dont know. Damn Small Linux has one, I dont know if it works with ubuntu though.

---

### Post by livingtarget on 2005-11-12
There should be a boot manager on the disk/iso somewhere. It's somewhere in an image you can write to a floppy to boot your system. I used it when I first installed ubuntu. 

Make sure you use something like rawrite for windows. (which will be able to read the image and burn it to the disk)

BTW, Image is not like a literal image. It's a single file that stores a bunch of files to be written to a cdrom/floppy. Almost like a zip file.

Good luck, hope this helps.

Ok I attached the things I used to install the bootdisk with. Click below to download the attachment (224kb). You will need a windows workstation though.
It contains a zip with sbm.bin which is the bootdisk image. Launch the program rawritewin0.7 and write that file to floppy. When you insert it on boot it will just ask you which drive you want to boot from. Try CDROM and hopefully that works.

---

