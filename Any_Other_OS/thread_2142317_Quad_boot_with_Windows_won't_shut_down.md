---
title: "Quad boot with Windows won't shut down"
date: 2013-05-05
forum: Any Other OS
---

### Post by pimaster on 2013-05-05
I quad boot Windows XP, 7, 8 and Ubuntu 12.04, and that has been working fine for a while. However now when I tell Windows 8 to shut down, it goes into sleep mode. This even happens when press the shut down button on the pc. What I am currently doing is restarting, getting to the grub menu then pressing the power button on the computer. Could this be something to do with the boot flag, or is windows confused about something? Sorry this isn't a very ubuntu related post, but most other solutions seem to be with just W8 installed on the hard drive. Thanks for any help!

---

### Post by sid0972 on 2013-05-06
have you tried shutting down in win 7 and xp?

---

### Post by oldfred on 2013-05-06
Is it related to Windows 8 always hibernated?
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

Do you have each Windows installed in primary partitions with their own boot files, or did you let each install overwrite the boot files in the first install that had boot flag?
      
 Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

