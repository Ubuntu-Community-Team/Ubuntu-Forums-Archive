---
title: "Ubuntu Directory for the kernel"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by pez6_9 on 2007-01-14
After updating Ubuntu, I noticed that there were two more options in the grub menu for the updated version, so i decided to delete the old ones out of /boot/grub/menu.lst but accidentaly deleted the new one aswell. Does anyone know how i can find the address for the kernel?

AND

is there an update out there for the networking on ubuntu that allows it to use WPA2-PSK security?, if so, where?

thankyou, all replies/suggestions welcome.

---

### Post by moshuptrail on 2007-01-14
I think you can just navigate from /boot and locate the correct directory where the kernel is located.

My file has these entries, the second one for "recovery" mode
```
title           Ubuntu, kernel 2.6.15-27-k7
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-k7 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-k7
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-k7 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-k7 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-27-k7
boot
```

I'm using Dapper, so that has some effect on which kernel is used.  If you are using Dapper you can probably find 2.6.15-27 on your system.  the -k7 is the processor type - but you will see yours when you go to /boot and do a ls -l.  (That will also give you dates, etc)

Don't forget to fill the in the right drive location.

---

### Post by PriceChild on 2007-01-14
To remove kernels please take them out using synaptic (linux-image-<<version>>)

I reccomend you keep two kernels isntalled incase one fails.

---

### Post by zerhacke on 2007-01-14
There is not going to be a direct "here you go" answer to this, because we may be running different kernels.

To find out what kernel you are running, enter the terminal and type in

uname -r

and press enter.  Keep this information handy.

In the same terminal, type

sudo gedit /boot/grub/menu.lst

and press enter.

You're going to edit the area of this file that you accidentally erased.  My menu.lst file looks as following:

```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```

You're going to replace the section in my file that says 2.6.17-10 with the information you got from the uname -r command.

It would help if you open Nautilus or your file manager and go to the /boot directory.  The vmlinuz-whatever file is the file that is your kernel.

---

