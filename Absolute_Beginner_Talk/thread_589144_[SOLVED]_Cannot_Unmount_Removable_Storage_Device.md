---
title: "[SOLVED] Cannot Unmount Removable Storage Device"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by ShadowMKII on 2007-10-23
I have looked around a bit but have not been able to find any solid information on this. I cannot unmount my USB drive from my computer without receiving a message that states that I cannot unmount the device. Can anyone help me out?

Thank you!

---

### Post by john.nicholls on 2007-10-23
Check that you don't have a file manager or something else using the device.

---

### Post by xyphur on 2007-10-24
I've had this little annoyance with one of my USB enclosures as well... some USB->IDE bridges don't play nice, and end up either not unmounting, or just remount themselves right away.

Solution I found was to manually eject it from a terminal:

> sudo eject /media/disk

...replace /media/disk with the mount point of your device, and blamo, device unmounted.

---

### Post by 3rdalbum on 2007-10-24
Just that it can't unmount, or that a file on the device is busy?

Have you applied all the updates to your Feisty system? The version of HAL that ships with Feisty is buggy; there is an update available in Update Manager and Synaptic that fixes a lot of those sort of problems.

---

### Post by ShadowMKII on 2007-10-25
> **john.nicholls said:**
> Check that you don't have a file manager or something else using the device.

What do you mean by this?

As for the device not being able to be unmounted, it simply says that "The device cannot be unmounted." It is basically as simple as that, even when nothing is running off of the USB. In terms of system updates, I have all of them accounted for thus far, besides for an error I am having with Gutsy that will not allow me to upgrade because of gtkpod.

---

### Post by magicman5421 on 2007-10-25
what they mean is do you have the contents of the drive open in any window. are you looking at what is in the drive? Do you have any programs open that are using the drive? If you're sure that there are no programs using it, you can just unplug it...

---

### Post by ShadowMKII on 2007-10-25
I know for sure that there are no programs using it, I just want to be safe and make sure that I do not lose any data. Is this problem fixed in Gutsy? Are there any other workarounds?

---

### Post by ShadowMKII on 2007-10-26
Well, never mind that! It appears that this problem has been fixed in Gutsy! Thank you for all of your help by the way! It was much appreciated!

---

