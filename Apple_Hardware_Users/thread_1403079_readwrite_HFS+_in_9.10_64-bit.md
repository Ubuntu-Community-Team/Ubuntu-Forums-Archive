---
title: "read/write HFS+ in 9.10 64-bit"
date: 2010-02-09
forum: Apple Hardware Users
---

### Post by polyphonictimothy on 2010-02-09
I'm trying to set up an AFP server with my linux computer. One of the shares I want to set up is an external drive formatted to HFS+. I have disabled journaling in OS X but I still cannot gain full read/write privileges. Any help would be greatly appreciated. Thanks.

---

### Post by mickie.kext on 2010-02-09
You should check permisions and ownership of HFS+ filesystem you trying to write. If your OS X username and UID are not same as ones at Ubuntu, that is the reason why you can't write.

---

### Post by polyphonictimothy on 2010-02-09
they're the same. the ownership is listed in Ubuntu as usr #99. I've tried using chown and diskutil to change ownership but neither seem to help.

---

### Post by kalos on 2010-02-27
I have an HFS+ external drive that I connect to a Mac, Xbox360, and Ubuntu. I frequently have problems with it. I have to go through various dead chicken-waving steps to get it to work again. (It usually stops working when it's not unmounted properly.)

In the steps below, my drive is named zapf. Be sure to use whatever you've named yours.

[LIST]
[*]Turn off journaling: (see [apple docs]("http://support.apple.com/kb/HT2355?viewlocale=en_US"))
Can also be done with in a Terminal on your Mac: ```
diskutil disableJournal /Volumes/zapf
``` 
[*]Verify and Repair -- On a Mac, open /Applications/Utilities/Disk Utility. Select your drive and click Verify Disk. Once that completes, click Repair Disk. Generally no repairs are necessary.
[*]Today, when Ubuntu mounted my drive it would switch to read-only filesystem after a few seconds, so I decided to do it manually. I re-ran the above steps, plugged in my drive, quickly unmounted it (eject in Nautilus), and then ran this: ```
sudo mkdir /media/zapf; sudo mount -t hfsplus -o rw /dev/sdd3 /media/zapf
```. I knew to use /dev/sdd3 because when it was mounted read-only, /etc/mtab listed my hfsplus drive as /dev/sdd3.
[/LIST]

After that, I used ```
sudo umount /media/zapf
``` to unmount the drive and when I unplugged and replugged, it seemed to work. We'll see until next time : \

---

### Post by kalos on 2010-02-27
Oh, and also, Ubuntu now shows it in nautilus as 500 GB filesystem instead of zapf. I can probably fix that with "install gparted and use that to unmount, label, and apply, then restart ubuntu" (from [this post]("http://ubuntuforums.org/showthread.php?t=1294942")), but I'd like to figure out how to get these settings applied every time I connect the device. I don't know how I add it to my fstab since any device could probably get put on /dev/sdd3

---

