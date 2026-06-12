---
title: "Question about dual boot"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by dljesse on 2007-08-16
I currently only have ubuntu 7.04 installed on my computer, however I wish to install windows 2000 as well now. My question is how would I go about setting up my computer so that I can choose which OS I want to use when my computer starts.

---

### Post by Arthur Archnix on 2007-08-16
Install gparted and free up about 5 gigs for windows 2000. Insert your windows cd, boot and install it to the space you just freed up. Once done, you'll only be able to boot windows, so you'll need to reinstall grub. 

There are plenty of links and directions on how to do this on the forums already. Your feisty live cd or a grub live cd will be required.

Best,

---

### Post by obscur156 on 2007-08-16
Well i have made a triple boot   XP/FEISTY/GUTSY.
I have used the info from one site but they are starting the opposite way.
Windows first and after ubuntu.
i am not sure if it will work but i think it should.
You can try it at your own risk and if you do,just make sure to do a backup before.

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty")

I repeat use it at your own risk.
Good luck budy.

---

### Post by MQMike on 2007-08-16
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

Very doable.
Install Windows.
Then reinstall GRUB (the bootloader) from Ubuntu using at a GRUB prompt
grub> root (hdx,y)
grub> setup (hd0)
grub> quit
$exit
Then re-boot to test it.

NOTE:
(hdx,y) is the hard drive and partition of your Ubuntu.  Find out x and y.  GRUB starts numbering from zero.  So (hd0,0) is the first hard drive (hd0), the first partition (the “0”).  At a GRUB prompt, run
find /boot/grub/stage1
and the result will tell you the (hdx,y) value you need n the root statement. 

If necessary edit the boot menu (called /boot/grub/menu.lst in Ubuntu) to make sure your boot stanza entry for Windows is correct.

---

### Post by ronmarley1 on 2007-08-16
Another option is the Super GRUB Disk.  [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

