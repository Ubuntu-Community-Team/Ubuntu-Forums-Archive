---
title: "Can't Get Back GRUB After Windows 2000 installation"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by freakylinux on 2006-06-27
hi guys,

i have recently joined this forum & hope to give & receive some really good help!!

i installed Ubuntu 5.10, & then for some reasons Windows 2000 after it.
Windows ate my GRUB Loader.
Although i have tried wat is told in the Ubuntu Guide.

i booted in rescue mode using the cd, got into a shell & did this...

sh3.0# grub-install /dev/hda

But this shows an error message....
" The file /boot/grub/stage1 not read correctly":confused: 

What is the problem over here? Am i doing something wrong?:confused: 
Do i need to install Ubuntu again...??

---

### Post by Apple 101 on 2006-06-27
The /boot area was not mounted during the recovery process of GRUB.

In the recovery console:
mount /boot
grub-install /dev/hda

---

### Post by Jagot on 2006-06-27
If that doesn't work then you could try this:

[http://ubuntuos.com/2006/03/howto-restore-grub](http://ubuntuos.com/2006/03/howto-restore-grub)

---

