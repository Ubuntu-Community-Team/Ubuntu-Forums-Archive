---
title: "Boot floppy"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by darkborg on 2006-01-24
Hi All,

I´m new to Ubuntu and have several questions related to this, I´m trying to install this on a very old laptop that won´t allow me to boot from the cd...I even tried bootmanager so seems like I used pretty much all the resources, bios updated won´t help since there is not...now if you are old enough like me and had the terrible experience of installing winslow 98, you´ll remember that it came with a floppy and you loaded the floppy and then access the cd and start it from there...
Please tell me that there is a boot floppy for Ubuntu and we can copy the same procedure..

---

### Post by lha on 2006-01-24
[QUOTE=darkborg]Hi All,

I´m new to Ubuntu and have several questions related to this, I´m trying to install this on a very old laptop that won´t allow me to boot from the cd...I even tried bootmanager so seems like I used pretty much all the resources, bios updated won´t help since there is not...now if you are old enough like me and had the terrible experience of installing winslow 98, you´ll remember that it came with a floppy and you loaded the floppy and then access the cd and start it from there...
Please tell me that there is a boot floppy for Ubuntu and we can copy the same procedure..[/QUOTE]

Do you mean Smart BootManager with bootmanager? If not, try it. It's on Ubuntu install cd, /install/sbm.bin. You'll need rawwrite to make a boot floppy out of it if you have Windows.

If you have (fast) internet connection, you can start netinstall from hd.

First, you'll need two files, [linux]("http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/linux") and [initrd.gz]("http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/initrd.gz"). Those files are on Ubuntu install cd, too. Look into install/netboot/ubuntu-installer/i386. Put those files somewhere on your hard drive.

Then you want to get [linload]("http://elserv.ffm.fgan.de/~lermen/"). [The file you need]("ftp://elserv.ffm.fgan.de/pub/linux/loadlin-1.6/update-1.6c/loadlin.exe.gz") is compressed, so you'll have to extract it. Put loadlin.exe to the same directory you have the two files we fetched earlier.

Last but not least, breezy.bat. Open notepad and paste the following lines in it.
```
smartdrv /C
loadlin.exe linux vga=normal initrd=initrd.gz ramdisk_size=16384 root=/dev/rd/0 rw --
```
Save the file as breezy.bat in the same directory as used above.

Now we're ready to start installation. Restart your computer and press F8 during boot up sequence to get into the menu that allows you to boot into command line. (Restart to MS-DOS mode from Start Menu didn't work for me.) Cd to the folder where you put the four files, type breezy and hit enter.

If you don't have 'net or you're on modem, you could try replacing files linux and initrd.gz with those found under /install on cd.

PS. Sorry if I'm wrongly assuming you have Win on your laptop.

---

### Post by darkborg on 2006-01-24
Hi Lha,

Thanks much for getting back to me, I´m afraid that I´m using the horrible xp and when I try to use loadlin it gives me the error that loadling only can run under real dos....not xp emulated dos....my bad I did not provided all the info...

---

### Post by lha on 2006-01-25
[QUOTE=darkborg]Hi Lha,

Thanks much for getting back to me, I´m afraid that I´m using the horrible xp and when I try to use loadlin it gives me the error that loadling only can run under real dos....not xp emulated dos....my bad I did not provided all the info...[/QUOTE]

Try it with a [FreeDos]("http://www.freedos.org/") boot disk or use these [installation disks.]("http://ubuntuforums.org/showthread.php?t=75372")

---

### Post by Red_Kite on 2006-01-25
Thanks this works a treat didnt realise that it was available on teh CD.

Just got 2 old Toshibas that cant boot from CD to start the install from CD.
Will get and install on these now.
Thanks for the help

---

