---
title: "Intall/Boot problem"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by zephor on 2007-04-28
Hi, i'm farily new at linux and i've just started using it on my university computers, I decided it might be a good idea to install it at home.  The problem is whenever I try to boot up from the desktop live cd (this is a fresh install of ubuntu as dual boot with windows XP) i get a black screen with:

[B]
kernel alive
kernel direct mapping tables up to 100000000 @ 8000 - d000[/B]

I browsed through the forums and I found a solution for this that basically said to boot the cd with the extra options (f6) noapic and to remove 'quiet splash'

The install then seemed to work, but afterwards when I tried to boot from the hard drive i got the same error as above.

Does anyone know why? and how to fix it? Any help would be appreciated.

My computer processor is:
**AMD Athlon64 X2 Dual Core Processor 3800+**

and I've downloaded the 64bit version

also I checked the md5sums and they match (after downloading) and i burnt the cd at 2x speed

---

### Post by kagashe on 2007-04-28
Hi,

As far as I know, if you boot Live CD with any special options the same options should be present in Grub. Please search these forums and/or Google to know how this option is to be entered in /boot/grub/menu.lst

Boot again with Live CD, mount the partition in which you have installed if it is not already mounted by the Live CD and edit this file (/boot/grub/menu.lst) to enter the option.

Meanwhile I will also search and post here if I can find out.

Yes here it is:
> The kernel line will be something like this:

kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash

Remove "quiet splash" add noapic at the end:

kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro noapic

kagashe

---

### Post by zephor on 2007-04-28
Thanks! that fixed the problem, although now i have to change the command line everytime I boot (i'm sure theres a way to make it permanent I just need to find it :)  
So yeah thanks I'm off now to see what I can do with ubuntu

---

