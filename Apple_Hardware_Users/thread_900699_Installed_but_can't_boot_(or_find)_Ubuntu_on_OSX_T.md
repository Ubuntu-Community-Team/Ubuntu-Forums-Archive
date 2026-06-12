---
title: "Installed but can't boot (or find) Ubuntu on OSX Tiger!"
date: 2008-08-25
forum: Apple Hardware Users
---

### Post by fatiSar on 2008-08-25
I installed Ubuntu properly (with the help of the technical support staff at my school) on my MacBook with Tiger but I can't find it to boot from. When I hit Option from reboot and it takes me to the startup menu I only have the option to boot from OSX. And in disk utility it shows the partitions I made for Linux (both the root and swap) but they're grayed out and I can't make them bootable. Any suggestions?

---

### Post by cyberdork33 on 2008-08-25
> **fatiSar said:**
> I installed Ubuntu properly (with the help of the technical support staff at my school) on my MacBook with Tiger but I can't find it to boot from. When I hit Option from reboot and it takes me to the startup menu I only have the option to boot from OSX. And in disk utility it shows the partitions I made for Linux (both the root and swap) but they're grayed out and I can't make them bootable. Any suggestions?

Install refit.
See if your linux install shows up there
If not, sync the partition tables with the partition tool in the refit menu.

---

### Post by fatiSar on 2008-08-25
I installed refit and linux did show up there but it still won't boot. It just shows me the linux icon and freezes on that. I also synced the partition tables with the tool and still nothing.

---

### Post by cyberdork33 on 2008-08-25
well at least it sees your linux partition.

You probably need to reinstall grub. This can be done from the Ubuntu LiveCD. I am pretty sure that your problem is due to a bug in the installer. Boot the LiveCD and open a terminal.

```
sudo grub
```You will then get a "grub>" prompt. You need to enter these commands:
```
find /boot/stage1
```This will return a code that is in the format that grub uses to name partitions and hard drives. It should look something like (hd0,2). Now using this code that you found, do
```
root (hd0,2)
``````
setup (hd0)
```Leave the comma and the last number off of the setup command. This will install grub to the MBR of your hard drive.
Now, exit
```
quit
``` and reboot into your system.

---

