---
title: "Install or Live CD"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by mevets on 2006-04-08
I'm trying to figure out weather I need to download the Install CD or Live CD. What am attempting to do is make a dual-boot system.

Also, when installing Ubuntu do I only have to worry about installing it only a separate partition?

I know vaguely how to go about this but not quite.

Thanks.

---

### Post by muep on 2006-04-08
Hi

You need the install cd. The Breezy LiveCd is not installable.

Ubuntu needs a partition of its own. The installer can create one during install if you have some unpartitioned space available on your hard disk and it should even be able to resize some existing partitions to make space for Ubuntu.

If you are running a PC, take the i386 install image. 64-bit isn't as mature as the old 32-bit i386.

---

### Post by Stranger678 on 2006-04-08
Install CD, the Live CD is only for running the entire OS from your disc drive, which is a great way to test drive, but you wouldn't want to go primetime with it, IMO.

---

### Post by mevets on 2006-04-08
One more question.

By installing Ubuntu on a separate partition does this allow me to choose which OS to run at startup (as is the case with a dual boot system)?

---

### Post by ubuntu27 on 2006-04-08
[QUOTE=mevets]One more question.

By installing Ubuntu on a separate partition does this allow me to choose which OS to run at startup (as is the case with a dual boot system)?[/QUOTE]

Yes, when you dual boot, it allows you to choose the OS (Operating System) of your choice.


By the way, here is a good guide on how to dual boot and stuff:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)


Check it out.

---

### Post by wasp on 2006-04-08
[QUOTE=ubuntu27]Yes, when you dual boot, it allows you to choose the OS (Operating System) of your choice.


By the way, here is a good guide on how to dual boot and stuff:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)


Check it out.[/QUOTE]

I second that site. Dapper was the first time I tried Linux, and after reading through that guide, I was able to install it without any problems.

---

### Post by serlex on 2006-04-22
to create a live cd, do i need to extract the files? do i need to use Nero? thanks

---

### Post by catlett on 2006-04-22
I don't know what you mean by extract? Do you have the files compressed?(as in Zip or Rar format) You should have downloaded an uncompressed image file. You now have to burn that image to disk which Nero can do. The download is an image on your computer (an ISO file). You now need to burn that image to a disc (CD). Then put it in you hard drive and restart your computer. As long as your Bios are confuigured to boot from the cd the install will start.

---

### Post by 3rdalbum on 2006-04-23
The following can never be said enough times:

Don't just select "Data CD" in Nero and burn the .iso file like that. You must actually use the "Disc Image" setting in Nero to burn it. If you burn it and it appears in Windows with one file (the .iso) on it, you've done it incorrectly. If you burn it and it appears in Windows as having lots of files and directories on it, and the CD's name is "ubuntu_breezy_badger_i386_install" or something like that, then it's been burnt correctly.

---

