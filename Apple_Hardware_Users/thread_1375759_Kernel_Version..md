---
title: "Kernel Version."
date: 2010-01-08
forum: Apple Hardware Users
---

### Post by Tuesdays on 2010-01-08
[FONT="Trebuchet MS"]Ok so I am following the guide here on Ubuntu Forums ([http://ubuntuforums.org/showthread.php?t=1327758](http://ubuntuforums.org/showthread.php?t=1327758)) and everything is going great until I get to step 24. It loads the Grub menu, however when I choose Linux to boot, it say's something along the lines of "You must boot kernel first"... 

Can anybody help? Thanks.[/FONT]

---

### Post by linuxopjemac on 2010-01-08
> 
Copy and paste the following into that file (modify for your kernel version)
menuentry "UBUNTU 2.6.31-14" {
# Set the root device for Linux.
fakebios
root=(hd0,3)
# Load the loader. - other options: video=vesafb noefi
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 video=efifb acpi=force
initrd /boot/initrd.img-2.6.31-14-generic
}

Did you use the right kernel version and did you provide the right details as to where the kernel and root is?

---

### Post by Tuesdays on 2010-01-08
I didn't change the Kernel because I don't know what it is and I don't know which bit to change :S

---

### Post by linuxopjemac on 2010-01-08
if you do the exact thing as written, it should work. I guess you missed something then.

if you go into the liveCd...can you show the output of

```
sudo fdisk /dev/sda
```

---

### Post by Tuesdays on 2010-01-08
The exact error that appears is:

Rom image present
Error: You need to load the Kernel first.

---

