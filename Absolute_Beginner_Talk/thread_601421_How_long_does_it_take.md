---
title: "How long does it take?"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by antony11 on 2007-11-03
Hi folk,
I've finally got around to giving Linux a go. My first machine is running a dual boot Vista/Ubuntu 7.04. The second machine is a Compaq Proliant ML370. Its an old server and up till recently ran NT.
Ive now installed Ubuntu Server 6.06 on this machine and this is where I need the help. It has gone through the install process with no problem. Ive removed the disk and rebooted it. It has begun to load in the system but seems to be just hanging there. Here are the last couple of lines of text on the screen:-

root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernal /boot/vmlinuz-2.6.15-26-server root=/dev/ida/c0d0p1 ro quiet splash
  [Linux-bzImage, setup=0x1c00, size=0x16c98f]
initrd /boot/initrd.img-2.6.15-26-server
  [Linux-initrd @0xf94a000, 0x6a176a bytes]
savedefault
boot
Uncompressing Linux. . . Ok, booting the kernal.
_

Hopefully someone can tell me what's happening. How long does it take to complete this boot for first time? So far its takeabout 15 mins plus  the length of time for me register on here and write this out so about 25-30 mins. I have tried rebooting but it just comes back with the same message and nothing happens when I use the keyboard.

---

### Post by kosmic on 2007-11-03
In grub edit the kernel line and remove this :

quiet splash

Then reboot, and past here again the boot messages...

---

### Post by antony11 on 2007-11-03
Thanks - but how do I access the grub if it is not completing the startup? The flashing cursor doesnt allow me to do anything. So how can I bypass it?
Im not sure if I made it clear that I no longer have NT on this system just linux

---

### Post by Gremlinzzz on 2007-11-03
should be 25 seconds or less . sounds like your second computer is a slow reader.did you wipe the harddrive before installing ubuntu or go over top. try doing a good format and reinstall .my thinking is computers weeding out the  crap left over from last system.or not! just a guess.i use this free program to  wipe the drive takes about a hour or so but does a good job.
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by kosmic on 2007-11-03
After your bios stops booting..it should say something like starting booting or starting grub...press "ESC" KEY and you will see the grub boot manager.

then pres the "e" key and go to the end of the line and remove that 2 words i've told you

then press "enter" and the press "b" key to boot again ubuntu...

Hope it helps...

---

### Post by antony11 on 2007-11-03
Thanks, I did do a complete wipe of the drives and started from fresh. I figured out how to get into grub and removed the item as recommended. On restarting it went a lot further but is still hanging at a prompt. Here is the last few lines:

[42949380.550000] EISA: Probing bus 0 at eisa.0
[42949380.550000] EISA: Mainboard CPQ0690 detected:
[42949380.550000] Cannot allocate resources for EISA slot 1
[42949380.550000] Cannot allocate resources for EISA slot 2
[42949380.550000] EISA: Detected 0 cards.
[42949380.550000] NET: Registered protocol family 2
[42949380.600000] input: AT Translated Set 2 keyboard as /class/input/input0

On rebooting again it initially went back to the original script so I obviously hadnt saved it properly so how do I save it?

Edit: Im presuming that the EISA is referring to the hd controller?

---

### Post by antony11 on 2007-11-03
bump. Anyone any suggestions here please?

---

### Post by steve.horsley on 2007-11-03
It looks like either your install disk is corrupt or your hardware isn't compatible. You could try burning your installer CD again at the lowest possible speed. You should also checksum your .ISO image with md5sum and make sure the checksum matches the one quoted on the web site.

---

### Post by antony11 on 2007-11-04
ok this is driving me nuts. First of all I know the box is linux compatible as it had it on it once before a couple of years ago. So following Steve's advice I decided to check the checksum of the iso. It failed. So I downloaded it again and again and again etc from several differnt sites but ecah time it fails the checksum. I cant see why particularly as I have often downloaded larger files frequently (including ubuntu desktop 7.04) - all with no problems. :confused:
I thought about purchasing a copy from one of the recommended sits but the only one I could find in the UK that does the server edition want to sell them in packs of 20 which is no good to me. So Ive had a look and cannot see any means to request a copy on disc of this particular version (Ubuntu server 6.06). I have a couple of choices I guess - 1 install something like breezy desktop and then get help her converting it to server status - 2 hope someone in the UK might have a copy on disc they could send me :) - or 3 use a different version of linux on the server.

---

### Post by Soarer on 2007-11-04
A couple of things which might help (or not)...

1. Some Compaq motherboards  (including the one in my Evo) have some dip switches. If set, they prevent you overwriting the boot sector, and therefore  stop Grub working. Might be worth checking.

2. I have run 6.06 server OK before, but couldn't install Feisty (7.04) server on my no-name box. Gutsy (7.10) server just worked. It might be worth trying to download that & give it a go, as you have no data to worry about.

---

### Post by antony11 on 2007-11-04
Thanks Soarer. Im fairly confident that no dip switches were altered when the box originally had linux on it, and Im absolutely certain I never changed any to put NT on it so I can at least be sure that its not that. So I will try tracking down a copy of Gutsy and give that a go.

---

### Post by steve.horsley on 2007-11-04
antony11:
If you are in the UK and want to email me your address (steve.horsley@gmail.com), I'll drop a burned CD in the post for you. I seem to be able to reliably burn CDs and can even verify the checksum of the disk after burning (md5sum /dev/cdrom).

---

