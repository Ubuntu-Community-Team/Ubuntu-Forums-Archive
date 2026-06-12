---
title: "Installing XP AFTER ubuntu!!"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by galego on 2006-09-05
i would like to install xp into a separate (clean HDD). i already have ubuntu installed and also Vista. both in the primary drive. what i would like to know is i install to the second HDD will XP overwrite the whole MBR and force me to re-install everything else? can i just install to the second HDD and not have XP overwrite the MBR?

---

### Post by MiThRaZoR on 2006-09-05
You could just install to your second HDD and not worry about it messing with your first HDD.

If that's what you mean.

---

### Post by szf on 2006-09-05
Past experience tells me that two things will occur:
1. Windows always expects to be the first partition on the first hard drive - you're going to have to swap the drive Master/Slave order.
2. Windows will always overwrite the MBR. Note that with point 1, above, the "old" MBR will be in hibernation on the Slave drive. You should be able to install GRUB to the Master MBR then.

---

### Post by jISh on 2006-09-05
It will overwrite the MBR, but it's very easy to re-install GRUB right away after. Just set up your /boot/grub/grub.conf and boot into Ubuntu's LiveCD, mnount the filesystem with chroot and type grub-install dev/hd0.

---

### Post by szf on 2006-09-05
[Here's]("http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+MBR") a GRUB installation thread.

---

### Post by galego on 2006-09-05
szf, i have two SATA drives so i can specify which to boot from in the bios or change order from CMOS set-up.

jISh, 
Just set up your /boot/grub/grub.conf and boot into Ubuntu's LiveCD, mnount the filesystem with chroot and type grub-install dev/hd0.

i did not fully understand, i think you mean that i can boot with live CD and the re-install grub to dev/hd0. i did not follow the set up part. i dont have to physicaly configure anything right?

---

