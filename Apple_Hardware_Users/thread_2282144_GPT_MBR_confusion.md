---
title: "GPT MBR confusion"
date: 2015-06-12
forum: Apple Hardware Users
---

### Post by ruota on 2015-06-12
Hi,
while I tried to install ubuntu 12.04.5 amd64 on my macbook 5,3 , which ultimately I failed to install because the installation of grub fails.
but the more serious problem is that the partition table is this:

[ATTACH=CONFIG]262535[/ATTACH]

in this moment i have os x and windows 7 (bootcamp)
Help me!!
Thanks

---

### Post by oldfred on 2015-06-12
To boot Windows in BIOS mode you have to have MBR, but Macs use gpt and boot in UEFI mode.
And Ubuntu can use gpt with either BIOS or UEFI.

You then have hybrid partitioning which you must keep in sync. And only use the MBR for your Windows. Hybrid not normally recommended because of the sync issues.

       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

---

