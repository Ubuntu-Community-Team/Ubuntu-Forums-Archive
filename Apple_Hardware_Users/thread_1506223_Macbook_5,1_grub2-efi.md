---
title: "Macbook 5,1 grub2-efi"
date: 2010-06-10
forum: Apple Hardware Users
---

### Post by pattscott on 2010-06-10
Hi

I've installed grub2 from source and also with the ubuntu grub-efi package with the same result. I moved the grub-mkimage and the mod files to /efi/grub and I start grub2 with refit. Booting OS X works fine, booting linux doesn't work. When I start from linux I get the following output:
```
[Linux-bzImage, set=0x3201,size=0x1f922]
[Initrd, addr=0x4fd6f004, size]
```Then my Macbook freezes. I don't get any error even with the debug=all option. I've got 6 primary partitions (thought I only can create 3 primary partitions?). 1 fat32 efi, mac os x, boot, root, home, swap. I've also tried lvm with the same result.
This is my grub.cfg for linux:
```
menuentry "Linux" {
  root=(hd0,3)
  fakebios
  linux /vmlinuz root=/dev/sda4 video=efifb agp=off noefi
  initrd /initrd
}
```sda3 is my boot partition, sda4 my root partion. I've tried several options with the same result. My Macbook model should work with grub2: [https://wiki.ubuntu.com/KernelTeam/Grub2Testing#fnref-5a5735bce04955a8abfe81bf9ffee12b4bfdd938](https://wiki.ubuntu.com/KernelTeam/Grub2Testing#fnref-5a5735bce04955a8abfe81bf9ffee12b4bfdd938)

I've created the the grub-mkimage several times and tried different modules. 

[I][SIZE=1](I've also tried to compile grub2 on OS X. I've installed gcc4.4 with macports and selected it with gcc_select. When I try to configure I get the following error:
```
checking whether target compiler is working... no
configure: error: cannot compile for the target
```Is the macport gcc version is only 32 bit?[/SIZE][/I])

I'm really clueless about my problem. I appreciate any ideas!

Thanks for your help
pat

---

### Post by pattscott on 2010-06-11
Ok. the situation changed. I'm using a efi file from [http://ubuntuforums.org/showthread.php?t=995704&page=113. ]("http://ubuntuforums.org/showthread.php?t=995704&page=113")
Now I can boot linux but get the following error:
```
List all know partitions
kernel panic: cannot mount root fs on unknown block(0,0)
```This is my actual grub.cfg
```
menuentry "Linux" {
  root=(hd0,3)
  fakebios
  linux /vmlinuz26 root=UUID=fc955849-bf24-4329-aeb6-fd7a612bc8cf video=efifb fbdev noefi single persistent
initrd /kernel26.img
}
```

**Stupid question: Do i still have to install grub2 on linux or is it enough to have a grub.efi file on my mac partition???**

---

### Post by sudo_0 on 2011-01-16
> **pattscott said:**
> Ok. the situation changed. I'm using a efi file from [http://ubuntuforums.org/showthread.php?t=995704&page=113. ]("http://ubuntuforums.org/showthread.php?t=995704&page=113")
Now I can boot linux but get the following error:
```
List all know partitions
kernel panic: cannot mount root fs on unknown block(0,0)
```


i had the same problem trying to boot into windows through refit on my macbook with windows, os x and ubuntu installed..

i read a thread somewhere that states that the bootloader can only handle 4 partitions... if you have too many partitions refit won't boot it...

try this : [https://help.ubuntu.com/community/MacBook/TripleBoot](https://help.ubuntu.com/community/MacBook/TripleBoot)

---

### Post by metatechbe on 2011-01-17
> **pattscott said:**
> 
```
List all know partitions
kernel panic: cannot mount root fs on unknown block(0,0)
```

Grub 1.98 is known to corrupt the initial ramdisk.
This was fixed with the "newreloc" feature.
Please use 1.99 (trunk).
See instructions here :
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

metatech

---

