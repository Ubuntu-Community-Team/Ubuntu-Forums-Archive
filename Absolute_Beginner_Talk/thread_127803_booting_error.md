---
title: "booting error"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by newtolinux22 on 2006-02-09
I have installed Ubunto 5.10 on one hd, I have 2, one is 40gb(windows and some data) and another is 80gb(60gb for data now is empty, and 20 gb for linux) the problem is when I start ubuntu it stops at the part that says "Starting hotplug subsystem" and dont go forward that part, I dont know what to do, everything seems fine, please help me

---

### Post by blair on 2006-02-10
my guess is that the default USB driver settings are incompatible with your hardware. Your goal now should be to boot without loading the USB components. Once booted, you will have to start troubleshooting the USB problem. Then you will need to modify your startup config so that the USB drivers load in a way that is compatible with your hardware. I can't help you there since I have no experience troubleshooting USB.  

To control the boot process, you should edit your boot settings temporarily to prompt you at each and every step of the boot process so it asks you 300 times  do you want to load this? do you want to load that? etc. I can't remember exactly how to do this so will have to dig through my old notes. If you post a request for help on that (controlling the boot process) someone whoe knows the answer can help. 

Keep hitting enter (default response is yes), until you reach the option to load the USB hotplug component, at which point you select no. You may also want to decline any other USB-related things you see in the boot up proces.

---

### Post by newtolinux22 on 2006-02-10
[QUOTE=blair]Your goal now should be to boot without loading the USB components[/QUOTE] How do I boot without loading the USB components?

---

### Post by GreyFox503 on 2006-02-10
I don't know how to do the very detailed choosing method described above, but pressing Ctrl + C during the boot process will cause it to skip whichever item it is currently on.

Try pressing Ctrl + C as soon as you see the hotplug item that makes it stop.  If it works, it will just continue down the list.  Once inside Ubuntu, you can work on fixing it/turning it off.

---

### Post by newtolinux22 on 2006-02-10
[QUOTE=GreyFox503]Try pressing Ctrl + C as soon as you see the hotplug item that makes it stop. If it works, it will just continue down the list. Once inside Ubuntu, you can work on fixing it/turning it off.[/QUOTE]Now that is solved, I have typed crtl c on the part that appear Starting hotplug subsystem, then finish installing ubuntu but now is another problem it appears "Falided to start the X server(your graphical interface). It is likely that is not set up correctly. Would you like to view the X server output to diagnose the problem?" I select yes and show me some information that says: "no device detected" and "no screen found" and some other things, I Have and Nvidia Geforce FX 5200 256MB DDR TV DVI and this to:
Computer:
Computer Type Monoprocesador ACPI de PC
Operating System Microsoft Windows XP Professional
OS Service Pack Service Pack 2
Internet Explorer 6.0.2900.2180 (IE 6.0 SP2)
DirectX 4.09.00.0904 (DirectX 9.0c)
Computer Name LEON (leon salazar)
User Name Administrador
SMTP E-mail Address [email]flialeon@gye.satnet.net[/email]
Logon Domain LEON
Date / Time 2006-02-06 / 18:02

Motherboard:
CPU Type Intel Pentium 4, 2800 MHz (21 x 133)
Motherboard Name ASRock P4i45GV
Motherboard Chipset Intel Brookdale-G i845GEV
System Memory 512 MB (DDR SDRAM)
BIOS Type AMI (10/18/05)
Communication Port Puerto de comunicaciones (COM1)
Communication Port Puerto de impresora ECP (LPT1)

Display:
Video Adapter NVIDIA GeForce FX 5200 (256 MB)
3D Accelerator Intel Extreme Graphics
3D Accelerator nVIDIA GeForce FX 5200

Multimedia:
Audio Adapter C-Media CMI9739A/9761 @ Intel 82801DB ICH4 - AC'97 Audio Controller [B-0]

Storage:
IDE Controller Intel(R) 82801DB Ultra ATA Storage Controller - 24CB
Floppy Drive Unidad de disquete
Disk Drive MAXTOR 4K040H2 (40 GB, 5400 RPM, Ultra-ATA/100)
Disk Drive WDC WD800BB-22JHC0 (74 GB, IDE)
Optical Drive ATAPI-CD ROM-DRIVE-56MAX (56x CD-ROM)
Optical Drive HL-DT-ST CD-RW GCE-8520B (52x/24x/52x CD-RW)
SMART Hard Disks Status OK

---

### Post by GreyFox503 on 2006-02-11
I would try reconfiguring your xserver (this will write a new xorg.conf file) as described here:

[https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)

It is an automated process that just asks a bunch of questions that you answer.  If it doesn't work, then you might have to manually edit /etc/X11/xorg.conf file.

---

