---
title: "Unbuntu won't shut down"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by Smith101 on 2007-09-20
I hate to be a pain, I just installed Ubuntu and while everything runs great and super fast I might add. The only problem is the PC won't shut down, it just sticks on the shut down screen.

Thanks

---

### Post by arkara on 2007-09-20
ok go to the terminal and type and type:

sudo gedit /boot/grub/menu.lst

and remove quiet splash
look:

## ## End Default Options ##

title		Ubuntu Linux, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic ***_root=UUID=dff38c85-4c27-4138-888a-9bfe1b07941b ro splash acpi=off_***
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu Linux, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=dff38c85-4c27-4138-888a-9bfe1b07941b ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu Linux, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=dff38c85-4c27-4138-888a-9bfe1b07941b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu Linux, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=dff38c85-4c27-4138-888a-9bfe1b07941b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu Linux, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		CRAPYsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

see the highligted area
i have chosen acpi=off and made quiet splash to splash
now you must delete the quiet splash save and then reboot
so you can see if there is any problem during startup
btw quiet splash hides from you the processes that happen during startup
and by deleting ti you can see them..
now shut down your pc and see if there is anything wrong..
if it says
***_system will now halt and then system halted. its ok to power off by hand and its propably acpi problem_***

now if during shutdown ubuntu shows other prosecces post them here to see if i can help you further
dont be afraid toask any questions

---

### Post by Smith101 on 2007-09-20
Thanks for this.:)

---

