---
title: "No EFI for &quot;64-bit Mac&quot; distribution"
date: 2014-06-09
forum: Apple Hardware Users
---

### Post by jmjohn on 2014-06-09
Alright, so I've got a Mac, and I'm wanting to install Ubuntu. I look through the options, and I see "64-bit Mac" as an option. Perfect!

Except wait... **not** perfect. Because the normal 64-bit release has an EFI bootloader, but mysteriously, the 64-bit Mac version doesn't! Which means that it's unbootable from USBs on most Macs, which require an EFI bootloader.

I know there's a scarcity of time and resources, but... really? Why label something Mac-specific when it's less Mac-compatible than the normal release?

Alright, enough. Hope this thread can prompt a change.

---

### Post by bapoumba on 2014-06-09
*Thread moved to **Apple Users**.*
Edited thread title.

---

### Post by PartisanEntity on 2014-06-10
There is an easy fix, installed [refind]("http://www.rodsbooks.com/refind/"), this will allow you to boot Ubuntu in EFI mode.

This is how I did it back when I was dual booting Ubuntu and OSX

---

