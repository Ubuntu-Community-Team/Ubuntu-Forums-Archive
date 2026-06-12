---
title: "install problem due to RAID controller?"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by roderashe on 2006-05-24
Had an earlier post about a boot problem after install but realized that the box I have has a hardware raid controller. Is this the reason I can't boot? After install I try to reboot but get 'error loading operating system'. I've tried the auto-partition and manual partition but get the same result. Here's the config of the box. By looking at this, is there any reason I can't get this to work? Thanks!

1	5120P	CORD, POWER, 125V, 6FT, SPT2, UNSHIELDED
1	C0724	PROCESSOR, 80532, 2.8G, 512K, 800FSB, SOCKET N
1	K1010	CARD (CIRCUIT), GRAPHICS, VIDEO, PC INTERFACE, RAGE-XL
1	T2408	CARD (CIRCUIT), PLANAR (MOTHERBOARD), PE400SC, AUDIO/NIC, 2
1	K5360	KIT, DOCUMENTATION ON COMPACT DISK, DOCUMENT OBJECT MODEL, SINGLE CHANNEL, V2.0, WORLD WIDE
1	7N242	KEYBOARD, 104, UNITED STATES, SILITEK, LOW COST, MIDNIGHT GRAY
1	W1668	KIT, MOUSE, PERSONAL SYSTEM 2, 2BTN, WHEEL, LOGITECH
2	M0215	DUAL IN-LINE MEMORY MODULE, 512, 400M, 64X72, 8K, ERROR CORRECTION CODE, 184
1	F3053	COMPACT DISK DRIVE, 48X, IDE (INTEGRATED DRIVE ELECTRONICS), HITACHI LG DATA STORAGE, HALF HEIGHT, INTERNAL, CHASSIS 2001
1	M1619	DISPLAY, FLAT PANEL DISPLAY, 15, DUAL, E152FPC, MIDNIGHT GRAY, DELL AMERICAS ORGANIZATION
1	5U692	FLOPPY DRIVE, 1.44M, 3.5" FORM FACTOR, 3MD, NO BEZEL, SAMSUNG, CHASSIS 2001
1	42964	CABLE, LIGHT EMITTING DIODE, HARD DRIVE, AUXILIARY, 7
1	X2797	CARD (CIRCUIT), CONTROLLER, Serial ATA, PROMISE, DIMENSION, PRECISION WORKSTATION
1	P0253	CABLE, POWER, 6P, AUXILIARY, Serial ATA, TRANSFORMER SKY DIVE MINITOWER
2	T5714	ASSEMBLY, CABLE, Serial ATA, TRANSFORMER SKY DIVE MINITOWER, 2.0
1	U4001	HARD DRIVE, 160GB, Serial ATA, 8MB, 7.2K, WD-XL80
1	U4001	HARD DRIVE, 160GB, Serial ATA, 8MB, 7.2K, WD-XL80
1	C0132	OVERPACK KIT, MICROSOFT WINDOWS SERVER 2003 STANDARD EDITION, ENGLAND/ENGLISH, WORLD WIDE
1	8G779	CARD (CIRCUIT), NETWORK, PC INTERFACE, INTEL, PRO100S

---

### Post by jorn on 2006-05-24
I don't think the raid hardware is causing this as long as you don't try to set Ubuntu up with raid.
Do you see the grub menu at start-up? Press the ESC- botton after hardware detection.
Maybe grub can't find the correct boot partition.
I have to go to work now - sorry.

---

### Post by roderashe on 2006-05-24
Thanks, jorn.

No, I don't see the grub menu at startup. Is 'ESC- bottom' ESC + down arrow or page down? Thanks.

---

### Post by jorn on 2006-05-24
Just Esc. The grub boot-loader was installed automatically?
I'm afraid I'm on deep water, haven't got other suggestions that could lead to solutions.

---

### Post by roderashe on 2006-05-24
Thanks, again, jorn.

Yes, grup was installed automatically during the initial install. I'll try hitting ESC when I get home. Thanks!

---

