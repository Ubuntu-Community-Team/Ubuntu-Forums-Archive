---
title: "[SOLVED] booting grub to a dos partition"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by percy_vere_uk on 2008-02-11
Hi

I have my hard disk divided into 2 equal partitions I am running gutsy in one half and windows xp in the other. I am going to do away with xp and format this area for running dos programs. I see that the grub menu allows for 'other operating systems'. How can I set up grub to take me into this dos partition and also can I set this system up to boot from a dos bootable usb memory stick. My bios version does not seem to support usb booting.

percy

---

### Post by dstew on 2008-02-11
You can probably boot a DOS system by chainloading, just like you boot XP. As long as the DOS boot loader is in the boot sector of a partition, the same commands that boot XP should work. See the [DOS/Windows section of the grub manual]("http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows"). Here is the part about [chainloading]("http://www.gnu.org/software/grub/manual/grub.html#Chain_002dloading").

After you get rid of XP, how do you plan on installing a DOS system into the partition? I think if you use the fixboot command from the Windows XP recovery console, you can make the partition bootable.

---

### Post by percy_vere_uk on 2008-02-12
dstew

I will have a look at the grub manual and see if I can work it out from that. At the moment I have no idea how to how to get dos to run on this partition,  

Some time ago xp fell over and I had to do a re-install it caused me all sorts of problems corrupted bios for one thing. Now i have ubuntu up and working with adsl and not dial up i really have no desire to use xp anymore. I have tried  to move away from windows for years and at last have the opportunity!

Thanks for your help on this.

percy

---

### Post by dstew on 2008-02-12
I remember that to format a bootable DOS partition, you use the DOS command **format /s C:** or whatever the partition name is. Maybe check that with the DOS manual first, but that is what I remember.

---

