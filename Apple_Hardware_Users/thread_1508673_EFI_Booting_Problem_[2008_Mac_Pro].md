---
title: "EFI Booting Problem [2008 Mac Pro]"
date: 2010-06-13
forum: Apple Hardware Users
---

### Post by Ubuntious on 2010-06-13
I'm trying to boot ubuntu on a 2008 Mac Pro the native EFI way. 
grub.efi (renamed as BOOTX64.EFI and placed in /EFI/BOOT on
the hard drive's EFI partition) runs. It claims to have discovered
the framebuffer address and some other details. But when I issue
the 'boot' command I see nothing, though I suspect that Linux is
booting. This is the blind booting scenario.

Some more details. The machine has 64-bit EFI firmware:

```

bash: ioreg -l -p IODeviceTree | grep firmware-abi      
    | |   "firmware-abi" = <"EFI64">
bash: 
```

I am, therefore, using x86_64 grub.efi. I am using a 2.6.34 
self-compiled kernel with all the EFI options and the console 
framebuffer enabled. These are the boot time options I use 
(no error is reported):

```

linux /vmlinuz-2.6.34 video=efifb break=premount
initrd /initrd-2.6.34

```I have tried several versions of grub-mkimage to create
grub.efi, including one built from the latest SVN source. 
Same result with each. 

If I add the kernel option 'noefi' I do see boot messages
up until the point where the kernel panics.

Note: I have been able to boot the same kernel using the
same arguments ('video=efifb break=premount') within a
VMWare virtual machine:

[http://www.youtube.com/watch?v=uPcuo0FRVHE&fmt=22](http://www.youtube.com/watch?v=uPcuo0FRVHE&fmt=22)

That was using BURG.

Any help on native booting would be much appreciated!

Thanks. 

ps The graphics card is an Apple supplied NVidia 8800GT.

---

