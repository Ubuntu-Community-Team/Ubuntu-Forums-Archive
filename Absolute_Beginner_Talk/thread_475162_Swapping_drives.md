---
title: "Swapping drives?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Psyktek on 2007-06-15
I have a new Ubuntu installation on an internal HD. I also have a USB external drive that I keep forgetting about.
The internal drive is about filled and I'd like to install/reinstall feisty on the USB drive. Can this be done? Does the original HD installation need to be removed? Are there issues with access speed that are gonna drive me nuts?

As an aside, I know I have to use the DOS prompt to format /mbr. However, when I open the DOS window under XP it shows "C:\\Documents and settings/etc...>"
I can get rid of this except for the '>' but it won't recognize/execute the format /mbr command.

Feel free to answer this mess in chapters if necessary. ;)

Bob

---

### Post by bobplano on 2007-06-15
the right command is fixmbr for the recovery cd. i don't know if that will work in a current install command prompt but you can try. if that doesn't work and you can't find the recovery cd, there's fixmbr programs on the internet.

---

### Post by logos34 on 2007-06-15
> I have a new Ubuntu installation on an internal HD. I also have a USB external drive that I keep forgetting about.
The internal drive is about filled and I'd like to install/reinstall feisty on the USB drive. Can this be done? Does the original HD installation need to be removed? Are there issues with access speed that are gonna drive me nuts?
 
You might want to consider just cloning the ubuntu partition to a partition on the usb drive using Partimage.  It's on the [SystemRescueCD.]("http://www.sysresccd.org/Main_Page").  After you've copied it over and edited your menu.lst and fstab files to reflect the new location, write grub to the mbr of the usb drive and boot to that.

I have a usb drive and hdparm -tT /dev/sda indicates and average read speed of ~35 MB/s (vs. 54 MB/s on my internal ata133 drive).  ButI don't really notice the difference in everyday use.

---

