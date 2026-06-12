---
title: "GRUB Hard Disk Error"
date: 2008-04-25
forum: Apple Hardware Users
---

### Post by kyebach on 2008-04-25
Sorry if this question has already been answered in another post but I did search and didn't have any luck finding a solution to my specific problem.

So I'm new to ubuntu but did try the 7.10 liveCD and found that interesting so when 8.03 came out I thought I might as well install it and give it a go for a while. So I installed it on my MacBook which already had a bootcamp partition running windows XP and Leopard. My mistake was to install it to a USB flash drive which I now know isn't supported. So my problem now is I can't load Ubuntu off the usb key or boot up my Windows XP. Both of them give me the same error of "GRUB Hard Disk Error".

All I want now is to be able to boot Windows XP again without having to reinstall it. Is there a way I can completely uninstall ubuntu and or grub?

If and when hopefully I can get my windows booting again what is the best way to install ubuntu on a bootcamp partitioned mac. Is there a good tripple boot setup? Unfortunately it doesn't look like installing onto an external drive is an option right now.

Thanks in advance.

---

### Post by cyberdork33 on 2008-04-25
boot OSX, install refit, and reboot into the refit menu and select the partition tool sync the partition tables. then you should be able to boot windows. This will happen again when you install Hardy in the future.

---

### Post by kyebach on 2008-04-25
Wonderful. Thanks for the tip, I'll try that and post if it worked for me. 

Thanks!

---

### Post by billbear on 2008-04-26
Because you installed grub to the MBR of your internal disk, and grub points to the external drive that may not be bootable, you got this GRUB Hard Disk Error.
Now you need to boot from XP install cd and repair the master boot record by using the FIXMBR command from the Windows XP Recovery Console. This will erase grub and you will be able to dual boot.

cyberdork33: Installing to the external will not erase the MBR table of the internal so a sync is not needed.

---

### Post by cyberdork33 on 2008-04-26
> **billbear said:**
> cyberdork33: Installing to the external will not erase the MBR table of the internal so a sync is not needed.
OK. similar sounding error that other were having.

---

### Post by kyebach on 2008-04-26
Thanks so much for the FIXMBR tip Billbear. I worked like a charm.

I know the flash drive is bootable on my machine as I've booted OS X systems off it but never a linux or windows system. Is it possible? 

Next I think I'll just install Hardy Heron as an application in windows. Is it that much slower? I imagine it would be faster then booting it off a usb key now that I think about it.

---

### Post by billbear on 2008-04-27
> **kyebach said:**
> 
I know the flash drive is bootable on my machine as I've booted OS X systems off it but never a linux or windows system. Is it possible? 

You can boot OS X from external drives because it boots directly from EFI firmware. linux/windows (so called 'legacy' OSes) need a bios to boot, apple's firmware simulates a bios, it works for the internal disk but seems to not support booting 'legacy' OS from external. Grub2 will be able to boot natively from efi, so wait for grub2 final release. Or wait for apple to release a firmware update.

> **kyebach said:**
> 
Next I think I'll just install Hardy Heron as an application in windows. Is it that much slower? I imagine it would be faster then booting it off a usb key now that I think about it.
It's a good idea. You don't have to mess with partition problems. 8.04 Hardy has a bug that will likely to make windows unbootable. I have not tried wubi myself so please post here your experience.

---

