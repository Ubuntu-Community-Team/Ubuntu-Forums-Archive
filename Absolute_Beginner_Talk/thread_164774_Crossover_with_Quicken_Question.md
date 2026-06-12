---
title: "Crossover with Quicken Question"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by landsg on 2006-04-23
Just installed Crossover and then put Quicken 2005 on my Ubuntu box.  It works fine, however when I try to backup my data to a USB hard drive, Quicken doesn't see it.  I can see it from the Ubuntu desktop, however, where it is shown as read-only.

How can I make Quicken see this drive so I can back up data to it?  

Assuming that my other XP apps will have the same problem if I try to save to the external usb drive.

---

### Post by Kethinov on 2006-04-23
Your USB drive is just a folder somewhere on the computer. WINE may not have defined it as a windows "drive" but you can navigate for that folder in the Linux filesystem. It's probably something like /media/usbdisk or something similar. There is probably a drive in WINE called "Root" which is where you'd start, then you'd find media, then you'd find the name of your USB disk.

---

