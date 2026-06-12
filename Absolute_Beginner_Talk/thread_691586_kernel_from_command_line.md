---
title: "kernel from command line"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by lance bermudez on 2008-02-08
old computer has no gui because I'm trying to learn linux. want to update the kernel from linux-image-2.6.15-23-386 (from dapper) to kernel.org's 2.6.24 this i what i have been doing

sudo bash
cd /usr/src
wget [http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.24.tar.bz2](http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.24.tar.bz2)
wget [http://kernel.org/pub/linux/kernel/v2.6/patch-2.6.24.bz2](http://kernel.org/pub/linux/kernel/v2.6/patch-2.6.24.bz2)
tar -vxjf linux*.bz2
ln -s linux-2.6.24 linux
cd linux bunzip2 -c /usr/src/patch*.bz2| patch -p0
cp /boot/config-2.6.15-23-386 .config && make oldconfig
make menuconfig (to configure the kernel i load the old kernel in .config and save the changes to .config)
make-kpkg clean && make-kpkg -initrd -revision=386 kernel_image kernel_headers && dpkg -i *.deb

when i restart the kernel errors out or freezes. before i restart i see in the leftover stuff a mesage saying that their is no initrd.img and starting from scratch. i have installed build-essential bin86 kernelpagckage libqt3-mt-dev libncurses5-dev libncurses5 libqt3-headers

---

### Post by lance bermudez on 2008-02-08
sorry i missed typed
make-kpkg clean && make-kpkg -initrd -revision=386 kernel_image kernel_headers && cd .. && dpkg -i *.deb

---

### Post by lance bermudez on 2008-02-08
still not working any one have any idea as to why it is not working

---

### Post by RussellGee on 2008-02-08
Sorry, cant help you.

I dont understand why you have posted this here, kernel upgrades arent exactly beginners material.Mabey a move would get you an answer.

---

### Post by lance bermudez on 2008-02-08
i posted this here because it is new to me using the command line this much if i could use kernel check i would. im new to this it is not like i know what im doing. but thank you for your reply

---

### Post by lance bermudez on 2008-02-09
ok before i restart i see this after installing the .debs
setting up kernel-headers-2.6.24 (586cu)
/usr/src/kernel-headers-2.6.24/include/asm-i386 does not exist

setting up kernel-image-2.6.24 (585cu)
/initrd.img does not exist. installing from scratch, Eh?
Or maybe you don't want a symbolic link here. Hmm? Let See
/vmlinz does not exist. Install from scratch, Eh?
Or maybe you don't want a symbolic link here. Hmm? Let See
searching for grub installation directory ... found : /boot/grub
testing for splash image ... none found, skipping ...
found kernel: /boot/vmlinuz-2.6.24
found kernel: /boot/vmlinuz-2.6.15-23-386
found kernel: /boot/memtest86.bin
updating /boot/grub/menu.lst ... done

after reboot i get alot of I/O resource  not free and error ports already in use and it drops into a shell

---

### Post by tormod on 2008-02-09
> **lance bermudez said:**
> 
sudo bash
cd /usr/src
wget [http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.24.tar.bz2](http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.24.tar.bz2)
wget [http://kernel.org/pub/linux/kernel/v2.6/patch-2.6.24.bz2](http://kernel.org/pub/linux/kernel/v2.6/patch-2.6.24.bz2)

The patch is for upgrading from a 2.6.23 tree. You don't need it since you have downloaded the complete 2.6.24.

> 
tar -vxjf linux*.bz2
ln -s linux-2.6.24 linux
cd linux bunzip2 -c /usr/src/patch*.bz2| patch -p0


Here there should have been a ";" or "&&" after "cd linux". Since you don't need the patch it doesn't matter.

> 
cp /boot/config-2.6.15-23-386 .config && make oldconfig
make menuconfig (to configure the kernel i load the old kernel in .config and save the changes to .config)
make-kpkg clean && make-kpkg -initrd -revision=386 kernel_image kernel_headers && dpkg -i *.deb

when i restart the kernel errors out or freezes. before i restart i see in the leftover stuff a mesage saying that their is no initrd.img and starting from scratch. i have installed build-essential bin86 kernelpagckage libqt3-mt-dev libncurses5-dev libncurses5 libqt3-headers
Check that there really is an initrd in / or /boot and that it is referenced in /boot/grub/menu.lst

Compiling a 2.6.24 kernel for Dapper is not the easiest thing if you have no experience. Try first if you can install the Hardy 2.6.24 kernel packages in your Dapper. Or install Hardy!

---

