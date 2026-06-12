---
title: "ANOTHER dual boot cry for help !!"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by Stargate on 2006-07-01
Just installed Ubuntu - noob to linux, am trying to create a dual boot system with XP
Drives as follows
hdc1 - 250gb NTFS with XP installed
hdd1 - 250gb NTFS
hde1 - 40gb ext3 as \
hde2 - 2gb as Linux swap
hde3 - 100gb NTFS
hdf1 - 120gb NTFS
hdg1 - 120gb NTFS

ok, the problem I am having I think is with grub.

Grub starts to load and then I get error 17
If Insert my windows CD and boot up, grub then loads correctly to the boot menu, 
and i can then access and use both Ubuntu or Windows.
Any help would be greatly appreciated:D

---

### Post by Stargate on 2006-07-01
device.map


(hd0)	/dev/hdc
(hd1)	/dev/hdd
(hd2)	/dev/hde
(hd3)	/dev/hdg
(hd4)	/dev/hdh
(hd5)	/dev/sda

Menu.lst
title		Ubuntu, kernel 2.6.15-25-386
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hde1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hde1 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hde1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hde1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by u.b.u.n.t.u on 2006-07-01
I dual boot off 1 HDD. I install XP first and then Ubuntu. No problems. Sorry I can't be of more help.

---

### Post by Herman on 2006-07-01
stargate
    >  (hd0) /dev/hdc
hdc1 - 250gb NTFS with XP installed
 # on /dev/hdc1
 title Microsoft Windows XP Professional
 root (hd0,0)
 savedefault
 makeactive
 chainloader +1


     (hd1) /dev/hdd
hdd1 - 250gb NTFS

      (hd2) /dev/hde
hde1 - 40gb ext3 as \
hde2 - 2gb as Linux swap
hde3 - 100gb NTFS
title Ubuntu, kernel 2.6.15-25-386
 root (hd2,0)
 kernel /boot/vmlinuz-2.6.15-25-386 root=/dev/hde1 ro quiet splash
 initrd /boot/initrd.img-2.6.15-25-386
 savedefault
 boot

      (hd3) /dev/hdg
hdg1 - 120gb NTFS

      (hd4) /dev/hdh

      (hd5) /dev/sda
hdf1 - 120gb NTFS
 Hello, I re-arranged the information you provided so I can see what goes with what easier. 
:confused:  That looks okay to me....
You have sda and no hdb, but you have a hdc,hdd,hde, no hdf, but you have an hdg and hdh.
I'm kind of embarrasing myself a little here, I have no computers with that many drives to play with or I'd know more maybe.

error 17 :  Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 
Hmmm, I don't know...:-k
> If Insert my windows CD and boot up, grub then loads correctly to the boot menu,   and i can then access and use both Ubuntu or Windows. 
Have you double-checked your settings in your BIOS? (boot order?), jumper settings too?. I presume you would have, just making sure, that's all.

I really don't know, the best suggestion I can come up with is to try experimenting with GRUB's Command Line Interface and see if you can boot manually that way with and without the CD in the drive. GRUB's CLI always gives a little feedback for each command we enter, maybe you will discover something that way that will shed some light on the subject. For a How-To on GRUB's CLI, *[Click Here]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")*. In the meantime, I hope some-one more knowledgeable than me might come along with an answer. I have a funny feeling it's got something to do with the way your computer is wired or how it's set up in the BIOS though, but I don't know exactly what it might be.

Oh yes, here's another idea, try out GAG Boot Manager too and see what happens.
*[Click Here]("http://users.bigpond.net.au/hermanzone/p12.htm")* for a how-to on GAG.
All the best with it, Regards, Herman

---

