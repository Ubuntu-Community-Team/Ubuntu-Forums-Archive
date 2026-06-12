---
title: "Ubuntu not booting"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by csurdongulos on 2006-09-14
Hi everybody,

yesterday I installed ubuntu on my pc, I had win xp on primary partition, windows vista on logical, I could choose which one I wanted to boot.

I had a separate logical partition and a swap partition ready for ubuntu to take its place. installation went fine, but I had no option in the bootmenu to choose ubuntu.

I guess the reason for this is that it is on a logical partition after the primary xp partition.

is it possible to boot ubuntu from a logical partition? I was looking for some bootmanagers but they didn't recognie the ubuntu partition to be bootable.

do you have any recommendations for a bootmanager which I could use to choose which os to boot?

thanks for your help in advance
Viktor

---

### Post by benfindlay on 2006-09-14
Did you install GRUB into the MBR? This would give you a boot list with ubuntu at the top of the list I believe

---

### Post by csurdongulos on 2006-09-14
didn't see an option for it. should I have chosen to install that before the ubuntu install procedure?

where can I find that? and now that ubuntu won'T boot, I'll have to run the live cd again and do it all over? though not a big issue, didn't take long.

---

