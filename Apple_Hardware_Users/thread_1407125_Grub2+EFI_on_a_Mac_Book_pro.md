---
title: "Grub2+EFI on a Mac Book pro"
date: 2010-02-14
forum: Apple Hardware Users
---

### Post by Elv13 on 2010-02-14
Hi,

Anybody recently succeded in installing GRUB2 on Mac OSX partitions? I have to compile in un Fedora/Ubuntu/Gentoo. It work, but once back in OS X, I get this error:

./grub-mkimage -d . -o grub.efi part_gpt hfsplus fat ext2 etx3 ext4 normal sh chain boot configfile linux
-bash: ./grub-mkimage: cannot execute binary file

I tried to build it in Ubuntu 8.04, gentoo and Fedora Rawhide, all fail with the same error. Look like the binary compatiility between OSX and Linux is broken in Leopard.

I would love to have a faster boot, it take half a minute to get to grub, using Grub2 with EFI would take 3 seconds. As I don't need bios emulation, Fedora would also run faster. Anybody have a compiled and working Grub2?

I followed this tutorial:
[http://grub.enbug.org/TestingOnEFI](http://grub.enbug.org/TestingOnEFI)

Is there a better way to use Grub2 with EFI? A working one if possible

OSX: 10.5.8
Linux: Ubuntu 9.10
Mac: MacBook Pro Santa Rosa (3 years old with a Core 2 Duo 2.2ghz)
GCC: 4.2, 4.3, 4.4

---

### Post by sirbats on 2010-02-15
> **Elv13 said:**
> Hi,

==DEL==

Is there a better way to use Grub2 with EFI? A working one if possible

OSX: 10.5.8
Linux: Ubuntu 9.10
Mac: MacBook Pro Santa Rosa (3 years old with a Core 2 Duo 2.2ghz)
GCC: 4.2, 4.3, 4.4

I have been through so many forum and googling, nothing info to speed up booting grub/ubuntu on efi, other than refit and blessing ... :D my big problem I dont wanna to use refit and dont have osx cd installation .... thus my ubuntu solo on MacBook 2.1 booting on 30-45 seconds up to grub appear.

cheers up

---

### Post by pYrO1v1aniac on 2010-06-10
Press and hold option at boot, select the partition marked "Windows". This is a LOT quicker than waiting for the stupid EFI to find your Grub loader.

---

### Post by pattscott on 2010-06-10
I'm not an expert but I might help you...

This is from TestingOnEFI:
> Note that you need to use something else but MacOSX for the compilation, because the gcc shipped with MacOSX is broken by Apple.This means to me you can not use the apple gcc compiler to compile grub2 under OS X. It doesn't mean you can compile in linux and create the grub-mkimage in OS X....

I think you have to get another gcc on OSX. I've installed gcc 4.4 with macports but I can't configure grub2... 
Why do think you have to create the image in OSX and not under linux?
The grub2-efi documentation seems very rough to me.

---

