---
title: "Where does GRUB install?"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Shack_ on 2007-03-05
I have a computer with Vista installed on one hard drive, and Ubuntu 6.10 on a second hard drive. I've noticed that after I installed Ubuntu (Vista was first), neither OS will boot without both hard drives plugged in. When the Vista hard drive isn't in, the BIOS reports that no OS is present. When the Ubuntu hard drive isn't plugged in, a message reports "GRUB error 27", and then booting stops.

Did GRUB install on the Vista hard drive? And now is it trying to find a file on the second hard drive, that isn't in? I really need to be able to remove both hard drives interchangeably without affecting the boot process. Any help would be much appreciated.

---

### Post by K.Mandla on 2007-03-05
It sounds like it. It would explain why you get a Grub error when you boot without the Ubuntu drive. Chances are it installed Grub to the MBR which is on the first drive, with instructions to jump to the second drive for configuration files and menu items. So if the first drive is missing, it doesn't have an MBR, and if the second is missing, Grub can't find its configuration files.

If you're going to yank one drive or the other, you'll want a boot floppy or something that will handle the boot process for you. I don't know if this will be a solution for you, but if you look into [GAG]("http://gag.sourceforge.net/"), you should be able to redirect the boot sequence to one or another without the unwanted drive being present. 

I think (and I don't know for sure because I'm imagining this stuff in my head right now) if you install Vista as normal, then install Ubuntu with both drives in, you can run the alternate CD and use the Rescue option to install Grub directly to the Ubuntu drive. Then install GAG to a boot disk and configure it to jump to one or the other partition.

Did any of that make sense? :-k

Edit: Or maybe just install each drive separately and alone, then never run it with both drives in? Hmm. Think, think. Think, think. :-k

---

### Post by Amenemhet on 2007-03-05
Edit: Or maybe just install each drive separately and alone, then never run it with both drives in? Hmm. Think, think. Think, think. 

That would be my call...because you are correct, the mbr will want to 'jump' to the second drive, grub will look for its files there. It's a master/slave issue. I assume your drives are set to master, then slave, and therefore it looks for the master, gets files required initially from drive 1, and they will be incomplete/missing if drive 2 is absent. You could set up a hardware profile...but this is a lot of explaining...and you have done the deed already so to speak. I think if you set your drives to cable select, then you would be ok, but as it stands grub needs both drives in.

---

### Post by K.Mandla on 2007-03-05
That's the solution I'm coming to. I still think it might work if a third drive is introduced, which I think could be a boot floppy. I'm fairly confident GAG could do it, but I don't have any way of defending that statement. :roll:

---

### Post by confused57 on 2007-03-05
> **Shack_ said:**
> I have a computer with Vista installed on one hard drive, and Ubuntu 6.10 on a second hard drive. I've noticed that after I installed Ubuntu (Vista was first), neither OS will boot without both hard drives plugged in. When the Vista hard drive isn't in, the BIOS reports that no OS is present. When the Ubuntu hard drive isn't plugged in, a message reports "GRUB error 27", and then booting stops.

Did GRUB install on the Vista hard drive? And now is it trying to find a file on the second hard drive, that isn't in? I really need to be able to remove both hard drives interchangeably without affecting the boot process. Any help would be much appreciated.
Yes, grub installed to your Vista drive mbr...I don't know how to restore Vista's mbr, but this may help:
[http://vistabootpro.org/](http://vistabootpro.org/)

If you're able to restore Vista's mbr, you might want to set your system up this way:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by igknighted on 2007-03-05
Theres a fairly simple solution.  If you change the first boot drive to the disk Ubuntu is on and then install GRUB to the MBR of that drive then Ubuntu and GRUB will be on the same drive.  Then if you reinstall the bootloader for vista on its drive, you can boot to grub normally on the second HD, then when you remove that HD, switch boot targets and Vista should boot from its own bootloader normally.

---

