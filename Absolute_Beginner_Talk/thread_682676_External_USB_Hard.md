---
title: "External USB Hard"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-01-30
Hello!
When I plug the hard (formatted fat32) to my computer i get this error(attached) What should I do?
+++
In windows also I can't open it with double click and I have to right click and then choose open.
___
Thank you.

---

### Post by BillDozer on 2008-01-30
Have you tried to open it in Windows. Then use the safely unplug method as described in the message. And then plug it in your ubuntu machine again?

---

### Post by emarkd on 2008-01-30
That's an NTFS drive, not fat32.  NTFS is a journaled file system and has to be properly unmounted.  Ubuntu thinks its in use because it wasn't properly ejected in Windows.  There's probably some way you can get around this, but the best way is to allow Windows to properly eject the disk.

---

### Post by white3454 on 2008-01-30
This will force mount the drive in Ubuntu, first you need to create a mount point

> sudo mkdir /media/usb

then type this to force mount the drive

> sudo mount /dev/sdb1 /media/usb -o force


Make sure that your drive is at /dev/sdb1.  To find out type:

> sudo fdisk -l


Once your all done with the drive you will need to unmount the drive, in order for the data to be written:

> umount /dev/sdb1

---

### Post by muteXe on 2008-01-30
Sorry to hijack your thread but i have a question on this line in the last post:

> Once your all done with the drive you will need to unmount the drive, in order for the data to be written:


Do i have the wrong idea about what mounting and unmounting means?  How can you write data do a drive after you've unmounted it?  I thought if you had a memory stick for example you plug it in, mount it, write/read data to/from it, then unmount and unplug.
Sorry for the noob question.
Cheers,
Tom

---

### Post by Hoom@n on 2008-01-30
Thank you. I did so (post #4) and everything worked, but I after "umount /dev/sdb1" i get "umount: /dev/sdb1 is not mounted (according to mtab)" so i tryed right clicking on hard icon and click unmount, but i got this: (attached)

---

### Post by Hoom@n on 2008-01-30
Sorry! How can I unmount it? (see post #6) Please tell me.

---

### Post by emarkd on 2008-01-30
muteX:  In order to prevent excess wear on the drive as well as slower access, Linux caches a lot of the writes to the disk and does the writing in large chunks.  That means if you save a small document and then immediately unplug the drive, Linux may not have flushed that cache to the disk and you file may not really be there.  Unmounting the drive forces that cache flush and guarantees that your data is actually saved.

---

### Post by Atomic Dog on 2008-01-30
You can open the nautilus file browser, right click on the mounted drive and select "unmount"

---

### Post by Hoom@n on 2008-01-30
I don't know why are you tell this!!!
I told that this method doesn't work and that attached image shows what I get when I wanna do this. I'm asking how to force it.

---

