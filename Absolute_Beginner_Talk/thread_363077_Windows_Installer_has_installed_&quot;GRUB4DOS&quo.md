---
title: "Windows Installer has installed &quot;GRUB4DOS&quot; instead of Ubuntu?"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by jacobdis on 2007-02-16
Hi, I'm running Windows XP and the LiveCD wasn't working for me (computer simply hung at "Press any key to boot from CD..."), so I gave the Windows Installer a try.  The installation downloaded something roughly 700MB (which took forever, regardless of my broadband connection) and prompted me to reboot.  I did so, and selected the Ubuntu menu option from the boot menu.

However, instead of booting me into Ubuntu as I expected, I was placed into a "GRUB4DOS", which seems to be a command-line interface with a line that says "grub> " awaiting my input.  I do not know how or why this happened, or if there are any additional steps required to actually boot into Ubuntu, but if anyone could point me in the right direction it would be greatly appreciated.

---

### Post by meng on 2007-02-16
Go back to the Live CD or else try the Alternate CD (yes, it's another 700 MB download).

Troubleshooting:
1. check md5sum of the downloaded iso, and rule out a corrupted download
2. reburn iso at lower speed, e.g. 4x
3. try alternate if live cd is not working for you.

---

### Post by jacobdis on 2007-02-16
Thanks for the quick reply.  I do have a question regarding the ISO this installer has supposedly downloaded.  I selected the default UBUNTU option at the beginning of the Windows Installer and after the download was complete, I assume it ran the 603,380kb file "setup-ubuntu-full.exe" which extracted "ubuntu-6.10-desktop-i386.iso" into C:\ubuntu?
Other sources I have looked at say that the ISO belongs in C:\, instead of C:\ubuntu. Can anyone clarify?
Thanks.

---

