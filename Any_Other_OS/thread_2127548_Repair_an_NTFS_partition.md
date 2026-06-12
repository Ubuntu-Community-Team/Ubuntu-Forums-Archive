---
title: "Repair an NTFS partition"
date: 2013-03-20
forum: Any Other OS
---

### Post by Glutamico on 2013-03-20
Hello everyone,

I have been using ubuntu for a month now, and I'm getting used to it, it's really cool. Actually I wanted at the beggining just to try it, but since I messed up with my partitions, I decided to install Ubuntu 12.04 on my free space.
Hopefully, testdisk helped me get back my two data partitions (NTFS) which I used when I was with Windows 7. Indeed, I haven't been able to boot back on Windows 7 since I installed ubuntu : I have to use the recovery tool, which I don't have, and all my tries to boot it from a usb key failed. Two days ago, against all expectations, the incredible testdisk found the recovery partition out of no-where (+/- 20 GB). Unfortunatly, Gparted told me the disk was corrupted : I have to run **chkdsk**.
BUT : I can't boot in windows (I need the recovery partition)
I can't have the prompt command from a bootable usb (I haven't find an iso file that suits my PC).

So here's my question :
Is there any way to repair this ntfs partition (which is apparently broken) from ubuntu ? That would be nice. I've began projects with W7 and I miss one or two editing softwares. 
By the way, will it bring back the Windows Recovery Environment for sure?

(Sorry if I've made mistakes, I'm not English)
(Sorry if I posted in the wrong session : I thought "hardware" would fit the most, since it has to do with the hard drive)
(Sorry if the question has already been answered : I look in a lot of forums though)

(Thanks for any time you could give me to answer my question :))
Have a nice day !

---

### Post by oldfred on 2013-03-20
Moved to other OS since Windows issues.

There is no way to run chkdsk from Linux. You can make a few minor fixes, but it primarily turns on the chkdsk flag so when you reboot.

If you know someone with the same 32 bit or 64 bit Windows.
       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Glutamico on 2013-03-20
Ok, well i'll try once again to burn one of the iso files you linked !
One last question though : what is SP1 ? Should I take the files with or without ?

Thanks for your answer !

---

