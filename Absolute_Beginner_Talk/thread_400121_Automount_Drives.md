---
title: "Automount Drives"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-04-03
When I first started using Ubuntu, I could plug in a usb drive, and it would automatically mount it. It might not give me the ability to write to it (NTFS), but it would still mount it. Now, I have to issue the mount commands from the terminal. Would the fact that I added a line to my /etc/fstab file to mount my ntfs drive have anything to do with this? How can I enable the automount feature again. Thanks.

---

### Post by 3rdalbum on 2007-04-03
Adding a line to the Fstab to try to mount your NTFS pen drive is almost certainly the cause. I once tried to add a removable drive to the fstab and it caused that drive to stop automounting.

Get rid of the line, or simply comment it out (put a hash character # in front of the line), save your changes, log out and then back in again.

---

### Post by nhandler on 2007-04-03
> **3rdalbum said:**
> Adding a line to the Fstab to try to mount your NTFS pen drive is almost certainly the cause. I once tried to add a removable drive to the fstab and it caused that drive to stop automounting.

Get rid of the line, or simply comment it out (put a hash character # in front of the line), save your changes, log out and then back in again.

I'd do that, but I hate having to enter in the long mount command to be able to write to my ntfs drive. Is there any way to enable writing to ntfs drives AND automatically mount the other drives?

---

### Post by Ani_linux on 2007-04-05
Hi

I am using Ubuntu 6.06, I have configured the automount for USB with the following

file [FONT="Courier New"]/etc/auto.master[/FONT]:

[FONT="Courier New"]/mnt       /etc/auto.removable  --timeout=60[/FONT]

file [FONT="Courier New"]/etc/auto.removable[/FONT]:

[FONT="Courier New"]usb        -fstype=vfat                 :/dev/sda[/FONT]

When I insert the USB drive, I can see it mounted in [FONT="Courier New"]/mnt/usb[/FONT],
but it doesn't unmount after the timeout!, also I dont see the icon on Desktop.
Is there any other change I am missing?

--
Thanks

---

