---
title: "Clean Ubuntu Install"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by StGeorge on 2006-08-23
I would like to format my IBM 770x Laptop and Install Ubuntu 6.06 as a stand alone OS.
It has been FDisked into 3 Drives C, D & E.
I have downloaded and written to disc Ubuntu desktop & Ubuntu Alternate.
I have Ghosted my present OS and Software to My E drive.
I have all my IBM Drivers on my E drive.
I wish to Format my C and Install Ubuntu as a standalone OS on the C drive.
My D drive is clean and will be used for Docs Etc.
I have given some of the info about the laptop below if it will help.
All ideas and suggestions welcome.


Number Processors	1
Processor Description	Pentium(R) II, 297MHz
Total Memory	319MB
Total Hard Drive	18.6GB
Display	1024 x 768 pixels, true colour
BIOS Version	IBM
Windows 98 Second Edition (SE)
Product ID	02706-OEM-0084117-42721
Version Number	4.10
Build Number	2222
Service Pack	A
Service Pack Version	0.0
Plus! Version Number	IE 5 6.0.2800.1106

Processor Number	1
Name	Pentium(R) II
Short Name	P2
Speed [Estimated]	297MHz
Speed [Registry]	0MHz
Processor Type	OEM Primary
Manufacturer	Intel(R) Corporation
Serial Number	 
APIC Physical ID	0x00

Mouse	2 Button Mouse
Keyboard Type	IBM enhanced (101- or 102-key), 12 function keys
Display Resolution	1024 x 768 pixels, true colour
Network Installed	Yes

Adapter Name	IBM ThinkPad Fast Infrared Port

Device Type	CDROM
Device Name	 
Description	MATSHITA DVD-ROM SR-8171
Manufacturer	(Standard CD-ROM device)
Driver Provider	Microsoft
Driver Date	4-23-1999
Status Code	0
Status Message	OK

Device Type	Modem
Device Name	ThinkPad Modem
Description	ThinkPad Modem
Manufacturer	IBM
Driver Provider	IBM
Driver Date	3-23-1999

Device Type	Network adapters
Device Name	 
Description	EZ Connect USB to Dual Speed Ethernet Converter
Manufacturer	SMC
Driver Provider	SMC
Driver Date	6-21-2002

---

### Post by tkjacobsen on 2006-08-23
Just boot the ubuntu-alternative disc. Follow the instructions. Choose manual partitioning with /dev/hda1 [c:] as / and /dev/hda2 [d:] as /media/hda2
Don't touch /dev/hda3 [e:]

---

### Post by StGeorge on 2006-08-23
Thanks.
I will see how easy this is.
I have had murder with 98SE on this Laptop.
It messes with the IRQ's on install.
If Ubuntu works on this well it will be goodbye windows.

---

### Post by Major_Stitch on 2006-08-23
Just wanted to say that you and anybody else shouldn't be intimidated about installing a second or a fresh OS on your computer.

Just take the plunge and do it. Backup your data if you need and follow the instructions.

If you're worried about people having problems, that isn't the OS-es problem but most probably some software or hardware incompatiblity or users lack of care for the system.

That's all!

---

### Post by StGeorge on 2006-08-23
I am backing up now but will post with an update when I have installed.
I do agree with have no fear, but it is as well that I have good backup.

---

### Post by A_608 on 2006-08-24
Be sure and back up. Have you installed yet? I too switched from 98se to Unbutu. I'm going to keep 98se for my audio editing and midi. I'm not ready to give up Sibelius.

---

### Post by A_608 on 2006-08-24
Here I am saying back up and I missed the part where you said you were backing up your harddrive....Anyway hope your experience is painless. I had to find a fix to get my Brother HL2040 to work. One thing by default, the root account is disabled. As the first user, you will have administrative priviledges. You will be able to create accounts and place restrictions on them. Having the root account disabled makes hacking into your system difficult. Most of the time I am finding you can use the sudo command if needed for system administration.

---

### Post by tkjacobsen on 2006-08-25
> **StGeorge said:**
> 
Processor Description	Pentium(R) II, 297MHz
Total Memory	319MB


Maybe you should try xubuntu with that processor. It is more lightweight than ubuntu.

---

### Post by StGeorge on 2006-08-26
Well after a little problem with username on initial login, see:

[http://www.ubuntuforums.org/showthread.php?t=242764&highlight=login+problem+username](http://www.ubuntuforums.org/showthread.php?t=242764&highlight=login+problem+username)

Ubuntu installed well.
I did have a little problem with drive partitioning etc but got around that.
The problem now is that Ubuntu has not installed a sound driver.
I have checked ALSA Soundcard Matrix see:

[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

but my manufacturer is not listed.

Device Type	Sound, video and game controllers
Device Name	 
Description	Crystal PnP Audio System Control Registers
Manufacturer	Crystal Semiconductor Corporation
Driver Provider	Crystal Semiconductor
Driver Date	10-14-1998

Device Type	Sound, video and game controllers
Device Name	 
Description	Crystal PnP Audio System CODEC
Manufacturer	Crystal Semiconductor Corporation
Driver Provider	Crystal Semiconductor
Driver Date	10-14-1998

Device Type	Sound, video and game controllers
Device Name	 
Description	Crystal PnP Audio System MPU-401 Compatible
Manufacturer	Crystal Semiconductor Corporation
Driver Provider	Crystal Semiconductor
Driver Date	10-14-1998

Device Type	Sound, video and game controllers
Device Name	 
Description	Crystal SoundFusion(tm) PCI Audio Accelerator
Manufacturer	Crystal Semiconductor Corporation
Driver Provider	Crystal
Driver Date	2-12-1999

Device Type	Sound, video and game controllers
Device Name	 
Description	Crystal SoundFusion(tm) Virtual MPU-401
Manufacturer	Crystal Semiconductor Corporation
Driver Provider	Crystal
Driver Date	2-12-1999
Any ideas?

---

