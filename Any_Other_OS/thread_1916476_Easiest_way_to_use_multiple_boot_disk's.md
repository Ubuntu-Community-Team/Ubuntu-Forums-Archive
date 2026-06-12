---
title: "Easiest way to use multiple boot disk's"
date: 2012-01-28
forum: Any Other OS
---

### Post by MadsRC on 2012-01-28
So, I'm the kind of person that always carry a lot of boot disks around and on top of that, I work with a 32bit & 64bit enviroment. That kinda forces me to double my boot disks as I need both architectures.

1) I've tried MultiSystem & Sardu for creating a multiboot disk, but those also incorporate some other stuff I don't need. What I basicly would need is a disk I can boot from, which will allow me to choose from my different boot disks. No other fancy stuff. Have any suggestions?

2 )Is there any reason to have a 64bit boot disk if I'm only going to use it as an LiveCD? I get that if I need to install it to the HDD, a 64bit would be better (if the CPU supports it) as that would be a permanent installation.

But for LiveCD's it won't matter if I use 64bit or 32bit? I'm thinking that 32bit would be best, since that is more widely supported (IE: I can use a 32bit LiveCD on a 64bit CPU, but no the other way around)

The way I do multiple boot disk's right now is to use UBCD. That allows me to add the custom ISO's to the CD, and boot from it. UBCD also covers my emergency boot disk needs and incorporates Parted Magic, which makes that part ideal for me. 

3) Though I'm not aware if there should be any performance issues with starting a boot disk through the custom menu in UBCD or if it is just like booting from a boot disk alone (like burning the Ubuntu cd and booting from that)?

---

### Post by oldfred on 2012-01-28
I stopped using CDs as keeping them updated used a lot of CD. I now only use flash drives. Most systems in the last 5 or so years will boot from USB flash drives. On an update I just copy new ISO over to flash drive and edit my grub.cfg.

I did it manually before scripts came out to automate it.
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
multicd.sh - combine Linux ISOS into one 
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)
Another: multiboot055.sh
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
MultiSystem Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

---

