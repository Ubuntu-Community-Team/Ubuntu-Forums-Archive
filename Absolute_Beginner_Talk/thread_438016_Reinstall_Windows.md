---
title: "Reinstall Windows"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Literatka on 2007-05-09
:confused: Yeah I don't want to do it, but my printer or scanner won't work on ubuntu and I've got no other option at the moment. So I'm using my cd from Toshiba and after I run it and assume it's finished, I get the error... Loading... GRUB error 71

How can I fix this?

---

### Post by Cypher on 2007-05-09
A quick google serach will yield you answers. Try [this]("http://www.chrisburgess.com.au/reinstalling-or-repairing-the-windows-xp-bootloader/").

---

### Post by Literatka on 2007-05-09
Yeah that didn't work. Windows doesn't even load. GRUB is stuck on my computer, meaning that it's not off my HD but I don't know how else to get it off.

---

### Post by eddieb on 2007-05-09
If you reinstall Windows you will lose Linux. Windows will only install on the first partition( it MUST be C:) Insert your Windows disc and reboot , if the Windows install page comes up then just follow the screen prompts. If not , you will have to go into the Bios and make the 1st boot drive read cdrom. Remember to save and exit.

---

### Post by Terl on 2007-05-09
Is the cd from Toshiba an actual windows disk or just an image?  Did you get to the xp installation when you boot from the Toshiba cd?  The commands at that link should fix your MBR.

---

### Post by DNSBubba on 2007-05-09
The problem is that your MBR (Master Boot Record) is still allowing GRUB to try to load Linux, which no longer exists. You will need to reformat your MBR. 

The easiest way to do that is to use a Windows disk to boot from, then select the option to Repair an installation.

Once your at a command prompt, type the following (no quotes) - "fixmbr" .

This will reformat your MBR to "see" Windows.

Once done, type "exit" and Windows should boot.

---

### Post by umarvlie on 2007-05-09
ALternatively use another boot CD or Floppy of a previous window version and use FDISK /MBR which would also do the trick.

But going back to the start, some basic questions:
1/ did you even have a Windows partition on your disk?
2/ did you have multi boot? 
3/ is the Toshiba CD a reall windows (XP?) installation CD or just a recovery CD?

---

### Post by Literatka on 2007-05-09
> **umarvlie said:**
> ALternatively use another boot CD or Floppy of a previous window version and use FDISK /MBR which would also do the trick.

But going back to the start, some basic questions:
1/ did you even have a Windows partition on your disk? [COLOR="magenta"]No.[/COLOR] 
2/ did you have multi boot? [COLOR="magenta"]No.[/COLOR]
3/ is the Toshiba CD a reall windows (XP?) installation CD or just a recovery CD?

[COLOR="Magenta"]No, it's just a recovery CD, which is all that I have. [/COLOR]

---

### Post by Terl on 2007-05-09
Okay...couple of ideas.  The recovery cd won't do the job most likely.  Here is a link from Microsoft that might help:  [Create XP Setup discs]("http://support.microsoft.com/?kbid=310994").  If that does not work search over here at [BootDisk.com]("http://www.bootdisk.com/bootdisk.htm") for a solution.  You need one that will run fixmbr although you could also use a 98 disk and run fdisk /mbr.  I would check the M$ site first as they are the source.

---

### Post by umarvlie on 2007-05-10
> **Literatka said:**
> [COLOR="Magenta"]No, it's just a recovery CD, which is all that I have. [/COLOR]

If it is only a recovery CD and you had used the entire disk for Ubuntu, the small (proll. FAT32 or FAT16) partition where the restore files were on was deleted and used for Ubuntu as well. So unless you buy/borrow a new Windows CD you can't reinstall it.

Or go back to Ubuntu and see if your problem can be fixed another way :)

---

### Post by pissedoffdude on 2007-05-10
> **Literatka said:**
> [COLOR="Magenta"]No, it's just a recovery CD, which is all that I have. [/COLOR]

Do you have any blank cd's lying around. You might want to give super grub disk a try.  It can reinstall the window bootloader to the mbr. [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by Ateo on 2007-05-10
Download a bootdisk: [http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

Boot to it. Then do (from the C prompt) ```
fdisk /mbr
```

---

### Post by aquavitae on 2007-05-10
The original problem was a scanner and printer not working in Ubuntu - How about trying to fix that instead, it might be easier than installing window.  If you can't find any linux drivers (although I've seldom had problems there!) you could probably get it working through wine.  [www.linuxprinting.org]("http://www.linuxprinting.org") has a good list of printers that work in linux, along with recommended drivers.

---

