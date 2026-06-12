---
title: "GRUB error 21- odd load"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Wrackad on 2008-01-20
A little background...

I am trying to run Ubuntu on my laptop that has a non-working CD\DVD rom drive. I connected the laptop drive to my desktop ( via a USB to IDE/EIDE adapter)and booted to the Ubuntu CD I made from the downloaded .iso. I ran Ubuntu from the CD and kicked off the install to the connected laptop drive. It completed the install and asked for a reboot. Once I rebooted, I removed the CD and I disconnected the external drive and got GRUB error21. which to me is odd since I only installed to the external drive.

Now when I boot I can only get to a list of OS to boot from if I have the CD in and the external drive connected. 

Do I need to uninstall Ubuntu from the local HDD (that I did not install it to anyway) so that I can boot my desktop to WinXP normally. The desktop is primarily my wife's pc so naturally she is a bit upset. 

I would not even mind if GRUB was working properly and initially showed me a list of OSes to chose from.

:confused::confused:

---

### Post by capink on 2008-01-20
It seems that what happened is that you installed grub stage1 file to your MBR "Master Boot Record" of the internal hard. While the grub stage2 is installed somewhrere on the external drive.


If you have the Windows cd follow this [guide]("http://amazingrando.wordpress.com/2007/04/05/fixmbr-is-your-friend/"). to correct the problem.

---

### Post by Thund3rstruck on 2008-01-20
For whatever reason (which I cannot explain) if you install Ubuntu on a separate physical disk the Ubuntu installer is not capable of handling this. I recently installed Ubuntu on a 500GB SATA disk which was a separate disk and I got grub error 21 as well. Apparently you can hack the grub configs to allow this type of configuration but I never got around to doing  that.

---

### Post by capink on 2008-01-21
> **Thund3rstruck said:**
> For whatever reason (which I cannot explain) if you install Ubuntu on a separate physical disk the Ubuntu installer is not capable of handling this. I recently installed Ubuntu on a 500GB SATA disk which was a separate disk and I got grub error 21 as well. Apparently you can hack the grub configs to allow this type of configuration but I never got around to doing  that.

You just have to make sure not to install grub in the MBR of the first harddisk (hd0). Instead install it to the MBR of the second disk (hd1).

---

