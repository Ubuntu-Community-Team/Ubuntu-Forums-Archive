---
title: "Windows 3.0 install floppy layout"
date: 2012-04-07
forum: Any Other OS
---

### Post by roelforg on 2012-04-07
Long story...

I was helping my granny clean her attic and we found her old ibm ps/1 2121.
She gave it to me (there are some fun games on it! Original pacman anyone?).
It also has win 3.0 on it.
Now the problem is that everything is in german.
Now i succeeded in setting the kbd to international and using a kbd from another pc.
As i haven't figured out how to change the language of the dos console, "my software",ibm-dos and seperate progs yet, help would be appriciated.
The main problem is:
when i open win 3.0 control panel (thanks to google translate) and change the language to english, it asks for the (long gone) win 3.0 install floppy.
It wanted langeng.dll.
Now, that file is on the hd (C:\WINDOWS\DRIVERS\langeng.dll).
So does anyone know the dir layout of the second install floppy?
my plan is to take a blank floppy and put the file where win expects it.
And trick it into changing language.

Anyone any ideas?

Edit:
Some extra info:
Ibm ps/1 model 2121
40meg hd
O/S: Win 3.0 / Ms-Dos / Pc-Dos (the stuff on the build-in rom, gotta find a way to change it's language as well)
State: A little dusty (understatement) but in almost perfect condition otherwise. (the white colour of the case hasn't even started to fade!)
Bought in germany
CPU: intel 80386sx
Ram: 2mb
1.44 floppy

---

### Post by roelforg on 2012-04-08
bump

---

### Post by zirkoni on 2012-04-08
These are on my Windows 3.11 2nd floppy, I guess they are pretty much the same as in Windows 3.0
```
CGA40850.FO_
CGA80850.FO_
COMM.DR_
COMMCTRL.DL_
CPWIN386.CP_
DISK2
DOSX.EX_
EGA40WOA.FO_
EGA80WOA.FO_
EGA40850.FO_
EGA80850.FO_
FRAMEWRK.DL_
HPEBIOS.38_
HPSYSTEM.DR_
KBDBE.DL_
KBDBR.DL_
KBDCA.DL_
KBDDA.DL_
KBDDV.DL_
KBDFC.DL_
KBDFI.DL_
KBDFR.DL_
KBDGR.DL_
KBDHP.DR_
KBDIC.DL_
KBDIT.DL_
KBDLA.DL_
KBDNE.DL_
KBDNO.DL_
KBDPO.DL_
KBDSF.DL_
KBDSG.DL_
KBDSP.DL_
KBDSW.DL_
KBDUK.DL_
KBDUS.DL_
KBDUSX.DL_
KEYBOARD.DR_
KEYVIEW.EX_
LANGDUT.DL_
LANGENG.DL_
LANGFRN.DL_
LANGGER.DL_
LANGSCA.DL_
LANGSPA.DL_
LMOUSE.CO_
LMOUSE.DR_
LVMD.38_
LZEXPAND.DL_
MMSOUND.DR_
MOUSE.DR_
MSC3BC2.DR_
MSCMOUSE.DR_
MSCVMD.38_
NOMOUSE.DR_
POWER.DR_
POWER.HL_
SCHDPLUS.EX_
SCONFIG.DL_
SHELL.DL_
SL.DL_
SL.HL_
SUPERVGA.DR_
SYSTEM.DR_
SYSTEM.SR_
V7VDD.38_
V7VGA.3G_
V7VGA.DR_
VDD8514.38_
VDDSVGA.38_
VDDVGA30.38_
VDDXGA.38_
VER.DL_
VGA30.3G_
VGA850.FO_
VGA860.FO_
VGA861.FO_
VGA863.FO_
VGA865.FO_
VGA.3G_
VGA.DR_
VGADIB.3G_
VGAFIX.FO_
VGALOGO.LG_
VGALOGO.RL_
VGAOEM.FO_
VGASYS.FO_
VPOWERD.38_
WIN386.EX_
WIN.SR_
WINDOWS.LO_
XGA.DR_
XLAT850.BI_
XLAT860.BI_
XLAT861.BI_
XLAT863.BI_
XLAT865.BI_
386MAX.VX_
8514.DR_
8514FIX.FO_
8514OEM.FO_
8514SYS.FO_
APP850.FO_
BLUEMAX.VX_
CGA40WOA.FO_
CGA80WOA.FO_
```

---

### Post by roelforg on 2012-04-08
why's the last L a _ ?
And it's all just in the root dir?

---

### Post by zirkoni on 2012-04-08
> **roelforg said:**
> why's the last L a _ ?
That's the way some files are on the original disks. They are all compressed files. You can expand them with EXPAND.EXE

> **roelforg said:**
> And it's all just in the root dir?
Yep.

---

### Post by roelforg on 2012-04-08
> **zirkoni said:**
> They are all compressed files. You can expand them with EXPAND.EXE


Yep.

Can you tell me how to convert the uncompressed dll files into the compressed ones?
I'm a real dos/windows noob.
I wanna put linux on it but unless i can set the language to english i can't operate the file manager.

---

### Post by zirkoni on 2012-04-08
[This site tells]("http://www.cabextract.org.uk/libmspack/doc/szdd_kwaj_format.html") you'd need a DOS program called compress.exe to do it (the files I have are in KWAJ format).

Maybe just try renaming the *.DLL file to *.DL_
It might work even without the compression.

---

### Post by roelforg on 2012-04-08
THX zirkoni
I'll check tomorrow as i need to borrow a keyboard from another pc for this and i'm using that pc to run tests.

---

