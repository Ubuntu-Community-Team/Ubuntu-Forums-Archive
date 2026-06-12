---
title: "[SOLVED] updating confusion"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Tiemen on 2007-08-30
Hi everyone,
Yesterday I installed Ubuntu on my laptop using the CD installation. It shares the hard drive with W XP. Ubuntu worked immediately and as a first time user  I am impressed with the system. Then the Update Manager advises me that there are 117 updates available. Being new I did not know if all of these were/are needed. I went ahead, downloaded (147M) and they installed auto.
Restarted the machine and found a different start up screen, insofar as that there is now an extra Ubuntu Kernel (2.6.20-16) as the first choice for startup. Started this one and found that everything had slowed down to such an extent that it is virtually unusable. Also my wireless network was not detected and not working. Rebooted the machine and started up the initial installation (2.6.20-15) and this works fine plus it advises me that there are no new updates.
Can someone help please?

---

### Post by ARandomKid on 2007-08-30
Is your initial install 7.04 or something lower?

Because you might've accidentally downloaded Fiesty and that can REALLY slow down things on some older computers...so I've heard.

---

### Post by Tiemen on 2007-08-30
Initial install was 7.0.4.
Thanks
T

---

### Post by dpar on 2007-08-30
Until you get the problem with the new kernel sorted out, theres nothing wrong with using the old one.

---

### Post by Tiemen on 2007-08-30
Is it possible to delete the new Kernel or would that do away with all the updates?
Ta
T

---

### Post by Nekiruhs on 2007-08-30
> **Tiemen said:**
> Is it possible to delete the new Kernel or would that do away with all the updates?
Ta
T

You don't want to delete it, just remove it from the menu. Open a terminal and copy&paste:```

gksudo gedit /boot/grub/menu.lst
```
(Use right click to copy&paste, control - C doesnt work in terminal)
Then put a # (a hash) in front of the lines that reference the -16 kernel.
They will look like this:
```
title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=3b45b6f8-7ecc-48c4-875e-a3c13c0ebaf7 ro quiet splash vga=791
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=3b45b6f8-7ecc-48c4-875e-a3c13c0ebaf7 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

```
Make them like this:
```
#title           Ubuntu, kernel 2.6.20-16-generic
#root            (hd0,0)
#kernel          /boot/vmlinuz-2.6.20-16-generic #root=UUID=3b45b6f8-7ecc-48c4-875e-a3c13c0ebaf7 ro quiet splash vga=791
#initrd          /boot/initrd.img-2.6.20-16-generic
#quiet
#savedefault

#title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
#root            (hd0,0)
#kernel          /boot/vmlinuz-2.6.20-16-generic #root=UUID=3b45b6f8-7ecc-48c4-875e-a3c13c0ebaf7 ro single
#initrd          /boot/initrd.img-2.6.20-16-generic

```
Any line beginning with a # is ignored by GRUB and is a comment to the reader. This way, if you break the -15 kernel, you can still reverse the process and use the -16 kernel until you get it fixed.

---

### Post by Tiemen on 2007-08-30
Thanks very much, that works fine. Can I now swap the entries on the start up screen around so (2.6.20-15) is the first entry on the menu so the system starts auto with this one?
T

---

