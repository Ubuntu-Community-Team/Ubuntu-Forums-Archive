---
title: "Boot Hard drive from usb stick"
date: 2011-10-15
forum: Apple Hardware Users
---

### Post by jjlee on 2011-10-15
I have two hard disks in my computer. I want to try different distros on the second hd but I don't want to tamper with the main grub as the rest of the family use it and this may cause problems. I want to be able to use the whole second hd not just create a live USB, but use the USB stick to boot to the second hd. Is this possible. I Would appreciate any guidance.

---

### Post by oldfred on 2011-10-15
If you have two hard drives you have two MBRs. You can keep the standard grub2 boot loader in the one drive and modify/edit the other. You can then use one time boot key (f12 on my system) to change boot. You can also add a chainload entry into your standard install's 40_custom to chain to the other MBR or other installs.

You can just install grub2 to just about any device, but then you do not get the os-prober to set up boot stanzas. It is not all that difficult to copy & paste a boot stanza from an install into a grub.cfg on another device.

Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

I use USB flash drives to boot ISOs but have chainload or boot stanzas to other installs as backups.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

---

### Post by trystandale on 2011-10-16
Thanks for posting this, Oldfred. I have also run with the same problem and  been clueless of what would I do.

---

