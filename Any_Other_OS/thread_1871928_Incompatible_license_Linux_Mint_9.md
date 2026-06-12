---
title: "Incompatible license Linux Mint 9"
date: 2011-10-29
forum: Any Other OS
---

### Post by kikotiger on 2011-10-29
I have the same problem but with Linux Mint 9. I did a fresh install and when rebooted the same problem came up
Incompatible license
grub rescue>

I did what you suggested, selected the USB to boot from but did not boot into the Live CD. It actually booted into the system I installed. I thought it  might had fixed the problem so I booted without the USB and same problem. So I booted again with the USB and it booted my system. And no, I did not install the OS in the USB.
I ran that script and I attached the results. Let me know if you want me to post the results instead of the file.

---

### Post by kikotiger on 2011-10-29
I don't think grub was installed. I run the command 
sudo grub
and it said that grub was not found. I used Boot-Repair and it fixed the problem, follow this link.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Also after updating the system it asked me to install grub-pc since it was not installed on any of my partitions. I only have Linux Mint 9.
Hope this helps anyone.

---

