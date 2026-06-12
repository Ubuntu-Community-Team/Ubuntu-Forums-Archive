---
title: "upgraded to feisty, wont boot now"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by outer_space on 2007-05-05
I left my computer on overnight to upgrate to feisty.  When I woke up the computer was off.  And it wont boot.  If I start in safemode, it mounts root filesystem, then it waits for root filesystem forever.

---

### Post by bodhi.zazen on 2007-05-05
> **outer_space said:**
> I left my computer on overnight to upgrate to feisty.  When I woke up the computer was off.  And it wont boot.  If I start in safemode, it mounts root filesystem, then it waits for root filesystem forever.

Can you boot a live CD and check your hard drive ?

Make sure your partitions are OK.

See if you can mount the root partition from the live CD.

---

### Post by singamayya on 2007-05-05
Perhaps you have a SATA hard drive, where your main hard drive is reported as /dev/sda... instead of /dev/hda...

In this case, at the GRUB boot prompt, press 'e' and change the "/dev/hda..." to "/dev/sda..."  (i.e. change the "h" in hda into "s", so it becomes "sda") in the second line which says "/boot/vmlinuz...".  

Now press 'b' to boot with these modified parameters, and it should work.

To avoid having to do this manual intervention every time your computer boots, edit the /boot/grub/menu.lst file and change all the "hda" to "sda".

Cheers.

---

### Post by outer_space on 2007-05-05
Yes I do have SATA harddrive.  But on all the grub options it is hda not sda, and it boots windows xp with the hda settings.  I tried changing it to sda but it locks up just the same.

---

### Post by outer_space on 2007-05-05
If I wait a long time to boot, it will load the shell with the prompt "(initramfs)"

I ran memory check and that worked without errors.

---

### Post by outer_space on 2007-05-05
So I made a new partition and installing feisty from the iso.  The end.

---

