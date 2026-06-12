---
title: "Recovery Disk"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Campingman on 2007-06-20
Hi,

I am having a few difficulties with my XP installation and want to reinstall.  All I have is a return to original recovery disk from where the PC was bought.  I do not want to disturb my Ubuntu installation especially grub.
Does anybody know if these recovery disks overwrite the mbr again to windoze, there is no option to fix mbr when inserted just restore without format and restore with format (the option I want).

---

### Post by overdrank on 2007-06-20
> **Campingman said:**
> Hi,

I am having a few difficulties with my XP installation and want to reinstall.  All I have is a return to original recovery disk from where the PC was bought.  I do not want to disturb my Ubuntu installation especially grub.
Does anybody know if these recovery disks overwrite the mbr again to windoze, there is no option to fix mbr when inserted just restore without format and restore with format (the option I want).

Hi I have only done what you are attempting once and the restore disc formated the whole drive. So I would say that you need to backup you ubuntu system to dvd image or something. Good luck!:(

---

### Post by Benbow on 2007-06-20
I have used recovery discs several times and each time it has formatted the drive. There may be a workaround for this but I haven't found it.
Good luck if you try it but be prepared to install Ubuntu as well.
Sorry.

---

### Post by Campingman on 2007-06-20
Thanks, I thought that was probably the case.
XP is going really slow and I cannot get to the root of it.  I will put up with it till the next release of Ubuntu and do the both together.

---

### Post by buuntuu! on 2007-06-20
that's what recovery discs are intended to do: they set back your hd the way it was when you bought it... there is no way i know of to circumvent the wiping of the whole disc.
you could backup your ubuntu-partition using tar (read [here]("http://ubuntuforums.org/showthread.php?t=35087&highlight=howto+backup") and [here]("https://help.ubuntu.com/community/BackupYourSystem/TAR?highlight=%28system%29%7C%28backup%29"))  which will allow you to restore your system exactly the way it was, but you will definitely have to repair grub, as xp's MBR will be restored by your recovery-cd.

---

### Post by Campingman on 2007-07-20
An update to this:
I eventually bit the bullet and reinstalled XP with the recovery CD with the aim of reinstalling feisty afterwards with partimage.  To my surprise on reboot after installing i went off to get a drink, came back and feisty had loaded.  The recovery disk had not touched the mbr, a little worrying if my windows mbr had been screwed.  I have two hard drives, windows on hda and feisty on hdb, I am beginning to wonder if grub is on hdb.  Would this be possible?

---

### Post by alienexplorers on 2007-07-20
Just use the restore disk.  Remember to save any important data you have in Ubuntu first.  Reload windows and then load ubuntu and it will re-set up grub for dual booting.  Restore your backed up info and your good to go.

---

