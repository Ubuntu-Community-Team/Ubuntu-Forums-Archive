---
title: "Booting from CD."
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by SirD on 2006-01-07
Hello all! I was wondering if anyone here knows how to boot from a CD? I decided I wanted to get Ubuntu. I am currently running Windows and I wanted to know how to be able to put in a cd and then the cd would tell the computer to boot from Ubuntu. (Not a live cd or installing). I also wanted to know where to put all the files of Ubuntu once I have downloaded them.

Thanks.

-Ryan

---

### Post by truthfatal on 2006-01-07
Do you mean making a boot disk out of a CD-R(W)?

[http://ubuntuforums.org/showthread.php?t=19428](http://ubuntuforums.org/showthread.php?t=19428)

---

### Post by SirD on 2006-01-07
Yes but I don't understand that article. I am currently running Windows XP SP2.  Where do I put the linux operating system at on my hard drive? And I don't get what folders he is talking about.

-Ryan

---

### Post by racin on 2006-01-07
Check out these instructions. This will allow you to add Ubuntu but still have windows xp on your computer. After installation during the bootup it will ask which OS you want to boot from. Here is a link [http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/]("http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/")

---

### Post by aysiu on 2006-01-07
Just booting from the CD?

It's in the BIOS settings before Windows even loads up. You have to press a key (usually F2, Delete, or Escape) to get into the settings. In the settings, you can select the boot order--select to boot from the CD-ROM before the hard drive.

If you want to dual boot, I highly recommend the fifth link in my sig over the one racin recommended (no offense, racin).

---

### Post by Mission 10 on 2006-01-07
Well the only options you have to use Ubuntu is either the live CD or installing. What I think you are looking for is the ability to use Ubuntu but not have it on your hard drive and still be able to save files and settings the the hard drive. The only way I know how to do that is to have your hard drive formated to Fat32, because Linux by default cannot write to NTFS only read, (without some advanced knowledge). 

Dual booting both Windows and Ubuntu is the best option. With proper instructions you can easily partition a small amount of your hard disk to try out ubuntu, (5gb is what I used) and upon loading you'll have the choice to use either Windows or Ubuntu. The links above will help the install process.

---

### Post by SirD on 2006-01-07
I want Ubuntu on my hard drive. But when the computer starts I want BIOS to first check if there is a CD in if there is the CD tells it to boot up Ubuntu, or however it would. Else boot up Windows. Unless people put the certain CD in I want it to boot up in Windows without any one knowing that there was another OS.

-Ryan

---

### Post by Mission 10 on 2006-01-07
Well the bootloader gives you the option between the two os's every time the computer is started. To have your boot order check the cd-rom first you must go into your bios and edit that. But if you're looking to disguise that Ubuntu is loaded unless a cd is present to start it's boot process then you'll have to compile your own instruction on that cd to start Ubuntu. And that's far beyond my knowedge.

---

### Post by aysiu on 2006-01-07
You can install Ubuntu as a dual boot with Windows.
There will be a menu at bootup that allows you to choose Windows or Ubuntu.
If you make Windows the default and set the timeout to five seconds, no one will know the difference.
You can then choose Ubuntu yourself if you're fast enough.

Setting the BIOS to boot from CD is just so you can actually get Ubuntu installed in the first place.

---

### Post by SirD on 2006-01-07
Some one told me the CD tells what OS to use and if there is no CD to automatical use Windows XP. Is there no way to do that?

-Ryan

---

### Post by racecat on 2006-01-07
It strikes me that I saw something like this a while back. Maybe writing grub to a floppy. I'll try to dig up the info.

Bill

---

### Post by racecat on 2006-01-07
One other option would be to put Ubuntu on a second drive, don't install grub (boot loader), and use bios to set boot priority. Just be sure to reboot and reset bios to the XP drive when finished using Ubuntu.

Bill

---

### Post by janey on 2006-01-08
i could make a new thread but i figured this was similar so i'm just replying here and hoping someone will read it :D

i borrow a copy of the live and install cds from a friend, and i want to install ubuntu. i dont want to partition or still have windows or anything like that. but i dont know how to set my computer to boot from cd.

from what i've read, i just need to hit F2 when the computer starts up, before windows starts loading. is that right? someone else told me i need to hit enter. i guess i could just hit one and then the other and hope it works. :S

help appreciated. major n00b here.

---

### Post by racecat on 2006-01-08
[QUOTE=janey]i could make a new thread but i figured this was similar so i'm just replying here and hoping someone will read it :D

i borrow a copy of the live and install cds from a friend, and i want to install ubuntu. i dont want to partition or still have windows or anything like that. but i dont know how to set my computer to boot from cd.

from what i've read, i just need to hit F2 when the computer starts up, before windows starts loading. is that right? someone else told me i need to hit enter. i guess i could just hit one and then the other and hope it works. :S

help appreciated. major n00b here.[/QUOTE]

It depends on your BIOS. On many, it's the delete key. Look for it during the bootup script. It'll say something like - "Hit delete to enter setup" or "F2 to configure". Once I know the key, I usually start tapping it about once a second from the start of reboot until I see BIOS. I assume this is to change the boot order to boot from a CD.

Good luck,
Bill

---

### Post by janey on 2006-01-08
i got into setup and tried it, but it booted up windows all the same :S. so i'm going to cold boot it and try again.

here's hoping i reply to this thread with success :)

thanks

---

### Post by BobSongs on 2006-01-08
[QUOTE=SirD]Some one told me the CD tells what OS to use and if there is no CD to automatical use Windows XP. Is there no way to do that?

-Ryan[/QUOTE]Depends on the CD. Usually a well written CD's boot will say something like: "Boot to CD/Boot to hard drive". You'll see that on some CDs like Symantec's (Norton) Antivirus or Norton Utilities.

If you've got enough memory (RAM) then download the Ubuntu "Live CD" .iso file, burn it to CD and test it for a bit. If you're determined to install Ubuntu side by side with Windows XP, download the Ubuntu "Install" CD and Ubuntu gives you the option to either wipe the current hard drive or (the option you want) to install it in the largest free space available.

You must set your system's BIOS to boot from CD ROM as primary boot source with the option to boot from the Hard Disk Drive (HDD) as secondary. Follow your manufacturer's instructions on that.

Hope this helps. Let us know if there's anything else with which we can help you.

---

### Post by janey on 2006-01-08
now i'm offtopic, but oh well. starting new threads is scary.

i installed ubuntu, and it said it was all done, and to take out the disk and the computer would restart. but when it was loading, it said something like "boot error, insert system disk". so i put the cd back in, and now it wants to install it all again. 

help?! it says if i exit the installation it may be in an unstable condition. i dont want that!

---

### Post by SirD on 2006-01-08
I bought the computer from Dell. I don't know what BIOS I have. How do I find out?. I've neem downloading Ubuntu all night but it's still not done, I think it had an error in the downloading. . . And Ubuntu live is copying from my server where I uploaded it via SSH. And that should take about 7 more hours. I also don't know what contents to burn for the CD?

Thanks for all your help.

-Ryan

---

