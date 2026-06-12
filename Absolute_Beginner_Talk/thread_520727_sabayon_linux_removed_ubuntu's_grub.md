---
title: "sabayon linux removed ubuntu's grub"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by threeonethree on 2007-08-08
hi , i installed sabayon linux on top of ubuntu linux (made new / partition and used shared swap ) .. when it was installed it over written the ubuntu grub .. i have option of booting sabayon linux or other (other menu brings up another grub which is used to boot my slax and windows) .... how can i add the enteries to ubuntu linux back in sabayons grub so it gives me choice to boot ubuntu? please help

---

### Post by Happy_Man on 2007-08-08
Well, just copy the Ubuntu entries off its menu.lst into Sabayon's menu.lst. That should do it.

---

### Post by ron999 on 2007-08-08
Well, first thing is that you need to know where Ubuntu is installed ie which drive and which partition.

Then you need to add these lines to your sabayon grub. It may be a file named menu.lst (that's what Ubuntu calls it).
But when you add these lines you need to replace (hd0,0) with the location of Ubuntu.
But be careful, the drives and partitions start from zero.
So second drive and fifth partition would be (hd1,4)

These are the lines that I think you need to add:-
[B]title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a07b615d-3f3d-4125-92ed-e9135be51175 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a07b615d-3f3d-4125-92ed-e9135be51175 ro single
initrd		/boot/initrd.img-2.6.20-16-generic[/B]

Don't forget to save it!


Edit I've had second thoughts. I'm not sure that the UUID number is correct for you. I need help from somebody else.

---

### Post by Happy_Man on 2007-08-08
> **ron999 said:**
> Well, first thing is that you need to know where Ubuntu is installed ie which drive and which partition.

Then you need to add these lines to your sabayon grub. It may be a file named menu.lst (that's what Ubuntu calls it).
But when you add these lines you need to replace (hd0,0) with the location of Ubuntu.
But be careful, the drives and partitions start from zero.
So second drive and fifth partition would be (hd1,4)

These are the lines that I think you need to add:-
[B]title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a07b615d-3f3d-4125-92ed-e9135be51175 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a07b615d-3f3d-4125-92ed-e9135be51175 ro single
initrd		/boot/initrd.img-2.6.20-16-generic[/B]

Don't forget to save it!


Edit I've had second thoughts. I'm not sure that the UUID number is correct for you. I need help from somebody else.
Yeah, I thought the UUID is different for each computer (though it seems to stay between distros on the same computer. Huh?). Of course, you can use absolutes like /dev/hda5 instead of a UUID.

---

### Post by ron999 on 2007-08-08
Yes absolutely, try using absolutes. Thanks happy_man:lolflag:

---

