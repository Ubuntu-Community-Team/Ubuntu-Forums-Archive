---
title: "Mbr Gone"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by morequarky on 2006-12-16
Not again, yeah, don't ask.  There are many threads on here about restoring the master boot record.  Is there a definitive guide to re-installing grub and getting Ubuntu EDGY, not dapper, up and running again.

Does having a small /boot partition help in getting Ubuntu up and running again or not?

Is there a definitive guide to backing up the MBR?  How would one re-install the SAVED MBR if they had one saved?

Thanks.

---

### Post by Bachstelze on 2006-12-16
What would be the use of a saved MBR ? 99% of the people use a standard GRUB. Also, having a separate /boot partition is useful only if you run several Linuxes, so you can boot all of them with the same GRUB more easily.

---

### Post by morequarky on 2006-12-16
> **HymnToLife said:**
> What would be the use of a saved MBR ? 99% of the people use a standard GRUB. Also, having a separate /boot partition is useful only if you run several Linuxes, so you can boot all of them with the same GRUB more easily.

I was forced to reinstall windows on a dual boot system.  I can't boot to Ubuntu anymore.

Saving the MBR may be impossible and pointless for all I know.  
Having a separate /boot may generally be pointless for all I know.

I want to reinstall GRUB and get my Ubuntu working again AND
I would like to be able to get GRUB and Ubuntu up working faster next time if this happens again.

---

### Post by Bachstelze on 2006-12-16
This is really easy :

1. Boot from a live CD

2. Become root : *sudo -i*

3. Create a mountpoint for your root partition : *mkdir /mnt/root*

4. Mount it : *mount -t ext3 /dev/whatever /mnt/root*

5. Reinstall GRUB : *grub-install --root-directory=/mnt/root /dev/whatever*

6. Reboot


And As for having a separate /boot partition, I can tell you it's really useful when you have several Linuxes.

---

### Post by xyz on 2006-12-16
[ HOWTO: Restore GRUB (if your MBR is messed up) - with Install CD]("http://ubuntuforums.org/showthread.php?t=24113")

---

