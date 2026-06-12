---
title: "[SOLVED] How add item to kernel line in grub"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by victorbrca on 2007-03-18
Hi all,


  I want to add an item to my kernel line in grub. Can someone help me with this??

  This is what I have:

```
title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

```


So, should I add it to the first kernel as this:

```
title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash **selinux=0**
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot
```


Thanks,


Vic.

---

### Post by dstew on 2007-03-18
Use a text editor, and edit the file /boot/grub/menu.lst. For example, open the terminal and at the prompt type:

gedit /boot/grub/menu.lst

Put the statement on the line you want, save, and reboot.

---

### Post by Kobalt on 2007-03-18
If you want to add an option to the boot command that's how it should look like yes... But I suggest you try that out on your 2.6.17-10 kernel before you do on your current one, just in case it messes up.

---

### Post by victorbrca on 2007-03-18
> **Kobalt said:**
> If you want to add an option to the boot command that's how it should look like yes... But I suggest you try that out on your 2.6.17-10 kernel before you do on your current one, just in case it messes up.

 Sorry for my lack of knowledge, but I thought the older Kernel was only there for reusing purposes... Is it actually still being used by the system??

Tanks,

Vic.

---

### Post by Kobalt on 2007-03-18
If you didn't uninstall it's packages (linux-image, linux-headers, etc.) then yes you can still use it, but your system uses one kernel at a time, that one being the newer.

---

### Post by dreadlord_chris on 2007-03-18
> **victorbrca said:**
> Sorry for my lack of knowledge, but I thought the older Kernel was only there for reusing purposes... Is it actually still being used by the system??

Tanks,

Vic.

You will boot to whichever kernel you choose at the GRUB menu

---

### Post by victorbrca on 2007-03-18
Thanks a lot guys...

  This was a attempt to patch another problem that I'm having, but unfortunately it did not work....

  New information however assimilated... That's gotta be a gain!!  :)



Vic.

---

