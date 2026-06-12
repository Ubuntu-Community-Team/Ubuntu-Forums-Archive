---
title: "I wasnt ready..."
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by devilshaircut29 on 2006-12-15
Well, I tried out Ubuntu on my computer, but I guess I'm just not ready for it.  I'm really not as computer savvy as I would like to be, which has held me back with Linux.  I decided I needed to switch back to Windows, but when I ran my system restore disk (Windows ME) and it finished installing and I rebooted, it said Loading GRUB please wait... and then said Error 17.  I read up on it a bit, and it sounds to me like GRUB is something Ubuntu uses?  My system restore disk is supposed to clear off all of the hard drive before reinstalling Windows, but it sounds like it didnt.  Can anyone help me fix this problem?  Right now I am still using Ubuntu, but from the test portion of the installation disk.

---

### Post by dbott67 on 2006-12-15
Boot from your Windows CD and get to a DOS prompt.  At the DOS prompt type:
```
fdisk /mbr
```
This will overwrite the Master Boot Record.

-Dave

---

### Post by po0f on 2006-12-15
devilshaircut29,

Is there no way to restore the MBR from the system restore utilities that came with your computer?

(If all else fails, you *can* get GRUB to boot Windows.  :))

---

### Post by crispy_420 on 2006-12-15
Worst case situation, you can completely erase your hard drive. There is a good, small distro to do that called Darik's Boot & Nuke.

That will erase all and start from a raw disc. There may be an easier solution but I have used it in a pinch when I don't care about the data and want a fresh disc.

---

