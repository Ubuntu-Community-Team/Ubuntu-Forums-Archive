---
title: "Problem with bootloader"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by ezzus on 2006-03-26
Hello everyone!

this is my disk situation:
Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1848    14844028+   7  HPFS/NTFS
/dev/hda2   *        1849        3570    13831965   83  Linux
/dev/hda3            3571        3648      626535    5  Extended
/dev/hda5            3571        3648      626503+  82  Linux swap / Solaris

I had to reinstall windows xp and obviously it deleted my GRUB.
Then I followed some instructions and i re-installed it...
but still it was not working, xp was booting automatically.
To make it work i used the ubuntu installation cd then i changed the boot partition from hda1 (windows) to hda2 (linux) and now it works.
The problem is that every time I run windows it automaticaly configures back hda1 to boot partition so its really annoying.

Can you please help me?

I have a knoppix live cd and a Ubuntu installation one.

Thank you

---

### Post by ubuntuuser on 2006-03-26
I really have no idea what could cause this behaviour, but I would try this:

Boot WinXP, then reboot with Knoppix CD in the drive (<- I don't know if this is necessary, but I would do it just in case)
Boot knoppix
mount hda2, e.g. in /mnt/hda2
type ```
sudo chroot /mnt/hda2 /bin/bash
``` then
```
sudo grub-install
```
Finally```
sudo reboot
```
That should do it. As always, be sure to backup all important things.

---

