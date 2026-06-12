---
title: "Flash Drives with Linux"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2006-12-16
If i purchasd a 1GB Flash Drive (USB), would it work OK on Linux?

---

### Post by bodhi.zazen on 2006-12-16
It should. I use flash drives all the time, no problem.

Just plug 'em in and they work :p

---

### Post by Doug11 on 2006-12-16
> **Captain Kirk76 said:**
> If i purchasd a 1GB Flash Drive (USB), would it work OK on Linux?

It should. I have a Sony stick about three years old and Ubuntu picks it up right away.

---

### Post by Captain Kirk76 on 2006-12-16
I have got one, and it works, one question, why is the image the same as a HardDrive, can i change it to one of a Flash Drive (Memory Stick) So it helps me pick it out faster, like my iPod has a mp3 player image.

---

### Post by moshuptrail on 2006-12-16
There is one BIG difference using flash drives on Linux.

You can't just pop 'em out.  Right click and select "eject".  (Or in some cases "unmount")

Linux doesn't flush all the buffered data to the flash drive right away.  So it's easy to copy a file to your flash drive and pop it out before the file actually gets onto the drive.  It will "look" like it's there, but you're just looking at system cache.

---

