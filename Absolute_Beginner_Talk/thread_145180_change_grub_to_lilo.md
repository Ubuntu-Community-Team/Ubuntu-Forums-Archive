---
title: "change grub to lilo"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by malavar on 2006-03-15
hey can someone tell me how to change from grub to lilo, i installed lilo but it still boots grub and im afraid to remove grub because maybe then it wont boot at all... or someone explain why on this PC  takes over 1 minute to load grub during boot, but lilo loads within a few seconds.

---

### Post by Pragmatist on 2006-03-16
>  someone explain why on this PC takes over 1 minute to load grub during boot, but lilo loads within a few seconds.

I don't know.  Please tell us more about your system.  Is it a dual-boot?  If so, what OSes?  You said Lilo took a few seconds.  Did you have Lilo with Ubuntu before?

---

### Post by mrpivello on 2006-03-23
[QUOTE=malavar]... i installed lilo but it still boots grub ...[/QUOTE]


I have the same problem. Is there a file where I can set lilo instead of grub as the boot loader?

---

### Post by Pragmatist on 2006-03-23
First go into synaptic with:
```
sudo synaptic
```
use keyword: **lilo** to search and find the lilo package.  There are some other packages related to lilo as well, so you may want to read their descriptions and see if they apply to you.

LILO gives you three different things:
1.) Boot Loader code
2.) A Configuration file that modifies this boot loader code.
3.) A program that takes the 'custom code' that results from numbers 1 & 2 and places it in the MBR.

So you would first edit the /etc/lilo.conf file and then you would run the command ```
lilo
```

**Note: I am not recommending that you use Lilo, or that my instructions are correct. Bootloaders can be a tricky subject and alot depends on the specifics of your situation (are you dual-booting, etc..etc..)**

---

### Post by elamericano on 2006-03-23
The commands I used were:

sudo liloconfig
sudo lilo

liloconfig is interactive. Basically, you need to know what your doing, or accept the consequences of experimenting. Most important is knowing if your bootloader is in the MBR or in the header of the active partition.

I'd recommend trying it out. Knowing how to recover a bad bootloader is a basic skill. Read that HOW-TO first.

When I switched, I found that lilo was dog slow compared to grub (although I normally prefer lilo). So, I switched back:

sudo grub-install <device>

In my case it was "sudo grub-install /dev/hda2", but it's certainly a different location for you.

Good luck.

---

