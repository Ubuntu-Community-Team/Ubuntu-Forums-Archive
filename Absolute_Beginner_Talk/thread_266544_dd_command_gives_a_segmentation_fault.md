---
title: "dd command gives a segmentation fault"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by njparton on 2006-09-27
When I run the following command:

dd if=/dev/hdc0 of=bootsect.lnx bs=512 count=1

to create a bootsect.lnx file that I can copy to the windows partition so that I can dual boot via boot.ini, I get a segmentation fault.

When I try to use bootpart in windows to create a bootsect.lnx file, a file is generated but NTLDR doesn't like it when I try to dual boot.

Is there something wrong with my grub installation?

I can read menu.lst etc OK in Ubuntu.

---

### Post by steve.horsley on 2006-09-27
I have never heard of dd segfaulting before. But I have never heard of a device /dev/hdc0 before either. What device is that?

I can't help with setting up a windows bootloader I'm afraid - I always just use GRUB.

---

### Post by njparton on 2006-09-27
"hdc0" is what I resorted to as "hdc" didn't work...

Something very strange is going on :???:

---

