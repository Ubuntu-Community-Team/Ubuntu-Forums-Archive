---
title: "Windows NTFS problems"
date: 2011-11-23
forum: Any Other OS
---

### Post by Neonie on 2011-11-23
About 2 days ago I got an error message on my computer stating that my NTFS file was corrupted or missing. I am clearly not the first person who get this problem since there guides on google on how to fix it both with a Windows recovery disc and Ubuntu. 

I've tried to fix the problem using using Ubuntu following [this guide]("http://www.makeuseof.com/tag/fix-corrupted-windows-ntfs-filesystem-ubuntu/").

But every time I type in "sudo ntfsfix /dev/<device name>" (Device name is sda1 for me).

I get the message: "Refusing to operate on read-write mounted device /dev/sda1."

Keep in mind I'm using the newest version of Ubuntu (11.10) and this guide appears to be a bit old. I've also install lilo and attempted to fix the boot process the way it describes but every time I try to do that it just brings up the commands for Sudo Lilo.

I tried fixing it with a Windows recovery disc but kept getting a message saying something along the lines of "Windows cannot locate that file."

I have a 1tb hard drive and there's only about 400gb of data on the windows partition.

So am I doing something wrong?

If this is impossible to fix (which I really don't want to believe it is) could I possible resize my windows partition to 400gb, make a new windows partition, and then transfer the files I need from the old partition to the new partition so I don't loose data? 

Thanks in advance to anyone who can help.

---

### Post by oldfred on 2011-11-23
You need to run chkdsk from a Windows repairCD. Did you make one when windows still worked? The download that we used to recommend for one now charges $10. Or do you know someone with the same 32 or 64 bit version of Windows.
Linux tools cannot do a full chkdsk, at best they make a minor repair or two and set the chkdsk flag, so on next Windows boot chkdsk runs.

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Neonie on 2011-11-23
Got it fixed. Thanks man :)

---

### Post by LinuxFan999 on 2011-11-24
Don't forget to mark your thread as solved.

---

