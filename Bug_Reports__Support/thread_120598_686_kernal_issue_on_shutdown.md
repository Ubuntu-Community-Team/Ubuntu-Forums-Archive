---
title: "686 kernal issue on shutdown"
date: 2006-01-22
forum: Bug Reports / Support
---

### Post by Brigrat on 2006-01-22
I recently upgraded my 386 kernal to the 686 to take advantage of the smp capabilities.  My problem is that now when I go to shut down the machine it gets to the bottom of closing the modules etc.  it stops at powerdown and then just sits there.
     I followed the one post (don't have it in front of me) that said to add "apm" to the /etc/modules and that should work.  All it did was keep rebooting the machine, after I manually powered it down.
     Then I tried adding the following to the /boot/grub/menu.lst file  "acpi=off apm=off" as indicated.

title     Unbuntu, kernal 206012-10-686-smp
root     (hd0,0)
kernal  /boot/vmlinuz-2.6.12-10-686-smp root=/dev/sda1 ro quiet splash acpi=off apm=off
initrd   /boot.initrd.img-2.6.12-10-686-smp
savdefault
boot


With the 386 kernal the system shut down as it should, with the 686 it does not.  HELP PLEASE!!!!

---

### Post by Mez on 2006-02-09
not a backport issue - please use support forums

---

### Post by Nightwind on 2006-02-14
[QUOTE=Mez]not a backport issue - please use support forums[/QUOTE]
It's been posted in the desktop support forums for over a month now. I haven't posted it too because his problem is the same as mine. Where would you suggest we post it since we cannot get any support from desktop support over this shutdown issue? Some guidance would be  much appreciated, please point us to the forum that we might get a response from.
Thanks a million

---

