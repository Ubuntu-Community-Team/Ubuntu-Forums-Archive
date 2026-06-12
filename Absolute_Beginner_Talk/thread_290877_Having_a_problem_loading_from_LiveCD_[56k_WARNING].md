---
title: "Having a problem loading from LiveCD [56k WARNING]"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by DanSchnell on 2006-11-01
I'm having some problems booting from liveCD.  I think the easiest things to show you in order to help me is this:

Part of DXdiag
```
------------------
System Information
------------------
Time of this report: 8/24/2006, 19:14:36
       Machine name: XION
   Operating System: Windows XP Professional (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_gdr.050301-1519)
           Language: English (Regional Setting: English)
System Manufacturer: System manufacturer
       System Model: System Product Name
               BIOS: Phoenix - AwardBIOS v6.00PG
          Processor: AMD Athlon(tm) 64 Processor 3700+,  MMX,  3DNow, ~2.2GHz
             Memory: 1024MB RAM
          Page File: 253MB used, 2206MB available
        Windows Dir: C:\WINDOWS
    DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
     DxDiag Version: 5.03.2600.2180 32bit Unicode

---------------
Display Devices
---------------
        Card name: NVIDIA GeForce 6800 GS 
     Manufacturer: NVIDIA
        Chip type: GeForce 6800 GS
         DAC type: Integrated RAMDAC
       Device Key: Enum\PCI\VEN_10DE&DEV_00C0&SUBSYS_C3913842&REV_A2
   Display Memory: 256.0 MB
     Current Mode: 1280 x 1024 (32 bit) (60Hz)
          Monitor: Plug and Play Monitor
  Monitor Max Res: 1600,1200
      Driver Name: nv4_disp.dll
   Driver Version: 6.14.0010.9131 (English)
      DDI Version: 9 (or higher)
Driver Attributes: Final Retail
 Driver Date/Size: 6/1/2006 17:22:00, 4529408 bytes
      WHQL Logo'd: Yes
  WHQL Date Stamp: n/a
              VDD: n/a
         Mini VDD: nv4_mini.sys
    Mini VDD Date: 6/1/2006 17:22:00, 3925920 bytes
Device Identifier: {D7B71E3E-4380-11CF-5978-9BE303C2CB35}
        Vendor ID: 0x10DE
        Device ID: 0x00C0
        SubSys ID: 0xC3913842
      Revision ID: 0x00A2
      Revision ID: 0x00A2
      Video Accel: ModeMPEG2_A ModeMPEG2_B ModeMPEG2_C ModeMPEG2_D ModeWMV9_B ModeWMV9_A 
 Deinterlace Caps: {212DC724-3235-44A4-BD29-E1652BBCC71C}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {212DC724-3235-44A4-BD29-E1652BBCC71C}: Format(In/Out)=(UYVY,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(UYVY,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {212DC724-3235-44A4-BD29-E1652BBCC71C}: Format(In/Out)=(YV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {212DC724-3235-44A4-BD29-E1652BBCC71C}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
         Registry: OK
     DDraw Status: Enabled
       D3D Status: Enabled
       AGP Status: Enabled
DDraw Test Result: Not run
 D3D7 Test Result: Not run
 D3D8 Test Result: Not run
 D3D9 Test Result: Not run


```

screenshots: 
[IMG]http://img.photobucket.com/albums/v512/tathar902/other%20stuff/screenshots/100_0155.jpg[/IMG]

[IMG]http://img.photobucket.com/albums/v512/tathar902/other%20stuff/screenshots/100_0154.jpg[/IMG]

[IMG]http://img.photobucket.com/albums/v512/tathar902/other%20stuff/screenshots/100_0153.jpg[/IMG]

[IMG]http://img.photobucket.com/albums/v512/tathar902/other%20stuff/screenshots/100_0152.jpg[/IMG]

[IMG]http://img.photobucket.com/albums/v512/tathar902/other%20stuff/screenshots/100_0151.jpg[/IMG]

---

### Post by moshuptrail on 2006-11-01
Wrong video driver OR xconfig not configured properly.  I can't remember the file it's in.  I had a similar problem and had to manually edit it.
Be right back - I'll try to look it up.

---

### Post by moshuptrail on 2006-11-01
I think the file is xorg.conf.  Try this link.  A search on nvidia will find a lot of people who have had trouble with nvidia drivers.  Best of luck!

[http://www.ubuntuforums.org/showthread.php?t=289488&highlight=xorg.conf](http://www.ubuntuforums.org/showthread.php?t=289488&highlight=xorg.conf)

---

### Post by DanSchnell on 2006-11-01
Doesn't help.  

/bump need help...

---

### Post by DanSchnell on 2006-11-04
I'm still having this problem.. And I can't even make a partition from the alternate cd to install it and then install nvidia drivers....

Can someone help?

---

### Post by Dual Cortex on 2006-11-04
I  had a similar problem, use the VGA option.

---

### Post by DanSchnell on 2006-11-04
doesn't work.  tried it.

---

### Post by Efwis on 2006-11-04
can you post your xorg.conf file for review. It might be a simple case of trying to use the wrong driver for the nvidia card you have.

---

### Post by DanSchnell on 2006-11-04
How am I supposed to paste my xorg.conf when i can't even properly boot ubuntu?  Is there a way for me to paste it while in the Terminal?

---

### Post by 3rdalbum on 2006-11-04
Did you try booting the Safe Mode from the Live CD?

---

### Post by DanSchnell on 2006-11-05
Doesn't work.

---

### Post by VinylPusher on 2006-11-05
> **DanSchnell said:**
> Doesn't work.

A similar issue afflicts my old KG7-RAID, Athlon XP 1900+ machine. Every couple of boots, Ubuntu (6.06) falls at the first hurdle. It pauses very soon after displaying the initial Ubuntu logo and then, after a while, the screen corrupts much in the same way as the screenshots you've posted (although slightly less interesting!).

It does it when booting from the Live CD and it does it when booting from the one and lonely little HD I have in the machine.

Once it does boot, everything is rock solid and stable.

---

### Post by DanSchnell on 2006-11-05
My doesn't even revert back to normal.  It just stays like that.  The Display manager doesn't like my computer.  I don't know what it is.  And I can't even partition my hard drive for some reason...even with the alternate installer...

---

