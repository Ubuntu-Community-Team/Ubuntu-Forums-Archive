---
title: "Trouble resizing a partition"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by abstrakt on 2007-08-20
I have a problem I need a bit of advice on.

Here is my current drive configuration:

[---sda1---][--sda2--][--blank--][sda4[--sda5--][--sda6--][--sda7--]]

the double brackets inicates the beginning of an extended partition, sda5 is /, sda6 is swap, and sda7 is /home.

Ok so what I want to do here is reclaim the recently added [--blank--] partition as ext3 and append it to my /home partition (sda7).  In -theory- this should be easy.  I use qtparted or something similar to drag the existing partitions to the left, and then extend sda7 to the right to fill the remaining space.  However even when I boot to a knoppix utility disk, I cannot do this.  "Move" is not an option for any of the extended partitions.

I do have a Windows bartPE disk with a partition utility that will allow me to do this - but I'm concerned that if I move sda5 (my boot partition) then Ubuntu will become unbootable.

HELP!

Thanks :)

---

### Post by bodhi.zazen on 2007-08-20
Well, I would resize with gparted. You will need a more current version so use the live CD :

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)
	Download: [Download Gparted](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)

The worst that I forsee that you will need to re-configure (re-install) grub, which is very easy.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

