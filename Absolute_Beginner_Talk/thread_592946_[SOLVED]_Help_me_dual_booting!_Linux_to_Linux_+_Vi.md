---
title: "[SOLVED] Help me dual booting! Linux to Linux + Vista!"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-10-26
Well, I am using [this]("http://acpmag.com/5045/how_to_dual_boot_vista_with_linux") guide to dual boot vista and ubuntu. But, I installed Vista, changed the boot thing, and installerd and used the program easily. Still, when I open my computer and select to boot from Ubuntu (Gusty), an error happens. I can boot normally to Vista. Any help?

---

### Post by n3tfury on 2007-10-26
we'll need more info - specifically exactly what the error is. also, did you mean "can't" boot to vista?

---

### Post by Inxsible on 2007-10-26
you can also try this simpler guide to installing

[Psychocats Installing Ubuntu]("http://ubuntuforums.org/www.psychocats.net/ubuntu/installing")

You don't really need EasyBCD. That's only a bootloader modification tool for windows. Grub does the same thing and is installed automatically when you install Ubuntu

---

### Post by Fixman on 2007-10-26
Okay, heres the information:

I am booting Vista with the EasyBCD program to "easy dual boot" from Vista. There I can boot Vista normally, but I can't boot Ubuntu. If, instead of setting the boot flag to the Vista partition, I set it to the Ubuntu partition, Ubuntu loads perfectly.

When Ubuntu doesn't load (Vista partition, using EasyBCD) it gives me an error about that it ocouldnt find a file.

If you can't help me, then I will appreciate (very mutch) the following help:
A substitute to EasyBCD, (better if its a linux binary)
An easiest way to move the "boot" flag from MBR (I move it using Gparted)

---

### Post by Fixman on 2007-10-26
I found a workout:

If you have this error:
Go to EasyBCD, delete all partitions [except for WinVista :-)]
Create the Ubuntu partition as Grub
Go to "Manage partitions" and MAKE SURE THAT the Ubuntu Partition is set to BOOT (not to C:/)
Reboot the computer, and access Ubuntu. You shall still be having the same error
On the upper line of the manu, press "e" to edit.
Again, on the first line of the new menu, press "e" again.
Change that line to "root (X)", wherre X is the partition where Ubuntu is (generally h0,0)
Press "b" to boot and...
Enjoy having an Ubuntu and have the avalability to run games!

---

### Post by Computer Guru on 2007-10-27
You can also use the GRUB command "find --set-root /boot/kernel*****" instead of "root(x,y)" to dynamically locate the Ubuntu drive each time.

---

