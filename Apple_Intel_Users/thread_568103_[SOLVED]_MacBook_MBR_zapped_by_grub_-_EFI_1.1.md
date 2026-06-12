---
title: "[SOLVED] MacBook MBR zapped by grub - EFI 1.1?"
date: 2007-10-05
forum: Apple Intel Users
---

### Post by pxwpxw on 2007-10-05
**This is just a warning about using he "savedefault" option in the grub menu.lst, and how i fixed the problem it caused me.**



MacBook C2d, with EFI firmware update 1.1, triple boot using REFIT and grub.

I changed my grub menu.lst to include the "savedefault" option.
I think grub keeps a few byte of initial data in the MBR. savedefault updates 
/boot/grub/default, but somehow the MBR was affected.

After restarting to xubuntu, at the next restart only MacosX would boot - ubuntu and XP got a black screen with a blinking curso and no progress.

After  rebooting with the Gparted/grub rescue CD, I found that the Master Boot Record on the disk had been corrupted over the first 9 bytes. So I restored the MBR to normal using dd and a copy of a good MBR (DOS MBR in this case). 

I did the MBR fix from ubuntu first, and a second time from MacosX10.4.10 on a PowerMac G5 with the MacBook in Firewire target mode. That could also be done by Windows FIXMBR, or by reinstalling grub for a grub MBR.

I dont know if the firmware update can be blamed, I had not used savedefault before. In the standard grub menu.lst comments there is a warning about savedefault affecting some systems.
 
So dont use "savedefault" in your grub menu,lst.

This is from the G5 doing the firewire target mode fix to the MacBook drive MBR.
```

### Zapped MBR first 9 bytes
mac03:~/amacbookmbr admax$ hexdump -C -n32 /dev/disk2
00000000  00 0a 0a 0a 0a 0a 0a 0a  0a 07 50 1f fc be 1b 7c  |..........P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|

#### restore to dosMBR
mac03:~/amacbookmbr admax$ sudo dd if=dos16bytes of=/dev/disk2

#### restored DOS MBR first 16 bytes.
mac03:~/amacbookmbr admax$ hexdump -C -n32 /dev/disk2
00000000  33 c0 8e d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |3.....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|

```

---

### Post by ikker666 on 2007-10-07
i also got a triple boot os x (tiger) xp and ubuntu..
but at my bootmenu there is no os x so i can't start it.. :(
woult you tell me how?

o yea sorry i can't help you... :s

---

### Post by pxwpxw on 2007-10-07
If you cant boot MacosX, try zap the pram, restart holding the  4 keys  Command-Option-P-R for 2 chimes.

---

### Post by pxwpxw on 2007-10-08
Anyone else had a problem with "savedefault" - or anyone using savedefault but not had a problem?

Now I have removed XP, just leaving Macosx and Ubuntu via grub on ther MBR savedfault works fine and not a problem.
Seems to only be a problem with a Windows MBR.

---

