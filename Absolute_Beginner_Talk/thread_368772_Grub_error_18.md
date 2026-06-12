---
title: "Grub error 18"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by pwrntspd on 2007-02-23
Alright so ive been working on this system for a long time.  I keep getting problems after i install.  When i reboot i get.

GRUB loading stage 1.5.

GRUB loading...please wait...

Error 18

Can someone tell me whats wrong? Or how to fix it?

---

### Post by netkid91 on 2007-02-23
You BIOS doesn't support booting anything past the 1024th Cylinder on the disk.  You need to move (or create) a /boot partition at the beggining of your disk so GRUB can load your kernel.

---

### Post by pwrntspd on 2007-02-23
> **netkid91 said:**
> You BIOS doesn't support booting anything past the 1024th Cylinder on the disk.  You need to move (or create) a /boot partition at the beggining of your disk so GRUB can load your kernel.

Um, hate to be a burden but can you walk me through that?

---

### Post by netkid91 on 2007-02-23
And you solely booting ubuntu or dual-booting?

---

### Post by pwrntspd on 2007-02-23
> **netkid91 said:**
> And you solely booting ubuntu or dual-booting?

Just Ubuntu, actually xubuntu

---

### Post by netkid91 on 2007-02-23
You will need to reinstall your system to do this, sorry.  Go through the install as normal until it hits the partitioning page.  Then, you need to make three partitions.  The first one should be 128MB big, format it as reiserfs (or ext3 if you want, just my personal preference), the second one should be the amount of ram you have *2 (but no bigger than 1GB) and formatted as SWAP, the last one can fill up the rest of the disk, and use JFS or ext3 on it.
When it asks you where to mount them, put the 512MB to /boot, the second can only be swap, and the third to / (root).  After that, it should work.

---

### Post by linux_kid on 2007-02-23
netkid91, sorry, i had to put in my two cents

Just reinstalling should fix GRUB18, as that is all it took to fix it for me

And why would you allot 128mbBIG to /boot ?

---

### Post by pwrntspd on 2007-02-23
Ok thanks, net. As for the reason why...i think i accidentally messed something up when i booted the partitioner...whoops...anyway ill post again when and if this fixes it, thanks again.

---

### Post by netkid91 on 2007-02-23
> **linux_kid said:**
> netkid91, sorry, i had to put in my two cents

Just reinstalling should fix GRUB18, as that is all it took to fix it for me

And why would you allot 128mbBIG to /boot ?

Mine is 512 man!  I know that kernels don't take up much space (usually), but I always try to leave some room for when they start piling up.  Just something I do.

---

### Post by pwrntspd on 2007-02-23
alright guys thanks alot, it finally works.  After two weeks of tinkering the thing finally works....geez that took forever.  Anyway thanks again.:)

---

