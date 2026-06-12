---
title: "My boot option for Ubunt is gone!!!!"
date: 2007-08-09
forum: Apple Intel Users
---

### Post by mshale on 2007-08-09
Here's what happened... i have a partition that is supposed to be shared between os x and ubuntu, but i formatted that shared partition ext3... permissions just won't line up (eg i gave everyone permission to do whatever they want to the partition from inside ubuntu), so i went to format it as ext2 to see if that made any difference. So i booted to the Gparted liveCD (becuase the option to erase was grayed out in diskUtil), and proceeded to reformat ONLY THE SHARED PARTITION. I know that i reformatted the right one because i can boot into osx and still see the partitions and what is on them... but when i hold the option key at boot, i only get the Macintosh HD option... Where oh where did my Ubuntu go??

---

### Post by cyberdork33 on 2007-08-09
install refit

---

### Post by mshale on 2007-08-09
> **cyberdork33 said:**
> install refit

Well, I had it working before that... but i'm gonna go try it.  how do i install it? on which partition?

---

### Post by cyberdork33 on 2007-08-09
OSX. There are instructions.

My guess is that removing the partition confuses bootcamp, or that it removed grub from the MBR.

---

### Post by mshale on 2007-08-09
> **cyberdork33 said:**
> OSX. There are instructions.

Sorry, I got all ask questions then search on you... lol well, i just installed it and we'll see if it helps any!  thanks.

---

