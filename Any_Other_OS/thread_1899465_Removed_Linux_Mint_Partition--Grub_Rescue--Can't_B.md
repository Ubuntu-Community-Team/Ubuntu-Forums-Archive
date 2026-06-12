---
title: "Removed Linux Mint Partition--Grub Rescue--Can't Boot from CD"
date: 2011-12-23
forum: Any Other OS
---

### Post by segerfan83 on 2011-12-23
Hi all,

I'm extremely new to Linux and have run into my first real problem.  I am running a Lenovo Ideapad Z560 with Windows 7 installed. I installed Linux Mint last month and last night decided to remove that partition which I did under windows disk management (I don't remember if I used WUBI or rebooted from a Live disk to install Mint in the first place).  I continue to use windows just fine for the rest of the night.  This morning I wake up and all I can get to is the grub rescue screen.  I've read many threads online trying to fix this myself, but to no avail for one main reason.  I can't boot from a CD.  My comp won't let me enter the BIOS at all (F8, F12, Esc, F1, F2, etc...) and entering a CD into the drive does nothing.  I have a windows recovery disk and a Ubuntu Live Disk, but they do me no good since I can't get past this grub rescue screen.  I've entered "ls" and got "(hd0) (hd0,msdos5) (hd0,msdos4) (hd0,msdos2) (hd0,msdos1)".  When I enter "set" I get "prefix=(hd0, msdos6)/boot/grub root=hd0,msdos6".  

Any help would be greatly appreciated.  Again, I can't enter BIOS and I haven't been able to boot from any CD.  Thanks ahead of time!

---

### Post by howefield on 2011-12-23
Thread moved to "*Other OS/Distro Talk*" forum.

---

### Post by LinuxFan999 on 2011-12-23
If you have another computer, take the hard drive out of your laptop, then connect it to the other computer and format it there, then put it back in the laptop and try booting from a CD, or loading the BIOS. It seems weird that Grub can prevent those two things.

---

### Post by segerfan83 on 2011-12-23
How would I connect a hard drive from one laptop to another?

In the meantime, I put LiLi on a jump drive and have tried to boot from that following these instructions:  [http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293) Either I am doing something wrong, but it won't let me load from the jump drive.  It recognizes that the jumpdrive is in because ls shows a new drive as (hd1) and also (hd1,msdos1).  I'm not getting anywhere.

---

### Post by segerfan83 on 2011-12-24
Update:  I used startup disk creator to mount ububtu live to a jump drive, but at the grub rescue prompt, I can't get the computer to open up the usb drive using "ls (hd1)", "ls (hd1)/boot/grub", or "ls (hd1)/usr/lib/grub/i386-pc".  Its odd; when I plug the jump drive into another computer, it flashes like the computer is working with it.  When I plug it into the afflicted computer, nothing happens, but "ls" shows that it is plugged in.  

If I can't fix this issue in a conventional way and I have to attached the afflicted hard drive to another computer, what would be the route I would need to take to recover windows?

---

### Post by BC59 on 2011-12-24
Try to pull out the battery and leave it for a while. Then put it again and try to enter to BIOS with F2.

---

