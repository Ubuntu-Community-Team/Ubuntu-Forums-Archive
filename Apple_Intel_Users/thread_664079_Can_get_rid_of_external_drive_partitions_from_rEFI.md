---
title: "Can get rid of external drive partitions from rEFIt menu?"
date: 2008-01-10
forum: Apple Intel Users
---

### Post by PaulFXH on 2008-01-10
I have a heavily partitioned (16 partitions) usb HDD hooked up to my MacBook and it works fine.
However, one big problem is that every single one of the external drive's partitions shows up on the rEFIt menu when I start up the Mac.
Unfortunately, not one of these partitions are bootable from rEFIt (although a few are from the grub menu). 
So, I would like to get rid of them as they serve absolutely no purpose.
However, it appears that /efi/refit/refit.conf offers no options to "hide" the external drives partitions.
Is there any other way I can remove this unsightly mess from the rEFIt menu?
Thanks
Paul

---

### Post by cyberdork33 on 2008-01-11
> **PaulFXH said:**
> I have a heavily partitioned (16 partitions) usb HDD hooked up to my MacBook and it works fine.
However, one big problem is that every single one of the external drive's partitions shows up on the rEFIt menu when I start up the Mac.
Unfortunately, not one of these partitions are bootable from rEFIt (although a few are from the grub menu). 
So, I would like to get rid of them as they serve absolutely no purpose.
However, it appears that /efi/refit/refit.conf offers no options to "hide" the external drives partitions.
Is there any other way I can remove this unsightly mess from the rEFIt menu?
Thanks
Paul

As far as I know there is no way to remove only certain OS icons in rEFIt. This might be something to being up as a request to the developers of rEFIt.

---

