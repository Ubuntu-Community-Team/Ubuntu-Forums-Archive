---
title: "Installing bios update - with a .exe?"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Tatty on 2007-03-29
Hi all,

I would describe myself as an enthusiastic noob/amateur for this...  so possibly expect some stupidity in what im trying to do...

I decided to try to set up KVM to run windows as a virtual machine on my L730 Laptop.  No joy. To cut a long story short my laptop does support the virtualisation, but there is no option for it in the BIOS.  Judging from this thread [http://ubuntuforums.org/showthread.php?t=350691&page=14](http://ubuntuforums.org/showthread.php?t=350691&page=14) it seems that i need to update my BIOS.

The bios installer turns out to be a windows executable.  >_< it seems to be some sort of cruel joke from lord gates.

1.  Is there a simple option anyone can see other than re-installing windows to install the bios update, followed by re-installing ubuntu again?

2.  Wine seems a dangerous option to me... what do you all think?

3.  Would it work if i installed windows under QEMU first, to install the bios update?  Does windows running in qemu have total control over the machine to allow that, as if it wasnt running virtually?

4. Am i right in believing that its possibly to permanently break my bios if this goes wrong?

5. Also, i am running Feisty... i think i can imagine the answer to this one, but do you think that as it is beta, its simply gonna make it even more dangerous and i shouldnt risk it?

Thanks all!

---

### Post by lahook on 2007-03-29
most bios updates you create a boot floppy from windows with the bios update on it.
then boot to the floppy and run the updater

---

### Post by milton1 on 2007-03-29
bios updates write to the flash rom, not to any spot on the disk. Assuming the .exe runs in wine, it should work. The only thing I would watch out for is if the update is a windows exe or a DOS exe. Many updates seem to need to run in DOS, so you may need to have wine emulate and older version of windows (not xp).

---

### Post by Tatty on 2007-03-29
Hey guys,

Thanks for the replies.  It gave me the info i needed to delve in deeper, and i think i now understand how it works.  I need to make a boot disk to boot to DOS, and then run the BIOS updater from there... is that right?

So does anyone know how to make a bootable-to-DOS USB stick with ubuntu?

---

### Post by annda on 2007-03-29
i don't know how to make a bootable usb stick, but here goes a cd (i assume you can burn cds if you have a computer that is able to boot from usb):

[http://linux.inet.hr/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://linux.inet.hr/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

---

### Post by kahrytan on 2007-03-29
If you don't have system files, look at the cd that came with your computer.  
Sources for Dos Disks:

Bootdisk.com
[http://freedos.sourceforge.net/](http://freedos.sourceforge.net/)

Those who have similar issues:  Asus motherboards don't need Bootdisk. Just needs the bios file on a cd. Flash Utility is builtin.

---

