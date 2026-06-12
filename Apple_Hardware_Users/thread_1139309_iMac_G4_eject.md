---
title: "iMac G4 eject"
date: 2009-04-26
forum: Apple Hardware Users
---

### Post by fraterf93 on 2009-04-26
How do I open my cdrom drive to insert a disc while booted in Ubuntu?  This is an iMac G4.

---

### Post by tiresia on 2009-04-27
```
eject
eject -t
```
But you can configure your keyboard. In Gnome System > Preferences > Keyboard Shortcuts

---

### Post by roym4 on 2009-04-29
to eject a disk or open the drive try the eject button on your keyboard.

or right click (F12 plus click for a single button mouse) on the icon for the disk or drive and select eject from the context menu

or reboot the computer and hold down the mouse button while it reboots

or from a terminal try sudo eject /dev/hdc

---

### Post by GhostDawg on 2009-07-25
> **roym4 said:**
> to eject a disk or open the drive try the eject button on your keyboard.

or right click (F12 plus click for a single button mouse) on the icon for the disk or drive and select eject from the context menu

or reboot the computer and hold down the mouse button while it reboots

or from a terminal try sudo eject /dev/hdc
Hmmm, I just bought an iMac G4 yesterday and was thinking the same thing on how to open the cd drive door.

Thnx.

---

