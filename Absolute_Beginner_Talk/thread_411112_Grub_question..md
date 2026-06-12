---
title: "Grub question."
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by denysy1 on 2007-04-16
Hi,

I am trying to install grub after booting from live cd (I had to reinstall Vista, and it removed grub).

When i do 

sudo grub-install /dev/sda3

I get 
"Could not find device for /boot: Not found or not block device".

Same if I try any other partition.

If I try to "sudo grub-install --root-directory=/boot /dev/hda"

I get "/dev/hda: Not found or not a block device"

Am I doing something wrong? Please help.

---

### Post by dstew on 2007-04-16
Assuming your Ubuntu Linux installation is on /dev/hda2, and you want to boot /dev/hda, and that /dev/hda = (hd0), you could also use grub itself to re-install. From a Live CD terminal enter:

sudo grub
grub> root (hd0,1)
grub> setup (hd0)
grub> quit

Then reboot.

---

