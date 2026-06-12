---
title: "kernel update disables wireless card"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by econobeing on 2007-06-03
i have a Dell B130 laptop with a broadcom internal wireless card. it was working fine with ndiswrapper until i installed a kernel update. when i restarted my computer the network icon in the tray said it couldn't connect to a network. but when i opened up a terminal and typed "sudo iwlist scanning" it was able to detect my wireless network. needless to say this is very confusing... how can i use my wireless card with the updated kernel?

---

### Post by Inxsible on 2007-06-03
> **econobeing said:**
> i have a Dell B130 laptop with a broadcom internal wireless card. it was working fine with ndiswrapper until i installed a kernel update. when i restarted my computer the network icon in the tray said it couldn't connect to a network. but when i opened up a terminal and typed "sudo iwlist scanning" it was able to detect my wireless network. needless to say this is very confusing... how can i use my wireless card with the updated kernel?

There have been too many problems with the latest kernel update viz 2.6.20-16. Some like you have lost their network connections. Others have lost their local Samba networks. People like me see phantom CD Drives when there are none.

I would suggest that you use the older kernel until things get sorted out. Hopefully you won't have already un-installed your older kernel

---

### Post by kevdog on 2007-06-04
I could be way off the wall with this, but I thought that ndiswrapper when properly installed inserts itself into the kernel.  Because you updated the kernel, ndiswrapper may no longer be contained within the kernel.

Here is what I would try (Heck you dont have a working connection anyway):
```

sudo modprobe -r ndiswrapper
sudo depmod -a  
sudo modprobe ndiswrapper

```

If this doesnt work -- make sure everything is alright with ndiswrapper, ndisutills
```

ndiswrapper -v

```

Make sure there are no error statements or statements about conflicting versions.  If there are you might need to uninstall completely ndiswrapper then reinstall the package -- I would suggest from svn repository if you go this route!

---

### Post by econobeing on 2007-06-04
i tried uninstalling and re-installing ndiswrapper on the new kernel, but no luck there, i'd probably just be better off using the old kernel.

how would i go about making the old kernel the default boot one?

---

### Post by kevdog on 2007-06-04
Just curious to see what your system says:

```

sudo updatedb
locate ndiswrapper

```

Do you get anything like the following in the output???:
/lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko

---

### Post by econobeing on 2007-06-04
it gives me this:

/lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
/lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper
/lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper

---

### Post by Inxsible on 2007-06-04
Can you post the output of the following command, so I can tell you how to make the older kernel the default :
 
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by econobeing on 2007-06-04
here's all the uncommented stuff:

> 
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9fe0226c-a706-46a0-a97e-e604820a1e94 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9fe0226c-a706-46a0-a97e-e604820a1e94 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9fe0226c-a706-46a0-a97e-e604820a1e94 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9fe0226c-a706-46a0-a97e-e604820a1e94 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

---

### Post by kevdog on 2007-06-04
Thats the good thing about linux -- there is more than one way to skin a cat. 

If it were me, I would just uninstall, reinstall ndiswapper from svn and then just reinstall the driver.

I just did this today and can tell you it works! (although defaulting back to the previous kernel would probably be easier!)

---

### Post by Inxsible on 2007-06-04
You should have posted all of your file, but anyway.
 
There are two ways you can change the default:
 
1) you can move both the -15 kernels (kernel and recovery mode) above the -16 ones and save the file. On next re-boot, they will be default
 
2) You can keep the kernel order the same and change the default line it picks by looking for a line 
```
default 0
```
 
Change the number to 2 and your -15 kernel will be highlighted first as default. If you follow option 2, then the next time you do a kernel update, -16 will become the default since the -17 (or whatever the number) kernel will be placed on top of the -16...making -16 on line 2.
 
I hope thats clear enough to understand.

---

### Post by econobeing on 2007-06-04
oh yes, very clear :D

thank you for the help, much appreciated.

---

