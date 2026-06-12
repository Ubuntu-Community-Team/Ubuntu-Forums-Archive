---
title: "[SOLVED] Strange boot problems Kubuntu 7.10"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by neu_ser on 2007-10-25
Hi. I am completely new to linux and was hoping for an easy start!

I installed 7.04 fine but had problems getting connected via my wireless ralink card, I figured I may aswell install 7.10 with newer drivers (hopefully) before I start learning how to compile drivers etc.

Anyway, I am attempting to triple boot vista (on two sata drives in software raid), xp (on first partition of single IDE drive) and now Kubuntu 7.10 (on the second partition of the single IDE drive) using GRUB4DOS as the bootloader.

I chose not to install GRUB during Kubuntu install as I thought I did not need it. Feisty was booting fine (shutting down was a different matter, anyway...)
Assuming my equivalent  menu.lst of:
```
title Kubuntu 7.10
root hd(1,1)
kernel /boot/vmlinuz-2.6.22-14 ro root=/dev/hda2
initrd /boot/initrd.img-2.6.22-14-generic
boot
```
is ok, I have tried a few different ways but ultimately end the same way. Like so:
[IMG]http://img151.imageshack.us/img151/7545/dsc00098yc6.jpg[/IMG]

Nothing happens at this point, it's just stuck at a blinking cursor.

Any ideas?

Oh, when I loaded the 7.10 live cd, it broke my 7.04 install, the loading bar would just stick half way.
That's not all, more worringly, after I had actually installed 7.10 and get to point of producing the above error, it causes a fail in my software raid.See [here]("http://www.overclock.net/intel-motherboards/188267-gigabyte-ds3-raid-issue-raid-0-a.html").
Is this a coincidence we were both messing around with Ubuntu? I don't overclock and this seems to me that increased temperatures are to blame, I never saw these problems with Feisty nor the 6 months of using vista and xp. :confused:

---

### Post by neu_ser on 2007-10-26
No one with any ideas at all?

I would rather the install did not see my sata drives at all, or for that matter my ntfs  on the first partition of the single IDE/pata drive. Is there something I can add to GRUB to tell it to ignore them?

Did something change in Gutsy as I think it detected the pata drive as a SDA type whereas Feisty gave it a HDA label which is what I would have expected.

---

### Post by neu_ser on 2007-10-27
Well the fix was incredibly simple; Feisty was happy with **hda2** whereas Gutsy required using **sdc2**. I guess all the jazz on the screen at boot is just what is normally hidden behind the loading bar:
```
title Kubuntu 7.10
hide hd(0,0)
root hd(1,1)
kernel /boot/vmlinuz-2.6.22-14-generic ro root=/dev/sdc2
initrd /boot/initrd.img-2.6.22-14-generic
boot
```

I also added the hide line in an attempt to stop it breaking (albeit temperarily) my software raid but the lshw command still lists sda and sdb.
Oh and network manager seems no better, possibly even worse than in 7.04, it detects the ralink card but now it does not even look for networks by default.

I was suprised to find Ubuntu did not have comprehensive wireless support built in, are all the other distros similar in this regard?

---

