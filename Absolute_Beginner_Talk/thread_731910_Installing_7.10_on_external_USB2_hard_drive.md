---
title: "Installing 7.10 on external USB2 hard drive"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by doug97tj on 2008-03-22
Current hardware:

Processor: AMD Athlon 64x2 Dual Core 4800+ 2.5 GHz
4 gb USB2 thumb drive
CD/DVD burner
160 gb USB2 external hard drive
120 gb internal hard drive
OS: Windows Vista Ultimate - 32 bit

HP allows me to choose location for boot from computer's hard drive,
the thumb drive, the external hard drive or a CD. It's not quite a
boot manager. It's simply an assignment of boot priority, I think.


Plan/Goal:

1) Ubuntu OS and all linux programs installed on external 160 gb USB drive
2) Activity on internal hard drive restricted to Vista with possible exceptions of 
data files from Thunderbird, Firefox and OpenOffice.

I would like to use the above programs - Thunderbird etc. - in both
OS's and have the data files fully complete and up to date regardless
of the OS in use.

Questions:

1) Reasonable/doable??? I don't look at this technically as a "dual
boot" situation although my understanding of dual boot may be
inadequate. Instead I see it as a single machine booted into Vista by
choosing the internal hard drive as the initial boot device or
strictly a Ubuntu machine if the external USB hard drive is chosen as
the initial boot device.

2) Can I put the data files and possibly the individual program's
setup files in a single place and have the program - Thunderbird etc.
- read and update those files from BOTH operating systems?

3) If (2) is doable, should the data files be on the Vista hard drive
or the Ubuntu hard drive? Currently the external USB hard drive is not plugged
in. Since Vista recognizes it as one of its resources when it is
plugged in, my plan would be to only plug it in prior to booting to
Ubuntu. If the email, browser and office programs stored data on the
USB drive, that would require the drive to be active during Vista use
and thereby allow Vista to use the drive for other activity as well.
That I do not want.

4) If Ubuntu is installed as a 64 bit OS, would that have any effect
on on the two OS's using the same data files for Thunderbird etc.?
Vista is 32 bit.

5) Ubuntu is being delivered to me as a live CD. Hasn't arrived yet.
How do I get those files onto the USB drive from the CD? Simple
copy/paste or does the drive have to be configured for Ubuntu? or
install Ubuntu onto the USB drive. If it is an  installation process,
would that put any part of Ubuntu on the internal hard drive?

I'm assuming I can boot from an Ubuntu 7.10 CD - live or install CD - and 
establish the external USB drive as the repository for Ubuntu and
install 7.10 totally to that drive.

Comments and suggestions will be most appreciated.

Doug C.
Houston, Tex.

---

### Post by metalf8801 on 2008-03-22
make sure to disconnect you internal hard drive when you install Ubuntu onto the external or it will over wright the mbr and you wont be able to boot into windows unless the eternal hard drive is plug in.  This is just an issue i ran into once

---

### Post by backflip on 2008-03-22
My set-up on my laptop is just about what you want. I disconnected the internal HD, changed the boot order in the BIOS to boot first from CD. I had my external hd mainly  partitioned as 'free space' but also  made a couple of ntfs partitions for data and backups. I booted  the livecd and unchecked the three checked options on the first tab of systems/preferences/removeable drives and storeage. Then  installed linux  manually on the free space, making three partitions (root, home and swap). That done I rebooted and again changed the BIOS to boot first from USB, then hd, and reconnected the internal hd. Now when I boot, if I switch on the USB external drive it boots there, but if I don't have it on it boots into Windows on the internal drive. The two ntfs partitions I use for sharing data between the two drives.
It all works well for me and I don't have the hassle or worry of a dual boot or grub going wrong.
I do however dual boot (vista/ubuntu) on my desktop and have never had any problems.

---

### Post by NR1224 on 2008-03-22
if i remember correctly from my install, there is an option to use a second slave hard drive just as u described

---

### Post by doug97tj on 2008-03-22
> **metalf8801 said:**
> make sure to disconnect you internal hard drive when you install Ubuntu onto the external or it will over wright the mbr and you wont be able to boot into windows unless the eternal hard drive is plug in.  This is just an issue i ran into once

-----------------------------------------------------------

Thanks, but this brings up another question.  

If the live CD boots, runs and doesn't change any configurations on the hard drive, why couldn't the live CD system be transferred to the external USB hard drive and be booted from there instead of the CD?  Is the live CD different in some significant way so that it is in fact a "lite" version thus limiting the entire computer's resources in some manner?

I don't mind unplugging the internal HD for the initial install, but if the live CD version will work if transferred to the USB drive, that would seem to be easier and faster.

Another question:  I have plenty of ram and a fast dual core 64 bit CPU.  Any problem with running Ubuntu 64 while the internal hard drive is Vista 32?  Would that prevent both OSs from accessing the same data files for Firefox, Thunderbird and OpenOffice if those files were on the internal Vista drive?

Doug C.

---

### Post by toMeloos on 2008-03-22
I'm actually doing this!

