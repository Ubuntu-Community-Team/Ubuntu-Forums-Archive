---
title: "Mandriva entry in Ubuntu Grub?"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2007-11-15
Hi all
Installed Mandriva Free 08 just skipped grub part now there is no grub entry what should be the Mandriva grb input so that I can boot through it I installed it in sda1 .. Also is there a way to update a grub so that it can identify and all the missing entry if present in diff .. partition:confused:

Regards

---

### Post by Dark Star on 2007-11-15
Bump.. SSome 1 please help me ;)

---

### Post by eldepeche on 2007-11-15
Did you check on a Madriva site? You might be able to find the default options there. 

Just to boot, you want to mount the Mandriva partition somewhere , for example /media/mandriva , and then run ```
ls /media/mandriva/boot
``` to find out what the path to the kernel is. You'll want to look for vmlinuz-<something> and initrd-<something>. Then just put something like the following at the end of Ubuntu's /boot/grub/grub.conf :
```
title   Mandriva
root   (hdX,Y) #the GRUB name for your Mandriva partition
kernel /boot/vmlinuz-<something> root=/dev/sdXY #the normal name for your Mandriva partition
initrd  /boot/initrd-<something>
```
Without knowing your configuration, I can't tell you exactly what to put, but you get the idea.

There might also be extra kernel options, for example "splash", that Mandriva would add by default.

---

### Post by natehatewindows on 2007-11-15
im doing this tomarrow...i was wondering about this part too. please keep this updated.thanks!!

---

