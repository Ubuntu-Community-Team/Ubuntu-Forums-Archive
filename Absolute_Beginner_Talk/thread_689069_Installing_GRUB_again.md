---
title: "Installing GRUB again"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by onthefence on 2008-02-06
I have a dual boot scenario on a single laptop drive.
For some reason when I formatted the drive for Linux Installation it messed up the MBR so when Linux installed GRUB doesn't see a windows loader,  Even if it could see Windows loader, I don't think Windows loader is correct to boot to the windows install.

THis means I need to reinstall windows. My question is if their is anyway I can reinstall windows but then reinstall just GRUB so I can get back into my Linux partition as well.

Am I making sense?

Thanks

---

### Post by NightwishFan on 2008-02-06
After you reinstall Windows insert the live cd and reinstall grub, ill hunt the command now. Try "sudo grub-install" without quotes.

edit: [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351") - Should be what you need if that fails.

---

### Post by oedha on 2008-02-06
are you sure the winblows deleted ?
if your winblows still there and your linux too
you can restore the mbr by using xp installation cd from recovery mode and run fixmbr and fixboot
after that restore the grub

---

### Post by onthefence on 2008-02-06
I'll try that. Good point, the Windows installation is fine, just the MBR that got messed up while partitioning for LInux dual boot install.

Thanks to you both for the response.

---

### Post by oedha on 2008-02-06
ok then.....it means you have to boot using winblows installation....choose recoverymode.....after you get something like C:\windows
type fixmbr
then fixboot
restart.....
next....work on your grub

---

