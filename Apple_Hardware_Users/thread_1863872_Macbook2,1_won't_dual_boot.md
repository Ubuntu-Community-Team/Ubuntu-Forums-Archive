---
title: "Macbook2,1 won't dual boot"
date: 2011-10-18
forum: Apple Hardware Users
---

### Post by Carlos J. on 2011-10-18
Hi all, 

This is my first post here. I've been trying to install Ubuntu using the procedure as described for flash drives at [https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick) but the Macbook won't recognise the partition as a startup disk. This problem has been reported before in this forum ([http://ubuntuforums.org/showthread.php?p=11361615#post11361615](http://ubuntuforums.org/showthread.php?p=11361615#post11361615)).

I have tried the rEFIt route too, but like in the other report the Macbook won't recognise the flash for booting either. I've spent not less than one week trying to fix this and I'm really clueless,

Any idea would be greatly appreciated,

CJ

---

### Post by dracotux on 2011-10-20
Dear Carlos,

I just finally got Ubuntu 11.04 installed on my Macbook Pro 8.1 early 2011.

Try the tutorial on this link:

[http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/](http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/)

Some of the words are hyperlinks, one of them leads to Ubuntu 11.10 instead of the older versions. Just download the version you need to have on [www.ubuntu.com](www.ubuntu.com)

As you follow the instructions on that site, you will be able to try the Live USB stick, install ubuntu, but maybe not boot the installation afterwards. Make sure that the Ubuntu installation is on the fourth partition at max! I made the mistake to make my fourth partition the swap partition, and the fifth partition the ubuntu partition. After I reversed the fourth and fifth partitions (format, delete, partition again) and installed again, it booted into Ubuntu.

It didn't boot into Ubuntu by default though (you probably don't want this either). I have Refit installed on my Macbook Pro, but that one doesn't boot correctly as well (if I select the pinguin icon). I booted into Ubuntu by holding down the alt/option key during startup and then select the Windows drive.

I don't know why it worked for me, but it worked for me. Make sure [COLOR=Red]not to install the bootloader on sda[/COLOR] but on [COLOR=SeaGreen]sda4[/COLOR] (if your ubuntu [COLOR=SeaGreen]partition is 4[/COLOR] and you only have 1 harddrive in your mac, otherwise just follow the number of the partition you are installing ubuntu on). I read somewhere that GRUB2 can do some nasty things on a Macbook if not installed properly.

I went through great lengths to get Ubuntu installed and booted, so I hope I can save you weeks and weeks of googling for answers. If this works out for you, please let me know, so I will now that I actually helped a guy install Ubuntu on his Mac. If it doesn't work out for you, call me loser and swear at me all you want. :)

Kind regards,
dracotux

---

### Post by Carlos J. on 2011-10-24
Many thanks Dracotux! I will try it and report back!

Cheers,

Carlos

---

### Post by Joeb454 on 2011-10-24
Thread moved to ***Apple Users***

---

