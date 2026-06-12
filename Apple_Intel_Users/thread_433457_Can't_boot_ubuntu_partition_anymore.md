---
title: "Can't boot ubuntu partition anymore"
date: 2007-05-05
forum: Apple Intel Users
---

### Post by vh1 on 2007-05-05
I was trying to shrink my OSX partition using the gparted livecd (to create a fat32 shared partition). the resize itself took a while but I figured that was normal. then gparted crashed

uh oh. now OSX reports the disk is 30gb (which is what it should have resized to). disk utility however says it's 50gb, and when I run verify disk it returns a fail. this partition I'm not worried about. I'm in OSX now and everything still runs great.

the partition I'm worried about is my linux one. it's still there. as in, you can boot a livecd and mount it fine. the only thing is that rEFIt doesn't list it. so after booting the livecd, mounting the fiesty install, chrooting into it, and the re-running grub-install. now rEFIt shows the option to boot into linux, but when you select it nothing happens. just that cute little penguin stays there in the middle of the screen

the partitioning tool in rEFIt doesn't work either. it just reports a fail and that's that. I'm really stumped here

---

### Post by Azathoth_ on 2007-05-05
Launch a livecd of feisty and write these commands, but before change /dev/sda3 to your ubuntu partition and /dev/sda to you hard drive partition

sudo mkdir /a
sudo mount -t ext3 /dev/sda3 /a
sudo grub-install --root-directory=/a /dev/sda
sudo umount /a

reboot and all ok :D

---

### Post by vh1 on 2007-05-05
excellent!

I did what you suggested (well, replaced /a with /mnt. seeemed kind of redundant). but it booted fine into my fiesty install. it feels good to be back

thanks!

---

