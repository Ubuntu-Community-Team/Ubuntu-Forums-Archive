---
title: "Error 21 and resulting problems(s)"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by Maxxnme on 2007-11-30
Hi!  I recently d/l'ed a copy of Ubuntu 7.10. I thought I had d/l'ed it to an external drive-apparently not!
So, I had a dual boot with Windows XP Media Edition.
A few days ago, I was playing a game (on WinXP) and it froze up, so I shut off the pc. Upon coming back on, I got the Grub Loading....stage 1.5. and eventually ERROR 21.

So, I tried to reboot and, in the hopes of getting back into Windows however, I get NO boot screen: I can not even get into the 'last best configuration' screen when I hit the TAB nor can I get into BIOS. I can't get into WINDOWS at all!
I can get into the 'drive screen' and since I have no floppy, I hit the CD option with the WIN XP recovery disk in it. No good! It Does a repair/recovery but still can not boot up. [I] still get the Error 21 message.
I would hate to think I need to reinstall WINDOWS via the recovery disk and set up the backup option. Any help greatly appreciated.
Maxxnme

---

### Post by louieb on 2007-11-30
The GRUB pointer is in the MBR of your hard drive. The Grub program (stage2) is in your Ubuntu install. Which I guess is on the external. Is the external plugged in? 
To get it to boot windows without the external plugged in you need to run fixmbr from the recovery console of the XP install CD. or there are few other ways to it.
Look at the prepare MBR here: [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by Maxxnme on 2007-11-30
Hi Louieb and thank you for your response. Very kind of you. Okay:
The external drive is NOT plugged in at this time (not sure of the drive letter anyway-and since I get the black screen, I have no way right now of knowing what the drive letter is).
I entered the fixmbr command on the recovery console and what came up, scared the pants off me:
This is what it said:
This computer appears to have a non-standard or invalid master boot record. FIXMBR may damage your partition tables if you proceed. This could cause all the partitions on the current hard disk to become inaccessible. Are you sure you want to write a new MBR?

Frankly,Louieb, I'm scared to death. What do you suggest? I'm not entering anything until I hear back.
Again, many thanks.
Maxxnme

---

### Post by Maxxnme on 2007-11-30
Hey Louieb!!!!  As George Constanza might yell:'I'm back in business bay....I'm baaaack!'
Thank you for asking me as to whether the external drive was still plugged in or not. I did plug it back in but the crazy thing is, the system started going nuts BEFORE I unplugged it. Since it's the same OS (and the recovery CD is the same on both pc's at home, I noticed that the boot screen on the working model indicated: Press F11 for Recovery.
So I did...and it gave me my boot options-all functioning.
Thank you, thank you, thank you!
~Maxxnme:redface:

---

### Post by louieb on 2007-12-01
> **Maxxnme said:**
> ... This computer appears to have a non-standard or invalid master boot record. FIXMBR may damage your partition tables if you proceed. This could cause all the partitions on the current hard disk to become inaccessible. Are you sure you want to write a new MBR?...

Thats the standard scary message everybody gets - Just because GRUB is in the MBR.  

Can't tell if you got your MBR restored to the pre Ubuntu install state. Not sure what F11 does on your PC. I guess you found out that  the external needs to be plugged in when you reboot.  

Glad you got it back up and running. .

---

