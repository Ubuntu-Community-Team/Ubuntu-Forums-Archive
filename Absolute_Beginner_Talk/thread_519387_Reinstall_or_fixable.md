---
title: "Reinstall or fixable?"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by SBG on 2007-08-07
Greetings,

I've been asked by a friend to remedy a bad situation.

She's managed to hose up her Ubuntu install somehow; the xGUI wont load and to make matters worse she seems to have lost track of the root password.

Should I nuke the Ubuntu partition and start over or is there a way to salvage the install?  What are the consequences of a reinstall on the bootloader?


Background information:

- This is a new install, done on top of a dual boot system with both XP and Vista.  GRUB is handling bootloading with no problems; she can pick any OS she wants.  Order of install: XP first on HD0, Vista next on HD1, Ubuntu last on HD0.  

- The system is a homegrown "Frankenstein."  Full details are available if needed. 

- This problem occurred the first time she tried to boot to Ubuntu.  No one has logged in successfully yet.

- Version: Ubuntu 7.04 i386 from a downloaded ISO.  The ISO looks good from what I can see, and the optical drive seems fine.

- Video card: nVidia 7800 GTX.

- Level of experience: She's mid-level Windows, noob *nix.  Me: Somewhat advanced Windows admin (server admin in data center), basic *nix.


TIA,

SBG

---

### Post by SBG on 2007-08-07
One thing I forgot to add: Each OS has its own partiton.  HD0 has three, one with XP one for Ubuntu, and one for data.  HD1 has three, one for Vista, two for data and storage.

---

### Post by sysikon on 2007-08-07
Could you give the full details?

---

### Post by Inxsible on 2007-08-07
if she has forgotten her root password, there is hardly anything anyone can do. A re-install would be the only solution.

---

### Post by sysikon on 2007-08-07
I agree, if she can remember the password, mess with the X configuration, that would be my first guess.

---

### Post by SBG on 2007-08-07
Sure thing:

Short Version:

- MB: Asus P5N32-SLI Premium/WiFi-AP
- RAM: 2 Gigs Corsair
- Video: 7800 GTX
- HDs: HD0 160 Gig Seagate (I think it's Seagate, not sure) SATA1, 750 Seagate SATA2
- Intel Q660 quadcore


Longer version:

System Information report written at: 08/06/07 22:29:08
System Name: VISTA
[System Summary]

Item	Value	
OS Name	Microsoft® Windows Vista&#8482; Ultimate	
Version	6.0.6000 Build 6000	
Other OS Description 	Not Available	
OS Manufacturer	Microsoft Corporation	
System Name	VISTA	
System Manufacturer	System manufacturer	
System Model	System Product Name	
System Type	X86-based PC	
Processor	Intel(R) Core(TM)2 Quad CPU           @ 2.40GHz, 2400 Mhz, 4 Core(s), 4 Logical Processor(s)	
BIOS Version/Date	Phoenix Technologies, LTD ASUS P5N32-SLI PREMIUM ACPI BIOS Revision 0802, 3/5/2007	
SMBIOS Version	2.4	
Windows Directory	D:\Windows	
System Directory	D:\Windows\system32	
Boot Device	\Device\HarddiskVolume1	
Locale	United States	
Hardware Abstraction Layer	Version = "6.0.6000.16386"	
User Name	Vista\Me	
Time Zone	Central Daylight Time	
Total Physical Memory	2,045.94 MB	
Available Physical Memory	1.33 GB	
Total Virtual Memory	8.12 GB	
Available Virtual Memory	7.35 GB	
Page File Space	6.20 GB	
Page File	D:\pagefile.sys

---

### Post by SBG on 2007-08-07
> **Inxsible said:**
> if she has forgotten her root password, there is hardly anything anyone can do. A re-install would be the only solution.


Root password seems to be a goner.  Can I just boot from the ISO and reinstall to the same partition, or do I need to reformat it first?  What happens to GRUB if I do that?


SBG

---

### Post by az on 2007-08-07
> **Inxsible said:**
> if she has forgotten her root password, there is hardly anything anyone can do. A re-install would be the only solution.

There is no root password.  Boot into recovery mode and you are dropped into a root shell.  Run

passwd
and change the password.

> **sysikon said:**
> I agree, if she can remember the password, mess with the X configuration, that would be my first guess.

While you are there (recovery mode), run

dpkg-reconfigure -plow xserver-xorg

and pick the vesa driver for the video card.  Pick the default for everything else.

once you are back at the prompt, run

init 2 

to get into graphical mode.  Try the nv driver if that doesn't work.

---

### Post by sysikon on 2007-08-07
Umm...You should be able to boot the ISO and install it to the same partition. It should redo the partition, formatting and everything.

---

### Post by Inxsible on 2007-08-07
az is right. I had forgotten about the ability to change the password in the recovery mode. Try that first. It might save you a lot of grief !

:)

---

### Post by meierfra on 2007-08-07
Never mind. I was to slow.

---

### Post by SBG on 2007-08-08
I followed the steps that az put up.  Either they need a little tweaking or its just my newness with this OS showing, but either way it looks like it worked since I have GNOME running.

Thanks a ton for all the quick replies last night!


SBG

---

