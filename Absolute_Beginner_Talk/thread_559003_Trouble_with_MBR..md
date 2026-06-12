---
title: "Trouble with MBR."
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by matariu on 2007-09-24
Since i am a super beginner with linux so i even doesn't know where to look..

I have a laptop with dual OS (Win Vista and Kubuntu), i'd like to update my vista basic to vista premium. but there's a trouble when i tried to install my windows, because windows setup said that the setup did not find any hard disk drive installed..

I think this must be a problem with linux, so i try to remove linux from windows, all linux partition have been erased, and when i reboot, my system won't start (GRUB loader missing, error 22). so i looked over the internet to solve my problem and come up with fdisk solution. But unluckly i cudn't even access my computer. so how cud it'll be possible??

Please, give me an advice to solve this matter, as simple as possible..



Thanks,

---

### Post by kellemes on 2007-09-24
From the Windows-setupcd/dvd you can enter the recovery-console, from there you need to enter "fixmbr" I believe, this will fix the Windows-bootloader.. If you enter "help" you get all the commands there are..
You can also burn and boot with [SuperGrubDisk]("http://supergrub.forjamari.linex.org/") to fix your MBR (your bootloader so to speak)

---

### Post by Hospadar on 2007-09-24
> **kellemes said:**
> From the Windows-setupcd/dvd you can enter the recovery-console, from there you need to enter "fixmbr" I believe, this will fix the Windows-bootloader.. If you enter "help" you get all the commands there are..

Yeah, just so you know, (because we all love to learn!) every hard drive has a master boot record, which normally contain the bootloader (GRUB for linux or NTLDR for windows) and when you install linux it will overwrite the windows bootloader in the master boot record (unless you manually put grub elswhere, you can put it on the same partition as linux is installed) so when you remove linux, grub will still be there partially but not in a functional sort of way.  the fixmbr command will reinstall the default windows boot loader as it would have been set up by a windows install but depending on where you put grub, grub will probably be overwritten.

So, don't worry if that doesn't make any sense, fixmbr should solve your problem, but maybe you learned something too! =)

---

### Post by matariu on 2007-09-24
Thanks for the advice,

but i cudn't access my recovery console (since the setup didn't detect any hard drive). and i already burn and use Gparted but it came for nothing..

Right now i already re-formatted my hard disk, and it shows error message 
(invalid system disk, replace the disk, and so on..)

Any idea?

---

### Post by kellemes on 2007-09-24
Try SuperGrubDisk..
Here you should be able to clean your MBR.. Since you're starting over this is what you want anyway..
From most GNU/Linux livesystem you can use GParted to repartition your drive so Windows will detect it again, I guess.. I don't understand Windows sometimes.. :popcorn:

---

