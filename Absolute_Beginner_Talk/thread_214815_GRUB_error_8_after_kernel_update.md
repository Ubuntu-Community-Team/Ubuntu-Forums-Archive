---
title: "GRUB error 8 after kernel update"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by Pelham123 on 2006-07-13
Hi.

I have been running 5.10 for a short while now, but am still relatively new to linux. I allowed the kernel to be auto-updated the other day and after rebooting my system booted straight into:

grub>

I had a quick look at the commands available and the only one I felt I could try was 'boot' which gave me the next error:

Error 8: Kernel must be loaded before booting

I have tried to google error 8 but with limited (ie-none) success,  I have booted with a rescue disc and taken a look at the 'boot' section, but to be honest it might as well be written in Swahili. I just want my Ubuntu back

Any help please :(

---

### Post by OpsVentus on 2006-07-13
It would be real cool if grub would boot your system with just the command "boot". But at the moment we have to tell em first what to boot.
We have to take a look at grub's menu.list. It's at '/boot/grub/menu.list'. Are you able to open that file and tell us what's in there?

For Ubuntu 5.10 kernel 2.6.15-26-386 there should be something like this in there:
title		Ubuntu Linux 5.10
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

Cheers,
Bart.

---

### Post by Pelham123 on 2006-07-13
Thanks for the reply!

Under rescue mode, /boot/grub/menu.lst = 

title   Ubuntu, kernel 2.6.12-10-386
root    (hd0,0)
kernel  /boot/vmlinuz-2.6.12-10-386 root=/dev/md0 ro quiet splash
initrd  /boot/initrd.img 2.6.12-10-386
savedefault
boot

title   Ubuntu, kernel 2.6.12-10-386(recovery mode)
root    (hd0,0)
kernel  /boot/vmlinuz-2.6.12-10-386 root=/dev/md0 ro single
initrd  /boot/initrd.img 2.6.12-10-386
boot

title   Ubuntu, memtest86+
root    (hd0,0)
kernel  /boot/memtest86+.bin
boot

Will keep my fingers crossed. Thanks.

---

### Post by Pelham123 on 2006-07-13
In a (brief) burst of understanding I figured, from what you had posted, that GRUB was just a list of commands to get the ball rolling. So from the grub> I entered the following:

root (hd0,0)
kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/md0 ro quiet splash
initrd /boot/initrd.img 2.6.12-10-386
boot

Got fed the following line after 'uncompressing linux....':

Kernel panic - not syncing: VFS :unable to mount root fs on unknown block(0,0)

I read that the TAB key gave possible choices to commands, resulting in finding .old kernel/initrd files, so I used those:

root(hd0,0)
kernel /vmlinuz.old
initrd /initrd.old
boot

After a few pages of startup text scrolled past, system halted at:

/dev/cdrom: open failed : no medium found
no volume groups found
/scripts/local-top/evms: 31 : /sbin/evms_activate: not found
ALERT! Does not exist. Dropping to a shell!

'ls' at the shell produced: 'dev root lib sys tmp var etc bin' amongst others.

Will do some googling on linux startup order etc. and see if I can figure out whats going on.

---

### Post by Pelham123 on 2006-07-13
Success!

After spotting the deliberate mistake(!) I added:

root=/dev/md0 ro

to the kernel line.

So, I am now replying to this thread from my Ubuntu OS. YAY!

Many thanks for your help OpsVentus, you may feel like you didnt do that much, but your help got me to where I am now! Just need to figure out what to do about booting without the need for booting from the grub> command line.

:D thanks :D

---

### Post by OpsVentus on 2006-07-14
And what's wrong with booting from the commandline? ;)

Congratulations on solving the problem by your self!
To get your boot correct, maybe you can try to install an older kernel, this will add the older kernel to your menu.lst. If that one boots ok, you can try to reinstall the latest kernel, this will then add the new kernel to your menu.lst again.

Or(what I would do) keep playing with the menu.lst until it works.

Have fun,
Bart.

---

