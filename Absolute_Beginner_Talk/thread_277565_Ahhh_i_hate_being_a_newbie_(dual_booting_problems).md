---
title: "Ahhh i hate being a newbie (dual booting problems)"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by sunami88 on 2006-10-14
_Incoming wall of text._

Well, here we go i guess. I HAD the Windows Vista RC1 installed on a second partition i created along side my Windows XP partition. Long story short, i got sick of Vista and wanted to try out linux again seeing as how i havent tinkered with linux since like Fedora Core 2....

_Ugh, what a pain._

I was thinking i could just install Ubuntu over my Vista partition, overwrite the Vista bootloader etc, and just dual-boot with GRUB.

_Again, wrong :P._

First problem was, during install, X died. But when i hit enter the CD ejected and the computer rebooted up to the GRUB bootloader, good it was working. Well after trying for a little while to get X started, i was going to go back to XP and search some topics to try and fix this.

_My computer hates me._

After clicking on the "Windows XP Home Edition" (or some such jargon) from GRUB, i was presented with the Vista Bootloader screen. "Well thats not good", i muttered to myself. I clicked on "Previous Version of Windows" knowing that trying to boot to Vista would result in an error.

_BSOD._

After hitting enter on "Previous version...", XP seemed to be booting normally with the little moving bar thingy and the Windows XP logo. about a milisecond after, i got a BSOD.

_Recovery Mode._

After knowing i fudged something bad, i put in my XP Recovery Disk and went to Recovery Console. Through some trial and error, i got rid of GRUB, got rid of the Vista Bootloader, and things seemed to be going good. But again, i get the BSOD.

_As of now..._

Well as of right now, i can go into Safe Mode (it used to hang before i got rid of the Vista BL). I have tried using restore points etc, but to no avail...

Does anybody have any suggestions? My XP partition is all still there, i formatted the partition that used to have Ubuntu to NTFS just to be sure XP wasnt blowing chunks at the sight of EXT3. I'm starting to think this has nothing to do with Linux at all, but still, any uber-nerds out there willing to come to the aid of a newbie?

---

### Post by David_T on 2006-10-14
If you can boot into Safe Mode but can't boot into windows normally, try going to Start>Run and type msconfig, then turn off all non-ms services and all startup items.  Then maybe you can find the process that's causing the problem through trial-and-error. good luck

---

### Post by Sef on 2006-10-14
VISTA does not play nice with Linux.  Trying searching the threads here and see if you can find an answer to your problem.

---

### Post by sunami88 on 2006-10-14
> **David_T said:**
> If you can boot into Safe Mode but can't boot into windows normally, try going to Start>Run and type msconfig, then turn off all non-ms services and all startup items.  Then maybe you can find the process that's causing the problem through trial-and-error. good luck

Thats a very good idea, and i hadnt thought of that. However, it doesnt seem to be working.... i've disabled pretty well everything and im still getting a BSOD, any other ideas?

[quote=Sef]VISTA does not play nice with Linux. Trying searching the threads[/quote]

I don't have Vista anymore, i'm trying to get XP working after... well... SOMETHING happened....

---

### Post by sunami88 on 2006-10-14
Alrighty, i seem to have fixed her. Had something to do with Video Drivers in Device Manager, nothing at all to do with linux...

Thank you for your help.

---

