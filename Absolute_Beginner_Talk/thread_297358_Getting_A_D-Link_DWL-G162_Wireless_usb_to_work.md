---
title: "Getting A D-Link DWL-G162 Wireless usb to work"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by lucasl on 2006-11-11
Hi everyone,
I am completely new to linux and ubuntu, I barely know how to use the kernel and I would like to know how would I get a DWL-G162 Wireless usb to work. I have google this and found some things like "do this", "install that", but still I have no idea.
Thanks, and sorry for being a newb.

EDIT: I typed lsusb in the terminal and it shows up as "D-Link Corp.", but it isn't receiving power (light isn't on).

---

### Post by lucasl on 2006-11-11
I found that madwifi is the driver I need and it is on the system, but how do I use it?
Thanks!

PS. I tries insmod /lib/modules/2.6.17-10-generic/madwifi/ath_pci.mo but it said operation not permitted

---