I use the laptop I have been issued by my employer to run Ubuntu from an external 2,5" usb2 hard drive for personal use. It works great. At first I was afraid that usb would make my system slow but it doesn't seem to be any slower than Windows on the internal drive with regard to disk operations.

Some remarks:
[LIST]
[*]You can easily share your windows documents by using ntfs-3g. It's safe. Just make sure you use normal shutdown in Windows. Hibernating Windows causes it to lock the hard drive (because the memory image is written to it for recovery) which means you can't access it from linux (not even using ntfs-3g).
[*]Do not use hibernate features in linux because they will shut down your USB support, hence your system cannot wake up again. These kind of power saving features do not seem to be designed for running the OS on external equipment.
[*]If you wish to share files (thunderbird mail box, firefox bookmarks, etc.) use the ones on the Windows drive. Otherwise you allways need to connect the external drive to be able to use Windows and have to create a NTFS partition on your usb drive. I don't share any program files (just "my documents") so I can't tell you if this works without data corruption!
[*]You CAN install ubuntu on the external disk 3 ways:
[INDENT]- physically disconnect your internal hard disk first[/INDENT]
[INDENT]- disabling your internal drive in the BIOS[/INDENT]
[INDENT]- if these are not options: 1) do a regular install of Ubuntu on your external HD. this will overwrite the Master Boot Record on the internal drive so Windows won't boot anymore, 2) boot the Windows installation CD and run the repair program. This will overwrite the MBR with the Windows boot loader again. 3) boot ubuntu from the external drive. GRUB will probably refuse to load linux because it will mess up the disk numbers. in that case edit the boot parameters. It will probably try to boot from hd1 or sd1 because during installation it considered the internal disk as being primary (thus hd0) and the external disk as secondary (thus hd1). So, turning these numbers around will allow you to boot. After logging in, make sure you do the same trick to the /boot/grub/menu.lst file so you won't have to do this any more.[/INDENT]
[*]If your computer does not allow you to boot from USB, you can try using the Windows bootloader to boot the external drive. Check [this page]("http://www.thinkwiki.org/wiki/How_to_setup_boot_loaders") for instructions.
[*]To be safe I've set swap usage to a minimal. There is such a settings file somewhere. Search this forum and you'll find the instructions!
[/LIST]

Good luck. If you have any more questions, let me know.

---

### Post by doug97tj on 2008-03-22
> **backflip said:**
> My set-up on my laptop is just about what you want. I disconnected the internal HD, changed the boot order in the BIOS to boot first from CD. I had my external hd mainly  partitioned as 'free space' but also  made a couple of ntfs partitions for data and backups. I booted  the livecd and unchecked the three checked options on the first tab of systems/preferences/removeable drives and storeage. Then  installed linux  manually on the free space, making three partitions (root, home and swap). That done I rebooted and again changed the BIOS to boot first from USB, then hd, and reconnected the internal hd. Now when I boot, if I switch on the USB external drive it boots there, but if I don't have it on it boots into Windows on the internal drive. The two ntfs partitions I use for sharing data between the two drives.
It all works well for me and I don't have the hassle or worry of a dual boot or grub going wrong.
I do however dual boot (vista/ubuntu) on my desktop and have never had any problems.

-----------------------------------------------------------------

This sounds reasonable and barring any info to the contrary will probably be my install choice.

I would truly like to get away from MS, but there is a problem. the enormous amount of money I have invested in MS software with some being Vista specific.  I want to maintain that degree of computer usability.

Besides wanting to get away from MS I have a large  computer controlled (CNC) commercial milling machine.  The controller has a small flash drive loaded with a VERY limited version of Linux and a CAM program (Computer Aided Machining) that runs the entire system.   It has little room to spare on the drive.  The system will, however, recognize and run a USB flash drive in addition to the internal flash drive.

The external USB drive is used to store parts programs designed using the CAM system on the machine.  It is also used to transfer files particularly .dxf files via a USB thumb drive from my office Vista machine as well as .dxf files submitted to me by customers.  .dxf files are files created using various CAD programs.  My milling machine program will convert .dxf files into programs/files (CAM files) that will direct the machine to create the parts designed using outside CAD programs.  Obviously there is compatability between files created with multiple OSs and the Linux system on the milling machine.

If I can get Ubunta up and running on my office computer, I can load a Linux .pdf reader on the thumb drive and transfer it to the milling machine along with a .pdf version of the milling machine's operator manual.  This will be most helpful in the shop.  I could also create and transfer other .pdf files relating to machining data, metal properties, drill, tapping and threading charts, feeds & speeds for various metal cutting etc.  Possibilities are endless.  

With all this data available and transferred to the milling machine I would install a second USB hard drive in the controller and simply use the thumb drive to transfer between the office computer and the milling machine.  

Linux is multi tasking.  The milling machine is also multi tasking in that the Linux system and the CAM program will control the machine, make parts and all the while allow me to create additional parts programs at the same time.  It will even allow me to modify the program being used to create a particular part while that part is actually being created.  It's a pretty serious and versatile system.  All the possibilities of increased file storage and usage will only improve it.

Doug C.

---

