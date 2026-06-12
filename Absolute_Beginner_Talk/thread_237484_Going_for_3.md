---
title: "Going for 3"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by backinblack on 2006-08-16
Ubuntu is already sharing this HD with WindowsXP64-bit, but there's still about 80 gigs to play around with. This is a Western Digital 200 gig HD.
Is there some way to0 go about getting SuSe 10.1 to co-exist with Windows and Ubuntu?
Can Gparted be used to partition the HD for all three fo these OS's?[-o<

---

### Post by Kobalt on 2006-08-16
Yes of course. You can use Gparted to create a partition for Suse 10.1, then launch the installation process. Grub should detect the three OS at start-up, and should pick which one you want to boot.

---

### Post by bernied on 2006-08-16
No reason why you shouldn't do this - you would not be the first (google linux multi-boot). 

It wil depend a little on what partitioning you've already done. Is the 80gb unpartitioned?

post the results of 'fdisk -l' if you want help on the partitioning

There are a couple of things you might want to think about.
- You would benefit from getting to know grub (the bootloader), as you may want to edit this file manually to add your new OS
- It might be good to have a shared boot partition for linux distros, with separate partitions for your separate distros. All your kernels and initrd images could be kept together. Just make sure they have unique names (you will find files called vmlinuz and initrd.img, which will be simlinks to your current kernel and initrd image). 

It is possible that Suse will sort all this stuff out for you, but I doubt that it will get it right the first time, and you don't want to lose access to your other operating systems if you haven't got a web connection established on Suse (as an example).

---

### Post by lupine_nickt on 2006-08-16
I had SuSE, Gentoo and Ubuntu installed and inter-operating a short while back... so it does work :)

A few notes about SuSE... first, keep a close eye on the installer, as by default it wipes your hard drive, and I almost missed the menu option for it!

Secondly, it installs an activated SSH server by default... so you might want to turn that off.

Thirdly, it's package management system is "crap". No, really! 

Good luck with it, anyway :)

xF,

...Nick

---

### Post by anaconda on 2006-08-16
And it would be a good idea to make a separate partition for /boot (~100MB), so that when you decide to delete some linux, your computer would still boot. (boot manager Grub would be on it's own partition.)

It is easy to make. when you are installing suse you just make a separate partition for boot and assign it to be /boot.

Then if/when you want to delete suse, suses boot manager would not be lost..

It would be best if you could put the /boot -partition to the beginning of the hard-disk, but it can be anywhere.

---

