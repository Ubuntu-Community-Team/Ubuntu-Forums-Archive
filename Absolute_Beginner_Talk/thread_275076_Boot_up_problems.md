---
title: "Boot up problems"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by jrod101 on 2006-10-10
I'm new to Ubuntu and Linux in general... so bare with me please...

I've recently install Ubuntu on my Notebook and it run great, except for a random boot problem.  My notebook posts and then just goes to a blinking cursor, it won't boot past that.  If I reboot the computer a half a dozen time or so, it will boot.  I thought at first this may be a hardware problem, but I didn't have this problem with Windows XP on this notebook.  I've reinstall Ubuntu several times trying to correct the problem with no change.  I've even gone at far to download and install Suse and it doesn't seem to have the same issue.  

Has anyone else run into this?  I'd really appreciate some help.

THANKS!

---

### Post by dmizer on 2006-10-10
i can't see how suse and ubuntu would be different unless you're using lilo as your boot manager in suse.  at the post level, functions are pretty basic and almost independant of operating system.

it could be that your install of grub is stuffed somehow.  result of a bad/high speed burn of ubuntu, or a glitch in the install?

try turning off the boot splash for ubuntu:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo edit /boot/grub/menu.lst
```
find the section that looks like this:
```
title           Ubuntu, kernel 2.6.15-27-686
root            (hd0,0)
kernel          /vmlinuz-2.6.15-27-686 root=/dev/mapper/Ubuntu-root ro linux noapic pci=noacpi quiet splash
initrd          /initrd.img-2.6.15-27-686
savedefault
boot
```
remove the "quiet" and "splash" ... save, restart.  i really don't have a whole lot of hope for that, but it's worth a shot, and might give you a bit more information.

if your system will no longer boot at all (grub errors), boot to your live cd and replace the new menu.lst with the backup copy:
```
sudo mv /boot/grub/menu.lst_backup /boot/grub/menu.lst
```

if you're dual booting with windows, your treading on dangerous ground.  before you take actions at this level, really make sure you know what you're doing, and if not ... make sure you have backups.

---

