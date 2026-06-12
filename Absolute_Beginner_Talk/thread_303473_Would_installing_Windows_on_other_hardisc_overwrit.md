---
title: "Would installing Windows on other hardisc overwrite Grub?"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-11-20
Pretty much what the titile says..

Im thinking about installing windows on a seperate hardisc, so I can play some games..  will this overwrite grub?

Thanks!

---

### Post by Bachstelze on 2006-11-20
No, it will overwrite only the MBR of the drive you install Windows on.

---

### Post by rigol on 2006-11-20
It will overwrite the MBR of the first harddisk and so GRUB.

---

### Post by jhenager on 2006-11-20
> **rigol said:**
> It will overwrite the MBR of the first harddisk and so GRUB.

That's been my experience. M$ wants everything. Install it first, then Linux.
Otherwise, disconnect your Linux HD and run your Windows install. Then use F12 (Dells) or F8 (equivalent key on my PC Chips m/b) before the OS starts to load to select the device to boot from.

---

### Post by aktiwers on 2006-11-20
Damn crappy windows..  it even overwrites the MBR when its installed on a different HD..  ?

Hmm ok thanks guys..
Anyone have a link to a guide about how to restore Grub after this?

---

### Post by Dr. Nick on 2006-11-20
This should help you
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
 
as mentined earlier you may be able to unhook the linux drive now and then grub wouldnt be overwritten, you would just have to add windows to the grub list to be able to boot into it

---

