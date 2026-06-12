---
title: "Running from external hard drive"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by dan.s on 2006-11-02
I have an iPod like device (sony nw-a3000) and I wish to use it to boot from. When connected to Windows it appears like a removable hard disk, and I believe it’s formatted in FAT 32. Will installing a Linux distro Ubuntu or other cause me to have to start fiddling around with partitions, obviously I can’t do that or I’ll end up with a rather expensive removable HD that wont play my MP3s. Any tips on booting from USB media?

- Yeah I signed up to get this question answered and being a novice I’ll probably never give back to the community……at least I’m being honest about that.

---

### Post by mo79 on 2006-11-02
When you connect your nw-a3000 and go into the BIOS, are you able to see it as a bootable device? If so, then that can be done.

I don't know much storage space you have on that device, but if it's sufficient it should be fine (min 5GB). Bare in mind though that the file system will change from FAT32 to EXT3 - no need to mess with partitions.
You may want to temporarily unplug power to your hard drive during the install if you don't want GRUB to be written over your Windows master boot record.
After that, you can either dual boot by choosing a boot device from boot menu, or change boot sequence options, or [http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

If you don't like Ubuntu you could easily format it back into a clean FAT32.

PS: No one has to give back to the Ubuntu community, but after a while when you feed your feet you may find you can indeed help others. I've only been with Linux since mid Oct.

---

