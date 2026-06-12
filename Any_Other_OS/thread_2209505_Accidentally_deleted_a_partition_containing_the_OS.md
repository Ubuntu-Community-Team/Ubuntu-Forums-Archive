---
title: "Accidentally deleted a partition containing the OS..."
date: 2014-03-06
forum: Any Other OS
---

### Post by kris10 on 2014-03-06
I am assuming I couldn't be the first one to do this, but by accident I deleted the wrong partition and am stuck turning my laptop on only to start GRUB and possibly go into rescue mode... which does nothing it seems. Then again I am new to this and should not have been messing with it in the first place. How can I go back to windows 7?

Looking at previous posts about this already I will note some things...
1) I used the full hdd
2) I did not have a recovery disk beforehand as I didn't care for anything on the laptop (wasnt thinking about the OS though)
                - Downloaded windows 7 and created a disc though just in case
3) followed a thread [http://ubuntuforums.org/showthread.php?t=2070707&highlight=accidentally+deleted+partition+OS](http://ubuntuforums.org/showthread.php?t=2070707&highlight=accidentally+deleted+partition+OS)... to fix bootloader and to get out of GRUB 
                " - [COLOR=#333333][FONT=UbuntuMono]bootrec.exe /fixboot[/FONT][/COLOR]
bootrec.exe /fixmbr
[LIST]
[*=left]Now close the two windows and click "Restart." Take out your Windows DVD and hopefully, you will be left with your Windows bootloader."
[/LIST]
[LEFT][FONT=inherit]That worked but I restarted it and it almost went into a dual boot like state where I could pick between debian and windows 7. I choose windows 7 went to the disk I made which shows 0MB partitioned (there is 3 gigs worth of stuff on that CD I don't get it?) Clicked continue anyway just to see what would happen. went into startup repair and it said "Startup repair cannot repair this computer automatically" 

Problem Signature:
Problem Event Name: StartupRepairOffline
Problem Signature 01: 6.1.7600.16385
Problem Signature 02: 6.1.7600.16385
Problem Signature 03: unknown
Problem Signature 04: -1
Problem Signature 05: ExternalMedia
Problem Signature 06: 1
Problem Signature 07: CorruptBootConfigData
OS Version: 6.1.7600.2.0.0.256.1
Locale ID: 1033

Thanks for checkin out the post![/FONT]
[FONT=inherit]
[/FONT][/LEFT]

---

### Post by oldfred on 2014-03-06
Moved to Other OS, since not Ubuntu issues.

If booting an install disk on a DVD or flash drive, you boot that from BIOS, not from a boot loader (normally).

---

### Post by mips on 2014-03-06
> **kris10 said:**
> 
Looking at previous posts about this already I will note some things...
1) I used the full hdd


You got problems then.

Your best bet is to image the drive using gnuddrescue and then to see what you can recover from the image file using tools like testdisk/photorecord etc.

If you don;t have any valuable data to recover I would say just reinstall windows.

---

