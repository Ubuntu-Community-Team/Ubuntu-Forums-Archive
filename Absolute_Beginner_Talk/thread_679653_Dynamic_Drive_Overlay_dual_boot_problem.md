---
title: "Dynamic Drive Overlay dual boot problem"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by nesloaf on 2008-01-27
I installed Ubuntu on my slave HD which needs Dynamic Drive Overlay but the installation wiped out the DDO.  Grub would work and I could boot into both OS but Windows XP would no longer recognize all of the drive.  I restored the DDO but then grub disapeared and it boots into XP directly.

Is there a way to get grub to work after the Dynamic Drive Overlay loads?

---

### Post by forrestcupp on 2008-01-28
I don't think it's possible right now to do that without overwriting the DDO.  I doubt if it will ever be possible because DDO isn't really used much.  One thing you may be able to try is reformatting that hard drive for Windows and installing Ubuntu through [Wubi](http://wubi-installer.org/) which allows you to run Ubuntu from Windows.  I don't know if it would work or not, but it might be worth a try.  At least until you can update your rig with a motherboard that can support bigger hard drives.

---

### Post by nesloaf on 2008-01-29
Thanks forrestcupp for the suggestion of Wubi, I was unaware of this possibility since I'm very new to any Linux.

I did manage to solve the need for the Dynamic Drive Overlay.  I discovered my Seagate 250 GB slave HD was reporting to the BIOS incorrectly.  Seagate's "Seatools" corrected this and the BIOS now sees the HD correctly.  I was then able to remove the DDO and re-install Ubuntu.  The install completed flawlessly (easiest OS I've ever installed) and both XP and Ubuntu are working and I'm ready to start learning.

Thanks,

---

