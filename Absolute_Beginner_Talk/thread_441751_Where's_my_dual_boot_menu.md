---
title: "Where's my dual boot menu????"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by 3pinner on 2007-05-12
I installed Feisty on unallocated space, on the same hard disk containing Windows 2000.
I wanted to dual boot.
When I rebooted after installing Feisty, all I got was the usual Windows 2000 boot menu, no mentions of Ubuntu.
So did I make a mistake in the install?
How do I get the dual boot menu?
Just thought of it------when I installed Ubuntu, I partitioned the HD manually to partition the unallocated space, and remember a checkbox to install (the boot loader???)at the beginning of the drive or end of the drive. I chose end of the drive.
If that choice was for the boot loader, I assume the problem is Windows bootloader is usually at the beginning of the drive, so when the system starts, the other one isn't even available?
Does that make ANY sense at all???)
Thanks

---

### Post by 3pinner on 2007-05-12
bump

---

### Post by Duck2006 on 2007-05-12
You need to install grub to your mbr. Boot up from the live CD,
then go to Applications=> Accessories=> Terminal  and type

sudo grub

at the grub promp type

find /boot/grub/stage1

it will come back with (hdx,x) ie (hd0,1)

root (hdx,x)

setup (hd0)

quit

close and reboot if all goes well your boot in to ubuntu

---

### Post by 3pinner on 2007-05-13
Thank you
I assume after I find Grub, the commands you gave me will locate it in the proper place?

root (hdx,x)     I replace the "x" s with the designation for my root drive?

setup (hd0) I just type that in as-is to locate it on the first physical drive in the system? (I have two drives)

I also assume Leave out the parantheses? :lolflag: 

Thanks

---

### Post by Duck2006 on 2007-05-13
> I also assume Leave out the parantheses

No type as is 

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx,x)
quit

---

### Post by 3pinner on 2007-05-13
Thank you,
I'll post back with results for the benefit of anyone else that has this problem.
(Best forum I've been to!):biggrin:

---

### Post by 3pinner on 2007-05-14
Alllllllllllll righty then.......
After spending ALL DAY reinstalling my windows 2000, I'm ready to try and figure out what the heck happened...
I ended up reinstalling Ubuntu, locating the boot partition at the front of the drive.
Grub finally showed up at the boot screen, but when I clicked on Ubuntu - I got an error message (don't remember the number) that said the partition did not exist. hmmmmmmm.......

So I tried selecting my Windows 2000 OS, and got the message NTLDR is missing. Wouldn't start even after installing that.
Turns out there were some other files corrupted somehow, so it was install Windows in a different folder on the same drive so I could access my files, come up with another hard drive and the rest is wearisome history............:confused: 

I think the issue was a bad install of Windows in the first place. I kept getting letters other than C for the drive designation.
Anyway.
At least I have an operating computer now.
Next try will be to install Ubuntu on a seperate hard disk.
Maybe as a dual boot, maybe not.

I'm even thinking of disconnecting the Windows HDD when I install Ubuntu on the other, then reconnecting the Windows drive and loading a boot loader seperately somehow.
Now I'm really chicken!:lolflag:

---

