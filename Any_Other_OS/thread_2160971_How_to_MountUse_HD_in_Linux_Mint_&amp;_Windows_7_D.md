---
title: "How to Mount/Use HD in Linux Mint &amp; Windows 7 Dual boot"
date: 2013-07-08
forum: Any Other OS
---

### Post by kenizl86 on 2013-07-08
Hello,

   I recently installed Linux Mint alongside Windows 7 (with Windows 7 being the primary OS), and Linux Mint won't mount the Hard Disk from the Windows 7 OS. I can use the partition (or whatever it does when you use the Windows Installer version for Mint 15) for the Linux side of it just fine.

Any idea of what to do? Thanks for the tips!

---

### Post by coffeecat on 2013-07-09
> **kenizl86 said:**
> I can use the partition (or whatever it does when you use the Windows Installer version for Mint 15) for the Linux side of it just fine.


Does this mean that you used the Mint version of the wubi installer? I think the equivalent is called mint4win in Mint. If it is like wubi, then your Windows C: partition is already mounted inside the /host folder. Open the file manager and click on "Computer", "File System", or whatever Mint calls the selection to show the main system filesystem. You should see the /host folder with all the other system folders. Open /host and you'll see the Windows C: folders.

I hope that gets you where you need to go. One thing that puzzles me is that Mint 15 is based on Ubuntu 13.04, but 13.04 dropped the wubi installer due to lack of developer time. Perhaps a Mint user will have more information.

---

