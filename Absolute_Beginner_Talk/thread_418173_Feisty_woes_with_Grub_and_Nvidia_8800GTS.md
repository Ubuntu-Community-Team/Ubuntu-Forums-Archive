---
title: "Feisty woes with Grub and Nvidia 8800GTS"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by richardgundersen on 2007-04-22
Hi

Edgy is great, and I'm sure Feisty is too - unless you have an NVIDIA 8800GTS and or a dual boot system. Seems like loads of people are having very similar problems to me so first here's my tip FWIW. 

If you are having problems with an NVIDIA 8800 series card, try following these instructions (TO THE LETTER) posted on the NVIDIA website - [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

It worked perfectly for me. The only thing I had to do in addition was remove the links for Sxxgdm and Sxxkdm so that when I entered runlevel 3, the NVIDIA driver was satisfied that X wasnt running. (actually rename them to e.g. xS13gdm so you can rename them bask after the driver is installed)

Now my question - Grub. Arrrggghhhh! Please could someone tell me if there's an easy way to re-run grubs configuration utility or whatever it uses so it recognises my drives properly. I've got Feisty on /dev/sda1 and XP on /dev/sdb1. GParted puts a warning triangle against my XP partition, which I suspect has something to do with why XP won't boot (Grub error 13). Please please tell me I haven't trashed XP - I've nearly finished Stalker and can't be bothered to play all the way through again :)

Is there an easy way to tell Grub to just "do it" rather than editing menu.lst?

---

### Post by richardgundersen on 2007-04-22
Here&#347; the relevant bits from my menu.lst file. Really appreciate any help

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=79c4c066-eef8-4f8e-89d6-06d9cf2eecf7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=79c4c066-eef8-4f8e-89d6-06d9cf2eecf7 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by richardgundersen on 2007-04-22
If this helps anyone - my problem was that the disk that XP was installed on (sdb) was the primary disk in my bios. I set the disk with Ubuntu (and presumably GRUB) to be the first one in the BIOS, and then tweaked menu.lst a bit until both OSs would boot.

So, the order of the drives in the BIOS is very important!

---

