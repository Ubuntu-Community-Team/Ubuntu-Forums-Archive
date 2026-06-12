---
title: "X Server problem"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by newtolinux22 on 2006-02-10
I have typed crtl c on the part that appear Starting hotplug subsystem(because if I dont put crtl c it doesnt go forward that part), then finish installing ubuntu but now is another problem it appears "Falided to start the X server(your graphical interface). It is likely that is not set up correctly. Would you like to view the X server output to diagnose the problem?" I select yes and show me some information that says: "no device detected" and "no screen found" and some other things, I Have and Nvidia Geforce FX 5200 256MB DDR TV DVI and this to:
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

### Post by Pragmatist on 2006-02-10
Give us the output of:
```
cat /etc/X11/xorg.conf
```

---

### Post by newtolinux22 on 2006-02-10
I am gonna put that code, but someone told me that I need to install the nvidia drivers for linux, I have downloaded them but they are on a windows xp folder, they told me to mount it to get access to that file from ubuntu, but I dont know how, they give a guide but it is too complicate for me, if that is the solution, you can explain but for me a really begginer, that have 2 hd, one just for windows(40gb) and another for some data of windows(60gb) and ubuntu(20gb), the nvidia drivers are on the two hd's

---

### Post by Pragmatist on 2006-02-10
Can you get to a login screen?  (A black screen with white text that says Login: )

---

### Post by newtolinux22 on 2006-02-10
[QUOTE=Pragmatist]Can you get to a login screen?  (A black screen with white text that says Login: )[/QUOTE]
Yes, I can

---

### Post by Pragmatist on 2006-02-10
Great!  So, login and send the output of:  cat /etc/X11/xorg.conf

---

### Post by newtolinux22 on 2006-02-10
How do I do that, I just have to put cat /etc/X11/xorg.conf , I have already typed that and nothing happens

---

### Post by Pragmatist on 2006-02-10
ok, if you've logged in, what does your prompt look like?  It is the words like > username@ubuntu:~$  Sometimes there is a # instead of the $

Now, give me the output of ```
pwd;who
``` type it just like that with the semicolon in between.

---

### Post by newtolinux22 on 2006-02-11
what will happen when I press that code?

---

### Post by Pragmatist on 2006-02-11
```
pwd
```  means Print Working Directory  and will output to the screen the directory your located in.
```
who
``` will output to the screen your username.
Here is a new command that will help you:
```
man
``` stands for Manual.  You could get answers, like the ones I just gave you, by typing ```
man pwd
``` and ```
man who
```

---

### Post by Pragmatist on 2006-02-11
Also, I already asked you: > ok, if you've logged in, what does your prompt look like?  These are very basic things that I need if you want my help.

---

