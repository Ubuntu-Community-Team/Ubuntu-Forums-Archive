---
title: "[SOLVED] Really Frustrated... Can Not Install"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by Therion on 2007-09-29
Okay I've downloaded and burned four separate Ubuntu Live CD's and tried to install but every time it's a different error.  

First download was version 7.04 and everything was fine until I got a Gnome error when loading the desktop.  Burned the CD a second time, using the same download file but at a slower speed, and got the same error.

Second download was the 6.06.1 LTS version, and it's giving me Window X error pretty much right off the bat.  Burned another CD, using the same download file but at a slower speed, and got the same error.

All four CD's were write-verified and ARE in the proper .iso format. 

Help, please, before I throw in the towel!!

---

### Post by overdrank on 2007-09-29
> **Therion said:**
> Okay I've downloaded and burned four separate Ubuntu Live CD's and tried to install but every time it's a different error.  

First download was version 7.04 and everything was fine until I got a Gnome error when loading the desktop.  Burned the CD a second time, using the same download file but at a slower speed, and got the same error.

Second download was the 6.06.1 LTS version, and it's giving me Window X error pretty much right off the bat.  Burned another CD, using the same download file but at a slower speed, and got the same error.

All four CD's were write-verified and ARE in the proper .iso format. 

Help, please, before I throw in the towel!!

Hi and welcome, could you give us some specs on your system and did you checksum the disc?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Therion on 2007-09-29
I don't know if this is good news or bad; but the checksums are coming back mismatched.

What do I do now?

And thanks for your help!

As for specs, will a DXDIAG suffice?

------------------
System Information
------------------
Time of this report: 9/29/2007, 15:27:06
       Machine name: BAPHOMET
   Operating System: Windows XP Professional (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_gdr.070227-2254)
           Language: English (Regional Setting: English)
System Manufacturer: System manufacturer
       System Model: System Product Name
               BIOS: BIOS Date: 12/14/05 11:50:14 Ver: 08.00.12
          Processor: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+,  MMX,  3DNow (2 CPUs), ~2.2GHz
             Memory: 2048MB RAM
          Page File: 484MB used, 3456MB available
        Windows Dir: C:\WINDOWS
    DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
     DxDiag Version: 5.03.2600.2180 32bit Unicode

------------
DxDiag Notes
------------
  DirectX Files Tab: No problems found.
      Display Tab 1: No problems found.
        Sound Tab 1: No problems found.
          Music Tab: No problems found.
          Input Tab: No problems found.
        Network Tab: No problems found.

--------------------
DirectX Debug Levels
--------------------
Direct3D:    0/4 (n/a)
DirectDraw:  0/4 (retail)
DirectInput: 0/5 (n/a)
DirectMusic: 0/5 (n/a)
DirectPlay:  0/9 (retail)
DirectSound: 0/5 (retail)
DirectShow:  0/6 (retail)

---------------
Display Devices
---------------
        Card name: NVIDIA GeForce 8800 GTS
     Manufacturer: NVIDIA
        Chip type: GeForce 8800 GTS
         DAC type: Integrated RAMDAC
       Device Key: Enum\PCI\VEN_10DE&DEV_0193&SUBSYS_C8153842&REV_A2
   Display Memory: 320.0 MB
     Current Mode: 1280 x 1024 (32 bit) (60Hz)
          Monitor: Plug and Play Monitor
  Monitor Max Res: 1600,1200
      Driver Name: nv4_disp.dll
   Driver Version: 6.14.0011.6003 (English)
      DDI Version: 9 (or higher)
Driver Attributes: Final Retail
 Driver Date/Size: 4/27/2007 17:55:00, 5440000 bytes
      WHQL Logo'd: n/a
  WHQL Date Stamp: n/a
              VDD: n/a
         Mini VDD: nv4_mini.sys
    Mini VDD Date: 4/27/2007 17:55:00, 6778528 bytes
