---
title: "Screen Resolution !"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Sujith.James on 2007-08-19
[FONT="Garamond"][/FONT]
Hello everyone !

I am very very NEW to the whole UBUNTU / linux concepts.
I have Installed Ubuntu 6.06 using VMWare Server Console. Version 1.0.1 Build-29996
I did managed to get things working, except for some minor issues.

1) I CANNOT enable SOUND; If I go into settings, it sees NO SOUND CARD !
2) I cannot change the screen resolution. either its 800x600 or 640x480.
Y cant I get a Higher resolution ??
3) How do I get the DVD driver to work ? MOUNT ? how ?

Thanks in Advance.
:guitar:

---

### Post by tdrusk on 2007-08-19
Go to your terminal (applications>accesories>terminal)  and enter 
```
lspci
```

copy that and paste it here. That will help ALOT.

---

### Post by alienexplorers on 2007-08-19
What type sound card and video card are you using.  Do you have the current drivers for your video card loaded.  As in the previous post a listing of your devices would be helpfull.
Enter in TERMINAL:
> lspci and post results here if you want help.

---

### Post by Sujith.James on 2007-08-21
Hello All !
Sorry for the delay !
& thanks a lot for all those who took time to reply.
I have managed to Enable the sound + have the DVD drive working. 
Just playing around & getting to learn things pretty quickly !!!

Now, only issue remaining is the Video resolution. My Laptop has a nVIDIA GeForce Card + System board, AMD TURION 64x2 TL-52.

any suggestions ?

Regards,
James.
:guitar:

---

### Post by Sujith.James on 2007-08-21
LSPCI Says :

Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
0000:00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
0000:00:0f.0 VGA compatible controller: VMware Inc [VMware SVGA II] PCI Display Adapter
0000:00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
0000:00:11.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)
0000:00:12.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)


YYY ?Y INTEL ? I have a AMD Processor !!!! Does VMWARE has anything to do with it ?

---

### Post by Sujith.James on 2007-08-31
Does anyone know what this issue is ?

Or am I the First person to deal with it ?

:lolflag:

---

### Post by s26c.sayan on 2007-08-31
> **Sujith.James said:**
> Does anyone know what this issue is ?

Or am I the First person to deal with it ?

:lolflag:

No, you are most certainly not the first one on this!! :lolflag:

Try searching this forums using the search bar at the top right and keywords like 'screen resolution problem', and you'll know! 

You will even find a solution to this problem!! :)

---

### Post by brett611 on 2008-03-18
Try this link.  The instrux look very straightforward and make sense conceptually

[http://www.ubuntugeek.com/how-to-set-vmware-resolution-fullscreen-as-your-ubuntu-desktop.html](http://www.ubuntugeek.com/how-to-set-vmware-resolution-fullscreen-as-your-ubuntu-desktop.html)

---

