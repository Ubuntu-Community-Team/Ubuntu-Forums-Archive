---
title: "Cancelling Grub check during boot"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by AkiraBergman on 2007-05-23
Hello all,

I have Ubuntu-7 on HD-0 and Ubuntu-6 on HD-1.

1. How do I get rid of Ubuntu-6 on HD-1?

2. If I kept Ubuntu-6 on HD-0, how do I get rid of the Grub timeout screen during boot? Grub counts these timeouts and does an annoyingly long system check every 24 or so boots. I basically want the system to boot Ubuntu-7 without the Grub check. I suppose a Grub edit would do it but I don't know how and what to edit.

Thanks so much.

---

### Post by orb9220 on 2007-05-23
Open a term and enter   **gksudo gedit /boot/grub/menu.lst**

Then you can change the timeout time and comment out what you don't want to show with the **#** in front of items like this.

For Timeout

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

I change mine to 3 secs.

For removing menu items using the # symbol
> 
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b420607b-237e-4442-95a0-1353392b14a1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b420607b-237e-4442-95a0-1353392b14a1 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

#title		Ubuntu, kernel 2.6.20-14-generic
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.20-14-generic root=UUID=b420607b-237e-4442-95a0-1353392b14a1 ro quiet #splash
#initrd		/boot/initrd.img-2.6.20-14-generic
#quiet
#savedefault


the first two shows in menu the last one with all the # on each line removes the third option from menu.

Hope this helps

---

