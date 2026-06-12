---
title: "GRUB Error 15 -- Please help!!"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Veggieb0i on 2007-03-01
Well...
Ubuntu has been rather stubborn. 

I installed Ubuntu (edgy) Amd64 alternate, and since then I have not been able to boot back into Windows XP (second drive). This is the worst possible thing I can imagine happening besides a crash, but it's worse because I cannot use my wireless card with Ubuntu, so I have no access to the internet.

When I have both drives connected and attempt to start Windows, I get "GRUB Error 15".
When only the Windows drive is connected, I think I get Error 12. Maybe 27?... I'm bad with remembering numbers because I do it mathematically...

Anyway... because this is the 64 bit version, I can't run 32 bit programs, and apparently WINE has to be recompiled, and I have zero experience with this and have no clue where to start.

I cannot boot the Windows drive from this (my dad's) computer either, it just doesn't recognise it at startup. I can, however, access files from it this way...

And additionally, the Windows drive does not appear connected at all to Ubuntu.
I installed it with the Windows drive disconnected... probably why.

But is there anything I can do about this? I have no idea why GRUB was even loading with the windows drive, apparently it's installed on it somehow..

Any help would be appreciated greatly!!
I haven't been on the internet for like 4 days! :mad:

---

### Post by Dr. Nick on 2007-03-01
Have you pulled the linux drive and reset the jumpers and ide cables to make the windows drive the primary, then go into the bios and rescan the hard drives

Had you left the windows drive plugged it grub would have set it all up automatically.

To get to your windows drive in ubuntu try this
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by geirha on 2007-03-04
Grub error 15 means he can't find windows on the given partition. Ubuntu and grub don't always agree which harddisk is the "first". So ubuntu has probably guessed wrong here.

What you should try is this:

Reboot.
At the boot menu, select Windows and hit **e** to edit.
In the list you see now, there should be one line that says something like:
```
root    (hd0,0)
```
where *hd0,0* in this case would mean first partition of the first harddrive, but it could be that grub thinks the drive with windows is the second or third drive (depending on how many harddrives you have).

So, hit **e** again to edit the *root*-line, change it to ```
hd1,0
``` for example, to try the first partition of the second harddrive. then hit **b** to boot, it should either boot, or give you Error 15 again. Try with other values for hdX,Y untill you find the right one.

When you find the right one, you should boot ubuntu and edit /boot/grub/menu.lst to make the change permanent, you'll probably find the windows-section somewhere around the end of the file.

---

### Post by marmaladejackson on 2007-03-04
I had a lot of problems getting things to boot right.

Try [super grub.]("http://somafm.com/dronezone.pls")

It helped a lot.  For a while there, I was unable to get XP or Ubuntu, and was just about faced with doing clean wipe and install.  Of course, I had nothing backed up.

---

