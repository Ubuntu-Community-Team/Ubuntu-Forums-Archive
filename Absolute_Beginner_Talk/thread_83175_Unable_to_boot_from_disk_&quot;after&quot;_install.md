---
title: "Unable to boot from disk &quot;after&quot; installation"
date: 2005-10-28
forum: Absolute Beginner Talk
---

### Post by SepticInsect on 2005-10-28
Hi,
I've tried installing Ubuntu several times and failed every one. When the installation copies the files to disk and reboot, the system won’t start. I get the error message "Unable to boot from disk".

I've tried to partition the disk automatically and manually with no luck. Does anybody have an idea what the problem can be?

System information:
AMD 1.2GHz
80GB hdd
256 MB RAM

Thanks!

Erik

---

### Post by heimo on 2005-10-28
[quote=SepticInsect]
  Does anybody have an idea what the problem can be?
[/quote]

Not really... Did you install grub on MBR at the very end of the first part of install? You could try to go back at the end of install (there's option to do this) and install lilo instead. This isn't optimal solution (you'll lose some features like splash image on boot) but if you can't get it working otherwise and lilo works, it's better than nothing. :) Just an idea.

BTW, is the disk parallel ata (wide connector, cable like [this]("http://en.wikipedia.org/wiki/Image:Nappe.png")) or serial ata (cable like [this]("http://en.wikipedia.org/wiki/Image:SATA_Data_Cable.jpg"))?

---

### Post by SepticInsect on 2005-10-28
Thanks from the reply!

[QUOTE=heimo]Not really... Did you install grub on MBR at the very end of the first part of install? You could try to go back at the end of install (there's option to do this) and install lilo instead. This isn't optimal solution (you'll lose some features like splash image on boot) but if you can't get it working otherwise and lilo works, it's better than nothing. :) Just an idea.
[/QUOTE]
OK, I will try to install lilo in the weekend.

> 
BTW, is the disk parallel ata (wide connector, cable like [this]("http://en.wikipedia.org/wiki/Image:Nappe.png")) or serial ata (cable like [this]("http://en.wikipedia.org/wiki/Image:SATA_Data_Cable.jpg"))?
The disk is parallel ata (isn't that called IDE?). Why do you wonder?

Erik

---

### Post by LHZ on 2005-10-28
Just to be sure: did you install Ubuntu to a bootable partition? It should have a little lightning bolt in the partition manager. I'm pretty sure you have to, but you never know.

---

### Post by SepticInsect on 2005-10-28
[QUOTE=LHZ]Just to be sure: did you install Ubuntu to a bootable partition? It should have a little lightning bolt in the partition manager. I'm pretty sure you have to, but you never know.[/QUOTE]

Yes.

---

### Post by Cufishing on 2005-10-28
I had this issue as well. My problem was found to be within my BIOS. 
Within your BIOS usually under the first menu, you can find your drives. Mine was set to manual, as I had it set this way. I changed it from manual to Auto-Detect, then pressed the <F3> key to auto detect. <F3 may be different in your BIOS>. Once BIOS auto-detected the HDD, issue was solved.

---

### Post by SepticInsect on 2005-10-28
Thanks! I will try that.

Erik

---

### Post by SepticInsect on 2005-11-03
Still need help!

I tried to install lilo instead of GRUB, that didn't help.

I tried to hdd was already on auto but i tried to change it to maunal but that didn't help either.

Any more suggestions?

I'm thankful for all the help I can get!

Erik

---

### Post by Herman on 2005-11-03
Hi! Have a read of this link and see if there's anything in it that interests you.
[http://www.ubuntuforums.org/showthread.php?t=79286&highlight=gag](http://www.ubuntuforums.org/showthread.php?t=79286&highlight=gag)
                                                                                                            (herman)

---

