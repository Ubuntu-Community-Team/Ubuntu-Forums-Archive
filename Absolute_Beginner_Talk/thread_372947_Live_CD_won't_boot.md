---
title: "Live CD won't boot"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by ident4 on 2007-02-28
Hi I'm trying to get a live CD I have (version 5.10) to boot on a HP Pavilion. As soon as I press enter when it asks if I want to boot, two lines of text appear quickly on the screen, then it goes blank and starts again. I've copied the text from Belarc Advisor below so you know what hardware I have. I'm afraid I don't know what to look for:
```
Operating System 	  	System Model
Windows XP Home Edition Service Pack 2 (build 2600) 	  	HP Pavilion....
Enclosure Type: Desktop
Processor a 	  	Main Circuit Board b
2.53 gigahertz Intel Celeron
16 kilobyte primary memory cache
256 kilobyte secondary memory cache 	  	Board: MICRO-STAR INTERNATIONAL CO., LTD Gamila/Giovani/Neon series 030
Bus Clock: 133 megahertz
BIOS: Phoenix Technologies, LTD 3.09 03/25/2004
Drives 	  	Memory Modules c,d
80.00 Gigabytes Usable Hard Drive Capacity
52.14 Gigabytes Hard Drive Free Space

LITE-ON COMBO SOHC-4832K [CD-ROM drive]
3.5" format removeable media [Floppy drive]

WDC WD800BB-00JHC0 [Hard drive] (80.03 GB) -- drive 0, s/n -------------, rev 05.01C05, SMART Status: Healthy 	  	248 Megabytes Installed Memory

Slot 'A0' has 256 MB
Slot 'A1' is Empty
  	Local Drive Volumes
  	
		
c: (NTFS on drive 0) 	74.37 GB 	50.50 GB free
d: (FAT32 on drive 0) 	5.63 GB 	1.64 GB free
  	Network Drives
  	
 
Users (mouse over user name for details) 	  	Printers
local user accounts	last logon
 Owner 	25/02/2007 00:27:53 	(admin)
local system accounts
 Administrator 	never 	(admin)
 ASPNET 	never 	
 Guest 	25/02/2007 15:52:47 	
 HelpAssistant 	never 	
 SUPPORT_388945a0 	never 	
 SUPPORT_fddfa904 	never 	

DISABLED Marks a disabled account;   LOCKED OUT Marks a locked account
	  	None detected
Controllers 	  	Display
Standard floppy disk controller
Intel(r) 82801DB Ultra ATA Storage Controller-24CB
Primary IDE Channel [Controller]
Secondary IDE Channel [Controller] 	  	Intel(R) 82845G/GL/GE/PE/GV Graphics Controller [Display adapter]
hp v72 [Monitor] (15.7"vis, s/n CNN4222C3L, May 2004)
Bus Adapters 	  	Multimedia
Intel(r) 82801DB/DBM USB 2.0 Enhanced Host Controller - 24CD
Intel(r) 82801DB/DBM USB Universal Host Controller - 24C2
Intel(r) 82801DB/DBM USB Universal Host Controller - 24C4
Intel(r) 82801DB/DBM USB Universal Host Controller - 24C7 	  	Realtek AC'97 Audio
Communications 	  	Other Devices
Agere Systems PCI Soft Modem

		
1394 Net Adapter
Realtek RTL8139/810x Family Fast Ethernet NIC

	 
```

---

### Post by alienexplorers on 2007-02-28
Did you set your BIOS to boot from CD first.  If not then get into your BIOS setup routine and change it to boot CD first.

---

### Post by ident4 on 2007-02-28
> **alienexplorers said:**
> Did you set your BIOS to boot from CD first.  If not then get into your BIOS setup routine and change it to boot CD first.

Hi
Yes it boots from CD first.
The disk does kick in and Ubuntu asks me if I want to boot it (can't remember the exact words but I can get through all the help screens giving me options to press the F keys for help  with special setups)

But when I press enter to boot, it just blanks and restarts the process.

---

### Post by nickoli_02 on 2007-02-28
try checking the CD for errors when it first boots, it's one of the options. If the check finds any errors try burning the image again at a lower speed.

---

### Post by ident4 on 2007-02-28
... I should add that I've tried the disk in another computer and it works fine.

---

### Post by ident4 on 2007-02-28
> **nickoli_02 said:**
> try checking the CD for errors when it first boots, it's one of the options. If the check finds any errors try burning the image again at a lower speed.
Hi
The CD was one I sent away for, not one I burnt myself

---

### Post by ident4 on 2007-03-25
Anyone got any more ideas on this?

I have since tried a few other Live CDs - (Knoppix and Linspire)
and even [Wubi]("http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html").

None will work. So it's not just Ubuntu it doesn't like

---

### Post by lamalex on 2007-03-25
have you tried adding noapic and acpi=off to bootflags? hit f6 before you hit enter to boot livecd and enter those two flags.

---

### Post by randell6564 on 2007-03-25
> **ident4 said:**
> Hi
Yes it boots from CD first.
The disk does kick in and Ubuntu asks me if I want to boot it (can't remember the exact words but I can get through all the help screens giving me options to press the F keys for help  with special setups)

But when I press enter to boot, it just blanks and restarts the process.

Hi.  It's asking you do you want to boot from CD or Hard drive.  If you choose hard drive then yes, it will start all over again. You want it to boot from CD.

---

### Post by ident4 on 2007-03-25
> **Iamalex said:**
> have you tried adding noapic and acpi=off to bootflags? hit f6 before you hit enter to boot livecd and enter those two flags.

Fantastic!!
That worked. I'm writing this from Ubuntu. :) 

What did that do?

How do I make it do that permanantely when I install Ubuntu

---

### Post by ident4 on 2007-03-26
It's only acpi=off that I have to set.

If I make this permanant when I install Ubuntu, will it do any damage to the computer?

Sorry - completely new at this. :D

---

### Post by cowlip on 2007-03-26
I think it just turns of ACPI power management, which can be a problem with some computers, so you might not get nice options like turning off automatically when shutting down, or hibernate/suspend.  Or they might work with APM instead.

---