Device Identifier: {D7B71E3E-42D3-11CF-814C-1EE803C2CB35}
        Vendor ID: 0x10DE
        Device ID: 0x0193
        SubSys ID: 0xC8153842
      Revision ID: 0x00A2
      Revision ID: 0x00A2
      Video Accel: ModeMPEG2_A ModeMPEG2_B ModeMPEG2_C ModeMPEG2_D ModeWMV9_B ModeWMV9_A 
 Deinterlace Caps: {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(UYVY,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(UYVY,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(YV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
         Registry: OK
     DDraw Status: Enabled
       D3D Status: Enabled
       AGP Status: Enabled
DDraw Test Result: Not run
 D3D7 Test Result: Not run
 D3D8 Test Result: Not run
 D3D9 Test Result: Not run

-------------
Sound Devices
-------------
            Description: SB Audigy 2 ZS Audio [B880]
 Default Sound Playback: Yes
 Default Voice Playback: Yes
            Hardware ID: PCI\VEN_1102&DEV_0004&SUBSYS_20021102&REV_04
        Manufacturer ID: 1
             Product ID: 100
                   Type: WDM
            Driver Name: ctaud2k.sys
         Driver Version: 6.00.0001.1241 (English)
      Driver Attributes: Final Retail
            WHQL Logo'd: n/a
          Date and Size: 4/10/2007 04:20:38, 520488 bytes
            Other Files: 
        Driver Provider: Creative
         HW Accel Level: Full
              Cap Flags: 0x0
    Min/Max Sample Rate: 0, 0
Static/Strm HW Mix Bufs: 0, 0
 Static/Strm HW 3D Bufs: 0, 0
              HW Memory: 0
       Voice Management: Yes
 EAX(tm) 2.0 Listen/Src: Yes, Yes
   I3DL2(tm) Listen/Src: No, No
Sensaura(tm) ZoomFX(tm): No
               Registry: OK
      Sound Test Result: Not run

---------------------
Sound Capture Devices
---------------------
            Description: SB Audigy 2 ZS Audio [B880]
  Default Sound Capture: Yes
  Default Voice Capture: Yes
            Driver Name: ctaud2k.sys
         Driver Version: 6.00.0001.1241 (English)
      Driver Attributes: Final Retail
          Date and Size: 4/10/2007 04:20:38, 520488 bytes
              Cap Flags: 0x0
           Format Flags: 0x0

            Description: Microsoft LifeCam VX-3000.
  Default Sound Capture: No
  Default Voice Capture: No
            Driver Name: usbaudio.sys
         Driver Version: 5.01.2600.2180 (English)
      Driver Attributes: Final Retail
          Date and Size: 8/3/2004 23:07:56, 59264 bytes
              Cap Flags: 0x0
           Format Flags: 0x0

---

### Post by overdrank on 2007-09-29
> **Therion said:**
> I don't know if this is good news or bad; but the checksums are coming back mismatched.

What do I do now?

And thanks for your help!

HI you will need to download from another mirror. Then you can run the checksum again. This has happened several time in the last couple of days. :(
Edit I just saw your specs and the nvidia 8800 may be some problem but I think it will be manageable.

---

### Post by Therion on 2007-09-29
I've downloaded install .iso's from a couple different mirror sites already, but I have yet *another* download going, even as I type this.

I'm assuming there's no point in going any further until I get a burn that returns matching checksums, so I'll keep hacking at it.  Good thing CD's are cheap.

Thanks again... I'm trying not to lose hope.

---

### Post by overdrank on 2007-09-29
> **Therion said:**
> I've downloaded install .iso's from a couple different mirror sites already, but I have yet *another* download going, even as I type this.

I'm assuming there's no point in going any further until I get a burn that returns matching checksums, so I'll keep hacking at it.  Good thing CD's are cheap.

Thanks again... I'm trying not to lose hope.

Great it is worth it and if you have trouble with anything else please feel free to ask! :guitar:

---

### Post by Therion on 2007-09-29
> **overdrank said:**
> ... I just saw your specs and the nvidia 8800 may be some problem but I think it will be manageable.
Okay, just had minor brainstorm.  I bought a Ubuntu book the other day and never looked at the CD/DVD in the back.  

AH HA!!  The book does indeed have a bootable DVD with v6.06 LTS on it so I booted using *that* disc.

Server X error.

I'm assuming now this problem is related to my video card??

---

### Post by overdrank on 2007-09-29
> **Therion said:**
> Okay, just had minor brainstorm.  I bought a Ubuntu book the other day and never looked at the CD/DVD in the back.  

AH HA!!  The book does indeed have a bootable DVD with v6.06 LTS on it so I booted using *that* disc.

Server X error.

I'm assuming now this problem is related to my video card??

Yes it is and here is a thread that we worked through 
[http://ubuntuforums.org/showthread.php?t=559891](http://ubuntuforums.org/showthread.php?t=559891)
it is long post but you can breeze through it and get the commands and instruction and I hope this helps. :)

---

### Post by Presto123 on 2007-09-29
*Edit* Never mind.

---

### Post by overdrank on 2007-09-29
> **Presto123 said:**
> Quick question:

What program and process are you using to burn it to disk?

Good point you may look at this 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Therion on 2007-09-29
> **overdrank said:**
> Good point you may look at this 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Thank you but those are the instructions I've been following.  I've also tried using ActiveISO Burner.

> **overdrank said:**
> Yes it is and here is a thread that we worked through 
[http://ubuntuforums.org/showthread.php?t=559891](http://ubuntuforums.org/showthread.php?t=559891)
it is long post but you can breeze through it and get the commands and instruction and I hope this helps. :)

As for the aforementioned thread I found the following command line:

**sudo dpkg-reconfigure x-server-xorg**  but it returned an error saying either xserver or xorg was not installed and no information was available.

**** BUT!!! ****  And hopefully this is a good sign!!  I can get to the desktop without any errors using the Safe Graphics Mode (or was it Safe Display Mode?) from the main menu!  Whichever it's called, that option got me to the desktop without a problem.  Well, actually my screen went blank, but as soon as i hit a key on my keboard, the desktop appeared!  

Now... what I've been trying to do (for the past several hours) is install Ubuntu on my secondary hard drive.  I've backed up all the data and am comfortable using this secondary hard drive solely for a Ubuntu install (dual booting with WinXP which is installed on the primary hard drive).

So... am I safe, booting into Ubuntu's "Safe Graphics Mode", doing a full install and going from there, or would that simply be "shooting myself in the foot"??

Thanks for all the help so far, btw...

---

### Post by overdrank on 2007-09-29
> **Therion said:**
> Thank you but those are the instructions I've been following.  I've also tried using ActiveISO Burner.



As for the aforementioned thread I found the following command line:

**sudo dpkg-reconfigure x-server-xorg**  but it returned an error saying either xserver or xorg was not installed and no information was available.

**** BUT!!! ****  And hopefully this is a good sign!!  I can get to the desktop without any errors using the Safe Graphics Mode (or was it Safe Display Mode?) from the main menu!  Whichever it's called, that option got me to the desktop without a problem.  Well, actually my screen went blank, but as soon as i hit a key on my keboard, the desktop appeared!  

Now... what I've been trying to do (for the past several hours) is install Ubuntu on my secondary hard drive.  I've backed up all the data and am comfortable using this secondary hard drive solely for a Ubuntu install (dual booting with WinXP which is installed on the primary hard drive).

So... am I safe, booting into Ubuntu's "Safe Graphics Mode", doing a full install and going from there, or would that simply be "shooting myself in the foot"??

Thanks for all the help so far, btw...

HI I believe you are ok installing but that command is like it said it is not installed until you install the OS. That command will work and you may have to add the vga command to the kernel mentioned in that thread good luck!

---

### Post by Therion on 2007-09-29
> **overdrank said:**
> 
HI I believe you are ok installing but that command is like it said it is not installed until you install the OS. That command will work and you may have to add the vga command to the kernel mentioned in that thread good luck!

Alright then... I'm going to try a doing a full install using the Safe option.  I'll then try the command line and/or the kernel command line if required.  

I'll post back and let you know how it works out.

Thanks again!  Crossing my fingers...


**EDIT:**

Okay!!  Things seem to running smoothly at this point.  No errors when I boot, installed 265 updates, rebooted and still going strong.  Do I still need to use the command line updates, or am I okay at this point?  My monitor's display is acceptable at this point but it could be better.

Trying to use the **reconfigure x-server-xorg** command in the Terminal gives me the same (following error):

[i]
Package `x-server-xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: x-server-xorg is not installed[/i]

---

### Post by overdrank on 2007-09-30
> **Therion said:**
> Alright then... I'm going to try a doing a full install using the Safe option.  I'll then try the command line and/or the kernel command line if required.  

I'll post back and let you know how it works out.

Thanks again!  Crossing my fingers...


**EDIT:**

Okay!!  Things seem to running smoothly at this point.  No errors when I boot, installed 265 updates, rebooted and still going strong.  Do I still need to use the command line updates, or am I okay at this point?  My monitor's display is acceptable at this point but it could be better.

Trying to use the **reconfigure x-server-xorg** command in the Terminal gives me the same (following error):

[i]
Package `x-server-xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: x-server-xorg is not installed[/i]
HI just to make sure you are using the right command
```
sudo dpkg-reconfigure xserver-xorg
```
and if you would like to edit the file to fix your resolution you can do that and here is a good link 
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by Therion on 2007-09-30
> **overdrank said:**
> HI just to make sure you are using the right command
```
sudo dpkg-reconfigure xserver-xorg
```
Ah... Thank you.  I removed the superflous hypen and everything went according to plan.  I was able to add the **vga=795** command to the second line as instructed, the driver option was changed to **vesa**

[QUOTE=overdran:3450452]... and if you would like to edit the file to fix your resolution you can do that and here is a good link 
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)[/QUOTE]

Went there, followed the directions about adding the lines for Horizontal Sync and Vertical Refresh rates.  I also found that there are several screeen resolutions listed in this file, but when I try to use the System/Preferences/Screen Resolution option, the resolutions max-out at 1024x768.  Here's the relevent section of my xorg.conf file:

```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-96
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NVIDIA Default CardNVIDIA 8800GTS"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1200x800" "1152x864" "1152x768" "1024x768" "80$
        EndSubSection
        SubSection "Display"
                Depth           4

```This monitor really needs to be at 1152 x XXX (either will work for me but I believe it's native res is 1152 x 864).

I'll search around on the forums for more information about changing the screen resolution, but if you see immediately what I'm doing wrong, or know what I need to do to increase it, please feel free to point it out.  Everything looks a little "Playskoolish" at this resolution.

Thanks again!!

**EDIT:**

Okay... I'm not sure HOW it happened, but I fixed the resolution problem.

---

### Post by overdrank on 2007-09-30
> **Therion said:**
> Ah... Thank you.  I removed the superflous hypen and everything went according to plan.  I was able to add the **vga=795** command to the second line as instructed, the driver option was changed to **vesa**



Went there, followed the directions about adding the lines for Horizontal Sync and Vertical Refresh rates.  I also found that there are several screeen resolutions listed in this file, but when I try to use the System/Preferences/Screen Resolution option, the resolutions max-out at 1024x768.  Here's the relevent section of my xorg.conf file:

```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-96
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NVIDIA Default CardNVIDIA 8800GTS"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1200x800" "1152x864" "1152x768" "1024x768" "80$
        EndSubSection
        SubSection "Display"
                Depth           4

```This monitor really needs to be at 1152 x XXX (either will work for me but I believe it's native res is 1152 x 864).

I'll search around on the forums for more information about changing the screen resolution, but if you see immediately what I'm doing wrong, or know what I need to do to increase it, please feel free to point it out.  Everything looks a little "Playskoolish" at this resolution.

Thanks again!!

**EDIT:**

Okay... I'm not sure HOW it happened, but I fixed the resolution problem.

Great glad to hear could you mark this thread as solved. Thanks

---

### Post by Therion on 2007-09-30
Just to wrap things up, I think what might have solved the problem was going into the xserver setup and selecting only ONE additional resolution setting; that being the one resoultion setting higher than 1024x768.  If I ticked-off several additional resolutions at the same time, I'd get stuck in a logon-screen/command line loop after rebooting xserver.

At any rate, just putting the * in the box one the one-resolution-higher setting, and that one alone, seemed to do the trick.

Thanks for your help!!

---

