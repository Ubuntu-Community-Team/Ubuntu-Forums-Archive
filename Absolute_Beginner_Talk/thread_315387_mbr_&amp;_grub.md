---
title: "mbr &amp; grub"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by mr_samsonov on 2006-12-09
I have just moved over to ubuntu after using gentoo, and so far I am liking it a lot!

I have a question about the mbr and grub. I have two hard drives, one which used to host windows (hdc) and one which had gentoo on (hdd). I now have put ubuntu onto one hard drive (hdd) and am using the second as more storage for files (hdc).

When I boot up I seem to have to have hdc in my bios as the drive to boot from. As this is just for data storage, i would rather boot from hdd which is the drive with ubuntu on. But booting into hdd grub loads, but then I get an error message Error 15 - files not found. Booting into hdc grub loads and everything works fine.

Am I right in thinking as hdc used to have windows on and once upon a time was my only drive this will have the mbr on? Is it possible to change this so  I can boot from hdd? 

Its not a big deal, but would like to understand why this is the case.

---

### Post by beefcurry on 2006-12-09
try booting with the ubuntu live cd, run gparted and set the boot flag to hdd and switch the bootflag off on hdc. Try that, the error 15 should be because the grub is not configured properly. Try posting your Grub boot list here.

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by mr_samsonov on 2006-12-09
I will try gparted.

I think my grub is ok as it boots fine when i try and boot from hdc. Also I modified the grub, and both drives seem to load the same grub. But only one of the works... odd.

Anyway, here is my grub

> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


---

### Post by mr_samsonov on 2006-12-09
ok i have booted into the live cd, and I have noticed that boot is already set on hdd but not on hdc.

---

### Post by bulldog on 2006-12-09
I think the settings in GRUB on hdd are wrong.
You have to set this drive in your BIOS as boot device,than have alook at GRUB and change it like the settings are on hdc.

Why do you have GRUB on both hard disks anyway?
It's not a big deal,just a cosmetic change though.

---

### Post by mr_samsonov on 2006-12-09
I ended up with grub on both  hard drives, as i installed ubuntu on hdc initially to ensure i was happy with the installation, before writing over gentoo...

---

### Post by bulldog on 2006-12-09
You have GRUB already on hdd,you have just to go changing the settings to make it work.
Take a look at the settings on hdc and make a copy or print it out or something.

Than restart and set the hdd as boot device so it will boot every time you start your computer [BIOS]
Than have a look at this grub and change the settings.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by mr_samsonov on 2006-12-09
When i boot from hdc or hdd, I end up at the same grub. I know its the same as I have checked, and also when i edited my /boot/grub/menu.lst and then booted from hdc and hdd both where to the new edited version. 

As I mentioned earlier I installed ubuntu onto hdc with the bootloader to hd0, then installed ubuntu onto hdd with the bootloader on hd1. 

I then removed the ubuntu from hdc and made that one huge partition for storage. 

So I am not sure, could it be that I have to boot from hdc as this is the primary drive? But then why is my menu.lst on hdd. I can live with it how it is but am just confused, and would like to know how it all works!

---

### Post by bulldog on 2006-12-09
Grub is in the MBR of your disk,you can boot from both disks and see grub,so grub is on both disks :D 
They use both menu.lst in your /boot/grub folder,but the settings you have to change.
(hd0) becomes (hd1) and vice versa.
This you have to change.
```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,3)  <---------- if this is set to (hd1) make it (hd0) don't change things behind the ','
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```

In most case when you boot from another drive this one becomes hd0 so you have to tell GRUB about it.

---

### Post by mr_samsonov on 2006-12-09
ah of course!! Makes perfect sense... Worked a treat. 

Thanks for all your help with this!

---

