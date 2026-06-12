---
title: "ubuntu only on mac book"
date: 2006-09-24
forum: Apple PPC Users
---

### Post by goneskiing on 2006-09-24
Since I don't care about OSX, I just tried to load only ubuntu on macbook Pro - I deleted all partitions and created new "/" "swap" and "/home" - install completed with exception of bootloader (it failed loading elilo).   I followed other threads and tried to load a patched grub_0.97-1ubunutu10_i386 - but when I ran "grub-install /dev/sda"  got an error "/boot/grub/stage1 not read correctly"   

Any ideas what to do ?  thks

---

### Post by Asgaard on 2006-09-24
[here](http://bin-false.org/?p=17) is an installation guide that covers installing lilo. all the guides i've seen so far go with lilo, not sure about the situation with efi booting.

---

### Post by goneskiing on 2006-09-25
I installed Lilo and added a lilo.conf but when I try to run "lilo -b /dev/sda"  I get the following error:  ignoring entry boot" warning 'proc/partions' does not match '/dev" directory structure

my lilo.conf file looks like: 
boot=/dev/sda1
default=ubuntu
map=/boot/map
delay=20
image=/vminuz initrd=/initrd.img
root=/dev/sda1

when I run parted I see that sda1 is bootable

I am reaching the end of the line to use the mac.  any help appreciated.

---

### Post by ZERO_SHIFT on 2006-09-25
I think that you should have a OS X partition on your mac in order to run it, and also in order to get firmware updates.

---

