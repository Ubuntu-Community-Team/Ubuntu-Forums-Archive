---
title: "PPC Installation Problems"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by jaywalker13 on 2006-07-17
Greetings

I'm having problems installing live Ubuntu on my ppc.

Machine Model:	Power Mac G4
  CPU Type:	PowerPC G4  (2.9)
  Number Of CPUs:	1
  CPU Speed:	467 MHz
  L2 Cache (per CPU):	1 MB
  Memory:	768 MB
  Bus Speed:	133 MHz
  Boot ROM Version:	4.1.8f5

Apple Studio Display 17"
ATY,Rage128Pro:  
Type:	display
  Bus:	AGP
  Display Type:	LCD
  Slot:	SLOT-1
  VRAM (Total):	16 MB
  Vendor:	ATI (0x1002)
  Device ID:	0x5046
  Revision ID:	0x0000
  ROM Revision:	113-72701-130

Display:

  Resolution:	1280 x 1024
  Depth:	32-bit Color
  Built-In:	Yes
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes

1. Downloaded iso and burned disk in this computer.
2. Loaded disk in cd drive and restarted with "c" held down.
3. Got to prompt and hit [Enter] as suggested.
4. Screen went white very briefly, then black.
5. Left it for several minutes. Finally got a lovely chord sound, but still a blank screen.
6. Restarted pc. This time entered "live video-ifonly" at prompt.
7. After a few minutes, got white bar at bottom of screen, then nice heading with list of things it was doing - but the screen was split, with writing starting at centre of screen then finishing on left side. As though the screen is off centre, needing to be pushed to the left.
8. Eventually went to a blue screen with the same split problem. This one included a message:
"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"
9. There were further terminal type messages scattered over the screen, including:
"-bash: no job control in this shell. To run command as administrator (user "root"), use "sudo <command>" etc"

I would appreciate any advice on where to go from here.

Best wishes

Jay

---

### Post by Skia_42 on 2006-07-18
PPC installations are harder the i386, I feel you pain. I installed Ubuntu on my eMac and it took a week to get working. Press Control+option+F2 to get into the command line. Your xorg configuration file can be accessed with this command: > sudo nano /etc/X11/xorg.confI'll see if I can find anything else that could help.

---

### Post by jaywalker13 on 2006-07-18
Thanks for your reply Skia.

I had a look at the xorg configuration file and noticed under "Display" it gave 4 modes (1024 x 768 etc), but none of them were the setting I have (1280 x 1024). Am I looking at changing the config file in some way? If so, I would appreciate advice on how to do that.

Regards

Jay

---

### Post by linear on 2006-07-18
Suggest you repost this in the Mac/PPC forum - more likely to be read by someone who knows the correct xorg.conf settings.

---

