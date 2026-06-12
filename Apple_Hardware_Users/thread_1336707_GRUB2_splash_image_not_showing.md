---
title: "GRUB2 splash image not showing"
date: 2009-11-24
forum: Apple Hardware Users
---

### Post by EvansFive on 2009-11-24
I have dual boot Mac OS X 10.6.2 and Ubuntu 9.10 32 bit.

I am using rEFIt and then it goes to GRUB2.

/dev/sda (has amongst other things a linux-swap and /boot partition.
/dev/sdb (has /, /usr, /home partitions) - external drive

I changed the resolution in /etc/default/grub and added a splash image in /etc/grub.d/05_debian_theme.

The splash images live in /boot/grub/splashimages and this path was also added to /etc/grub.d/05_debian_theme.

Then did sudo update-grub and it finds the splash image ok.

Reboot the system, when it comes to GRUB LOADING, it flashes an error saying device does not exist (I eventually figured that this was the UUID for my "/"). It then displays the GRUB2 menu with no resolution change or splash image.

I can select the options and it boots ok...BUT...no splash images display!

Could someone please advise how to get this working?

Thanks

---

### Post by linds2009 on 2009-11-25
Sorry, did not encounter such a situation

---

### Post by EvansFive on 2009-11-25
Could someone help me with this one please?

Is it related to the fact that / is on an external drive and not where /boot is???

---

