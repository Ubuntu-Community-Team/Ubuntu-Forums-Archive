---
title: "Windows 8 partation size"
date: 2013-04-04
forum: Any Other OS
---

### Post by ads2996 on 2013-04-04
Hi,

I am currently reworking my laptop partations to triple boot, ubuntu, win 7 and win 8. My question is how big should i make the won 8 partation. my win 7 will be 90gb and my ubuntu will be 25gb, with the rest of my 320gb drive split between win 8 and data.

Thanks for any advice

---

### Post by mamamia88 on 2013-04-04
How much space does microsoft reccomend?  That's a start [http://windows.microsoft.com/en-us/windows-8/system-requirements](http://windows.microsoft.com/en-us/windows-8/system-requirements). Personally I reccomend using as little as possible and have a 4th partition for data with a filesystem that can be read and written too from any os.  I'd reccomend ntfs for that

---

### Post by oldfred on 2013-04-05
To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Even dual booting two copies of Windows this applies:

 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

