---
title: "Sound and internet settings"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by JackMeadows on 2006-10-05
Having installed Ubuntu 6.06 ico live on a clean and empty H/D with a copy from PC authority Mag freebie cd and being totally new to Linux I have too ask some very basic questions.

I have installed it on a spare Compaq  Deskpro EN Series, 
System Type	X86-based PC
Processor	x86 Family 6 Model 7 Stepping 3 GenuineIntel ~447 Mhz
BIOS Version/Date	Compaq 686T3, 10/02/1999
Old I know but as I am very knew I am very nervous about installing it on my main machine.

I have Ubuntu up and running except for no sound.
 I have set Ubuntu in sound prefs  and it is set to play sounds as it says in the prefs to do. But in there it shows no default sound card.
This Compaq played sounds with XP on it.

Also I would like so advice as to how to set up my internet connection, my isp login details or a place that I can read how to, step by step.

What I want is to use Linux Ubuntu as my main OS for internet and the most other things and do away with using XP so I feel I am in for a hard slog but feel it will be worth it.
AS I say I am not at all familiar with Linux, so with me I am afraid, you will need a lot of patience &#61514; :mrgreen: 
Any help will be most appreciated.

---

### Post by james_san on 2006-10-05
Well if you have a dialup modem then prospects are bleak... the main problem being that their are very few drivers for software-based modems for linux. Unfortunately I haven't used dialup for years so can't help you on that one.
My advice would be to install it on your main machine in a seperate partition, then you can choose what os to boot when you turn it on. The default Ubuntu desktop is very new and likes fast computers ;)
If you right click on the volume control icon (top right system tray area) and go preferences, does it not have any sound cards to choose from?
Could you open up a terminal (applications -> accessories -> terminal) and type in `lspci` and press enter, and paste the results here.

---

### Post by JackMeadows on 2006-10-05
Here is what you asked for:
desktop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:0f.0 Modem: Motorola: Unknown device 3052 (rev 04)
0000:00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
Also I note that I had to save the file above file via Floppy to be able to cut and paste into here as the computer that I have Ubuntu installed on can only see my externall usb h/d as read only. I tried to give it permisssion but it tells me I can't set it as Write to as it is read only.

---

### Post by james_san on 2006-10-15
> I had to save the file above file via Floppy to be able to cut and paste into here as the computer that I have Ubuntu installed on can only see my externall usb h/d as read only

Do you know whether your external hard drive uses FAT32 or NTFS? Windows will tell you if you right click, properties. Linux can't write to NTFS drives. If it does use FAT32, then it should be working.

Anyway sorry I can't help you with that modem, maybe someone here has heard of it. Have a look at [http://www.linmodems.org/](http://www.linmodems.org/)

---

### Post by JackMeadows on 2006-10-15
Thanks kindly for your help.
I have got all working now save the Modem.
You were right about the filing system and the spare H/D is now fat 32.
I will have to wait till I go broadband to check linux out more.
Thanks again for your Help.:-D

---

