---
title: "MacBookPro13,1 internal NVME SSD not visible in 16.10 installer"
date: 2016-11-08
forum: Apple Hardware Users
---

### Post by ramseygurley on 2016-11-08
When I boot into Try Ubuntu and open the installer, no internal SSD is visible to install Ubuntu. The only visible drive in Disks is the USB stick I have booted. I tried adding **nvme_load="YES"** and **nvd_load="YES"** (mentioned here: [http://manpages.ubuntu.com/manpages/xenial/en/man4/nvd.4freebsd.html](http://manpages.ubuntu.com/manpages/xenial/en/man4/nvd.4freebsd.html)) in addition to **nointremap** (required, otherwise I get a black screen) to the kernel parameters, but that did not help.

Also, keyboard and trackpad are dead. The only key that works is the power key. Any help on those would be great as well. :)

---

### Post by lucperte on 2017-05-28
[SIZE=4][FONT=arial]Hi I have the same trouble with my MBP 13,1. 
Used external keyboard an mouse to navigate the installer menu, that works but Ubuntu don't see APPLE SSD AP0256J [SIZE=4]and I am stuck[/SIZE]. 
[/FONT][/SIZE][SIZE=3]looking at various forums I haven't found the solution.[/SIZE]

---

