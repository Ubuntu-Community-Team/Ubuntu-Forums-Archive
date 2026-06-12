---
title: "Only 1 CPU in top"
date: 2007-04-25
forum: Apple Intel Users
---

### Post by cworley420 on 2007-04-25
Upgrade to Feisty was smooth. 

However, i have noticed some performace issues.  Did not take much time to look into it, but just noticed only 1 cpu i list in top and gnome monitor.  I have a Dual Core Intel and with Edgy it list both.

is thier somthing i need to do when booting the kernel?

-chris worley

---

### Post by Lord Illidan on 2007-04-25
You need to chose a generic kernel not a 386 one.

I don't know if you understood me...can we see your /boot/grub/menu.lst please?

---

### Post by cworley420 on 2007-04-25
ah, makes sense.  

here is m grub file.  I started with ubuntu server edgy because the gui would not work on the desktop version.  then i just apt-get a bunch of stuff and got X and all the other stuff the desktop had.

so, here is the list of kernels in the gub file.  I come from PCs / Slackware so, not sure which kernel would be best for the macBookPro.  Let me know if i need to install another one.  I choose ubunutu because osX was a pain after using linux.


title		Ubuntu, kernel 2.6.20-15-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=16a8ed4a-e3ce-4316-b7dc-1fe2e08d8568 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-386
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=16a8ed4a-e3ce-4316-b7dc-1fe2e08d8568 ro single
initrd		/boot/initrd.img-2.6.20-15-386

title		Ubuntu, kernel 2.6.20-15-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-server root=UUID=16a8ed4a-e3ce-4316-b7dc-1fe2e08d8568 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-server
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-server (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-server root=UUID=16a8ed4a-e3ce-4316-b7dc-1fe2e08d8568 ro single
initrd		/boot/initrd.img-2.6.20-15-server

title		Ubuntu, kernel 2.6.17-11-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-server root=UUID=16a8ed4a-e3ce-4316-b7dc-1fe2e08d8568 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-server
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-server (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-server root=UUID=16a8ed4a-e3ce-4316-b7dc-1fe2e08d8568 ro single
initrd		/boot/initrd.img-2.6.17-11-server

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=16a8ed4a-e3ce-4316-b7dc-1fe2e08d8568 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=16a8ed4a-e3ce-4316-b7dc-1fe2e08d8568 ro single
initrd		/boot/initrd.img-2.6.17-10-386

title		Ubuntu, kernel 2.6.17-10-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-server root=UUID=16a8ed4a-e3ce-4316-b7dc-1fe2e08d8568 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-server
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-server (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-server root=UUID=16a8ed4a-e3ce-4316-b7dc-1fe2e08d8568 ro single
initrd		/boot/initrd.img-2.6.17-10-server

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

---

### Post by ronocdh on 2007-04-25
Cworley, do you have a Core Duo or a Core2 Duo? SMP will indeed work for either, but with a C2D you could run the 64-bit build of Ubuntu and get the most out of your hardware.

---

### Post by cworley420 on 2007-04-25
2.16GHz Intel Core Duo

Where is a list of kernels i can install through apt-get?  and which do you suggest?

should i justt look through the ftp site in the apt-get config

-chris worley

---

### Post by ronocdh on 2007-04-25
> **cworley420 said:**
> 2.16GHz Intel Core Duo

Where is a list of kernels i can install through apt-get?  and which do you suggest?

should i justt look through the ftp site in the apt-get config

-chris worley
By 64-bit built I meant a different installation candidate of Ubuntu; it's a separate iso you'd download and burn to install from. But given that you are using the Core Duo, that's a 32-bit proc, so keep using the i386 build and as Illidan said, the generic kernel is what you want, as the i386 disables SMP support. The initial generic kernel should be listed in the GRUB file; I suspect it isn't because you've posted one from the server edition, but that doesn't quite make sense to me.

Anyone else have any ideas why cworley isn't seeing the generic kernel?

Also, the GUI problem on MBPs [is documented]("http://ubuntuforums.org/showthread.php?t=414194"); essentially, use the alternate CD and install the fglrx driver.

---

### Post by cworley420 on 2007-04-26
i went back to the server kernel and everything works fine with the cpu.

thanks

-chris worley

---

