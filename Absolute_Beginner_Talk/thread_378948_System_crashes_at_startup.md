---
title: "System crashes at startup"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by Heous on 2007-03-07
Hey everyone.  I'm a Windows user who's currently playing around with Ubuntu on a dual-boot Dell system, and recently I attempted to change my screen resolution.  I have a Dell UltraSharp 2007FP Flatpanel monitor, and I recently attempted to change my screen resolution to 1600x1200.  That's when everything went wrong.  I typed sudo dpkg-reconfigure xserver-xorg into the terminal based on advice I had read from the forums, and I tried adding the 1600x1200 option in there.  But whenever I reboot now, the Ubuntu loading screen crashes right before it's finished loading.  I'm not sure what exactly I did wrong, or how to correct it.  Here's some of my system specs I got from DXDIAG, if that helps you guys better diagnose my problem:

---

### Post by Heous on 2007-03-07
------------------
System Information
------------------
Time of this report: 3/7/2007, 22:53:14
       Machine name: ISANNAH
   Operating System: Windows XP Home Edition (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_gdr.050301-1519)
           Language: English (Regional Setting: English)
System Manufacturer: Dell Inc.                
       System Model: Dimension 8400               
               BIOS: Phoenix ROM BIOS PLUS Version 1.10 A03
          Processor: Intel(R) Pentium(R) 4 CPU 3.40GHz (2 CPUs)
             Memory: 1534MB RAM
          Page File: 320MB used, 1833MB available
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
        Sound Tab 2: No problems found.
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
        Card name: Radeon X1800 Series 
     Manufacturer: ATI Technologies Inc.
        Chip type: Radeon X1800 Series (0x7100)
         DAC type: Internal DAC(400MHz)
       Device Key: Enum\PCI\VEN_1002&DEV_7100&SUBSYS_0B121002&REV_00
   Display Memory: 512.0 MB
     Current Mode: 1600 x 1200 (32 bit) (60Hz)
          Monitor: Dell 2007FP (Digital)
  Monitor Max Res: 1600,1200
      Driver Name: ati2dvag.dll
   Driver Version: 6.14.0010.6652 (English)
      DDI Version: 9 (or higher)
Driver Attributes: Final Retail
 Driver Date/Size: 11/21/2006 22:25:23, 261120 bytes
      WHQL Logo'd: Yes
  WHQL Date Stamp: n/a
              VDD: n/a
         Mini VDD: ati2mtag.sys
    Mini VDD Date: 11/21/2006 22:25:08, 2829824 bytes
Device Identifier: {D7B71EE2-3240-11CF-4E6A-182BA1C2CB35}
        Vendor ID: 0x1002
        Device ID: 0x7100
        SubSys ID: 0x0B121002
      Revision ID: 0x0000
      Revision ID: 0x0000
      Video Accel: 
 Deinterlace Caps: n/a
         Registry: OK
     DDraw Status: Enabled
       D3D Status: Enabled
       AGP Status: Disabled
DDraw Test Result: Not run
 D3D7 Test Result: Not run
 D3D8 Test Result: Not run
 D3D9 Test Result: Not run

-------------
Sound Devices
-------------
            Description: Logitech USB Headset
 Default Sound Playback: Yes
 Default Voice Playback: Yes
            Hardware ID: USB\Vid_046d&Pid_0a01&Rev_1013&MI_00
        Manufacturer ID: 65535
             Product ID: 65535
                   Type: WDM
            Driver Name: usbaudio.sys
         Driver Version: 5.01.2600.2180 (English)
      Driver Attributes: Final Retail
            WHQL Logo'd: Yes
          Date and Size: 8/3/2004 23:07:56, 59264 bytes
            Other Files: 
        Driver Provider: Microsoft
         HW Accel Level: Full
              Cap Flags: 0xF5F
    Min/Max Sample Rate: 100, 200000
Static/Strm HW Mix Bufs: 0, 0
 Static/Strm HW 3D Bufs: 0, 0
              HW Memory: 0
       Voice Management: No
 EAX(tm) 2.0 Listen/Src: No, No
   I3DL2(tm) Listen/Src: No, No
Sensaura(tm) ZoomFX(tm): No
               Registry: OK
      Sound Test Result: Not run

            Description: SB Audigy 2 Audio [CCC0]
 Default Sound Playback: No
 Default Voice Playback: No
            Hardware ID: PCI\VEN_1102&DEV_0004&SUBSYS_10021102&REV_04
        Manufacturer ID: 1
             Product ID: 100
                   Type: WDM
            Driver Name: ctaud2k.sys
         Driver Version: 5.12.0001.0444 (English)
      Driver Attributes: Final Retail
            WHQL Logo'd: Yes
          Date and Size: 10/18/2004 15:21:24, 371376 bytes
            Other Files: 
        Driver Provider: Creative
         HW Accel Level: Full
              Cap Flags: 0xF5F
    Min/Max Sample Rate: 4000, 192000
Static/Strm HW Mix Bufs: 64, 62
 Static/Strm HW 3D Bufs: 64, 62
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
            Description: Logitech USB Headset
  Default Sound Capture: Yes
  Default Voice Capture: Yes
            Driver Name: usbaudio.sys
         Driver Version: 5.01.2600.2180 (English)
      Driver Attributes: Final Retail
          Date and Size: 8/3/2004 23:07:56, 59264 bytes
              Cap Flags: 0x41
           Format Flags: 0x444

            Description: SB Audigy 2 Audio [CCC0]
  Default Sound Capture: No
  Default Voice Capture: No
            Driver Name: ctaud2k.sys
         Driver Version: 5.12.0001.0444 (English)
      Driver Attributes: Final Retail
          Date and Size: 10/18/2004 15:21:24, 371376 bytes
              Cap Flags: 0x41
           Format Flags: 0xFFF

-----------
DirectMusic
-----------
        DLS Path: C:\WINDOWS\SYSTEM32\drivers\GM.DLS
     DLS Version: 1.00.0016.0002
    Acceleration: n/a
           Ports: Microsoft Synthesizer, Software (Not Kernel Mode), Output, DLS, Internal, Default Port
                  SB Audigy 2 DirectMusic Synthesizer [CCC0], Hardware (Kernel Mode), Output, DLS, Internal
                  SB Audigy 2 Audio [CCC0], Software (Kernel Mode), Output, DLS, Internal
                  USB Audio Device, Software (Kernel Mode), Output, DLS, Internal
                  Microsoft MIDI Mapper [Emulated], Hardware (Not Kernel Mode), Output, No DLS, Internal
                  SB Audigy 2 Synth A [CCC0] [Emulated], Hardware (Not Kernel Mode), Output, No DLS, Internal
                  SB Audigy 2 Sw Synth [CCC0] [Emulated], Hardware (Not Kernel Mode), Output, No DLS, Internal
                  SB Audigy 2 Synth B [CCC0] [Emulated], Hardware (Not Kernel Mode), Output, No DLS, Internal
                  SB Audigy 2 MIDI IO [CCC0] [Emulated], Hardware (Not Kernel Mode), Output, No DLS, External
                  Microsoft GS Wavetable SW Synth [Emulated], Hardware (Not Kernel Mode), Output, No DLS, Internal
                  SB Audigy 2 MIDI IO [CCC0] [Emulated], Hardware (Not Kernel Mode), Input, No DLS, External
        Registry: OK
     Test Result: Not run

-------------------
DirectInput Devices
-------------------
      Device Name: Mouse
         Attached: 1
    Controller ID: n/a
Vendor/Product ID: n/a
        FF Driver: n/a

      Device Name: Keyboard
         Attached: 1
    Controller ID: n/a
Vendor/Product ID: n/a
        FF Driver: n/a

Poll w/ Interrupt: No
         Registry: OK

-----------
USB Devices
-----------
+ USB Root Hub
| Vendor/Product ID: 0x8086, 0x265A
| Matching Device ID: usb\root_hub
| Service: usbhub
| Driver: usbhub.sys, 8/4/2004 00:08:44, 57600 bytes
| Driver: usbd.sys, 8/4/2004 06:00:00, 4736 bytes
| 
+-+ Logitech USB WingMan Gaming Mouse
| | Vendor/Product ID: 0x046D, 0xC004
| | Location: USB-PS/2 Mouse
| | Matching Device ID: usb\vid_046d&pid_c004
| | Service: HidUsb
| | Driver: hidclass.sys, 8/3/2004 23:08:20, 36224 bytes
| | Driver: hidparse.sys, 8/3/2004 23:08:18, 24960 bytes
| | Driver: hid.dll, 8/4/2004 06:00:00, 20992 bytes
| | Driver: hidusb.sys, 8/17/2001 14:02:20, 9600 bytes
| | 
| +-+ HID-compliant WingMan Gaming Mouse
| | | Vendor/Product ID: 0x046D, 0xC004
| | | Matching Device ID: hid\vid_046d&pid_c004
| | | Upper Filters: LMouFlt2
| | | Lower Filters: LHidFlt2
| | | Service: mouhid
| | | Driver: mouhid.sys, 8/17/2001 13:48:00, 12160 bytes
| | | Driver: mouclass.sys, 8/3/2004 22:58:34, 23040 bytes
| | | Driver: LHidFlt2.Sys, 12/17/2003 09:50:00, 25505 bytes
| | | Driver: LMouFlt2.Sys, 12/17/2003 09:50:00, 70801 bytes
| | | Driver: Logi_MwX.Exe, 12/17/2003 09:50:00, 19968 bytes

----------------
Gameport Devices
----------------
+ Intel(R) 82801 PCI Bridge - 244E
| Location: PCI bus 0, device 30, function 0
| Matching Device ID: pci\ven_8086&dev_244e
| Service: pci
| Driver: pci.sys, 8/4/2004 00:07:48, 68224 bytes
| 
+-+ Creative Game Port
| | Location: PCI bus 4, device 1, function 1
| | Matching Device ID: pci\ven_1102&dev_7003&subsys_00601102
| | Service: ctgame
| | Driver: ctgame.sys, 12/30/2002 10:53:36, 12160 bytes

------------
PS/2 Devices
------------
+ Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
| Matching Device ID: *pnp0303
| Service: i8042prt
| Driver: i8042prt.sys, 8/3/2004 23:14:38, 52736 bytes
| Driver: kbdclass.sys, 8/3/2004 22:58:34, 24576 bytes
| 
+ Terminal Server Keyboard Driver
| Matching Device ID: root\rdp_kbd
| Upper Filters: kbdclass
| Service: TermDD
| Driver: termdd.sys, 8/4/2004 02:01:08, 40840 bytes
| Driver: kbdclass.sys, 8/3/2004 22:58:34, 24576 bytes
| 
+ Terminal Server Mouse Driver
| Matching Device ID: root\rdp_mou
| Upper Filters: mouclass
| Service: TermDD
| Driver: termdd.sys, 8/4/2004 02:01:08, 40840 bytes
| Driver: mouclass.sys, 8/3/2004 22:58:34, 23040 bytes

----------------------------
DirectPlay Service Providers
----------------------------
DirectPlay8 Modem Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.2180)
DirectPlay8 Serial Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.2180)
DirectPlay8 IPX Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.2180)
DirectPlay8 TCP/IP Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.2180)
Internet TCP/IP Connection For DirectPlay - Registry: OK, File: dpwsockx.dll (5.03.2600.2180)
IPX Connection For DirectPlay - Registry: OK, File: dpwsockx.dll (5.03.2600.2180)
Modem Connection For DirectPlay - Registry: OK, File: dpmodemx.dll (5.03.2600.2180)
Serial Connection For DirectPlay - Registry: OK, File: dpmodemx.dll (5.03.2600.2180)

DirectPlay Voice Wizard Tests: Full Duplex: Passed, Half Duplex: Passed, Mic: Passed
DirectPlay Test Result: Not run
Registry: OK

-------------------
DirectPlay Adapters
-------------------
DirectPlay8 Serial Service Provider: COM1
DirectPlay8 TCP/IP Service Provider: Local Area Connection 2 - IPv4 - 

-----------------------
DirectPlay Voice Codecs
-----------------------
Voxware VR12 1.4kbit/s
Voxware SC06 6.4kbit/s
Voxware SC03 3.2kbit/s
MS-PCM 64 kbit/s
MS-ADPCM 32.8 kbit/s
Microsoft GSM 6.10 13 kbit/s
TrueSpeech(TM) 8.6 kbit/s

-------------------------
DirectPlay Lobbyable Apps
-------------------------

------------------------
Disk & DVD/CD-ROM Drives
------------------------
      Drive: C:
 Free Space: 63.0 GB
Total Space: 149.7 GB
File System: NTFS
      Model: ST3160023AS

      Drive: D:
      Model: _NEC DVD+-RW ND-3450A
     Driver: c:\windows\system32\drivers\cdrom.sys, 5.01.2600.2180 (English), 8/4/2004 06:00:00, 49536 bytes

      Drive: E:
      Model: JLMS DVD-ROM XJ-HD166
     Driver: c:\windows\system32\drivers\cdrom.sys, 5.01.2600.2180 (English), 8/4/2004 06:00:00, 49536 bytes

---

### Post by Heous on 2007-03-07
--------------
System Devices
--------------
     Name: Intel(R) 82801FB/FBM Ultra ATA Storage Controllers - 266F
Device ID: PCI\VEN_8086&DEV_266F&SUBSYS_01771028&REV_03\3&172E68DD&0&F9
   Driver: C:\WINDOWS\system32\DRIVERS\pciide.sys, 5.01.2600.0000 (English), 8/17/2001 14:51:52, 3328 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\pciidex.sys, 5.01.2600.2180 (English), 8/3/2004 23:59:42, 25088 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\atapi.sys, 5.01.2600.2180 (English), 8/3/2004 23:59:44, 95360 bytes

     Name: Intel(R) 82801FB/FBM SMBus Controller - 266A
Device ID: PCI\VEN_8086&DEV_266A&SUBSYS_01771028&REV_03\3&172E68DD&0&FB
   Driver: n/a

     Name: Intel(R) 82801FB/FBM PCI Express Root Port - 2662
Device ID: PCI\VEN_8086&DEV_2662&SUBSYS_00000000&REV_03\3&172E68DD&0&E1
   Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.2180 (English), 8/4/2004 00:07:48, 68224 bytes

     Name: Intel(R) 82801FB/FBM PCI Express Root Port - 2660
Device ID: PCI\VEN_8086&DEV_2660&SUBSYS_00000000&REV_03\3&172E68DD&0&E0
   Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.2180 (English), 8/4/2004 00:07:48, 68224 bytes

     Name: Intel(R) 82801FB/FBM USB2 Enhanced Host Controller - 265C
Device ID: PCI\VEN_8086&DEV_265C&SUBSYS_01771028&REV_03\3&172E68DD&0&EF
   Driver: C:\WINDOWS\system32\drivers\usbehci.sys, 5.01.2600.2180 (English), 8/4/2004 06:00:00, 26624 bytes
   Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.2180 (English), 8/4/2004 00:08:44, 142976 bytes
   Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.2180 (English), 8/4/2004 01:56:48, 74240 bytes
   Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.2180 (English), 8/4/2004 00:08:44, 57600 bytes
   Driver: C:\WINDOWS\system32\hccoin.dll, 5.01.2600.2180 (English), 8/4/2004 06:00:00, 7168 bytes

     Name: Intel(R) 82801FB/FBM USB Universal Host Controller - 265B
Device ID: PCI\VEN_8086&DEV_265B&SUBSYS_01771028&REV_03\3&172E68DD&0&EB
   Driver: C:\WINDOWS\system32\drivers\usbuhci.sys, 5.01.2600.2180 (English), 8/4/2004 00:08:38, 20480 bytes
   Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.2180 (English), 8/4/2004 00:08:44, 142976 bytes
   Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.2180 (English), 8/4/2004 01:56:48, 74240 bytes
   Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.2180 (English), 8/4/2004 00:08:44, 57600 bytes

     Name: Intel(R) 82801FB/FBM USB Universal Host Controller - 265A
Device ID: PCI\VEN_8086&DEV_265A&SUBSYS_01771028&REV_03\3&172E68DD&0&EA
   Driver: C:\WINDOWS\system32\drivers\usbuhci.sys, 5.01.2600.2180 (English), 8/4/2004 00:08:38, 20480 bytes
   Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.2180 (English), 8/4/2004 00:08:44, 142976 bytes
   Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.2180 (English), 8/4/2004 01:56:48, 74240 bytes
   Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.2180 (English), 8/4/2004 00:08:44, 57600 bytes

     Name: Intel(R) 82801FB/FBM USB Universal Host Controller - 2659
Device ID: PCI\VEN_8086&DEV_2659&SUBSYS_01771028&REV_03\3&172E68DD&0&E9
   Driver: C:\WINDOWS\system32\drivers\usbuhci.sys, 5.01.2600.2180 (English), 8/4/2004 00:08:38, 20480 bytes
   Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.2180 (English), 8/4/2004 00:08:44, 142976 bytes
   Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.2180 (English), 8/4/2004 01:56:48, 74240 bytes
   Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.2180 (English), 8/4/2004 00:08:44, 57600 bytes

     Name: Intel(R) 82801FB/FBM USB Universal Host Controller - 2658
Device ID: PCI\VEN_8086&DEV_2658&SUBSYS_01771028&REV_03\3&172E68DD&0&E8
   Driver: C:\WINDOWS\system32\drivers\usbuhci.sys, 5.01.2600.2180 (English), 8/4/2004 00:08:38, 20480 bytes
   Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.2180 (English), 8/4/2004 00:08:44, 142976 bytes
   Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.2180 (English), 8/4/2004 01:56:48, 74240 bytes
   Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.2180 (English), 8/4/2004 00:08:44, 57600 bytes

     Name: Intel(R) 82801FR SATA AHCI Controller
Device ID: PCI\VEN_8086&DEV_2652&SUBSYS_01771028&REV_03\3&172E68DD&0&FA
   Driver: C:\WINDOWS\system32\DRIVERS\iaStor.sys, 4.05.0000.6515 (English), 6/29/2004 12:17:16, 477952 bytes

     Name: Intel(R) 82801FB LPC Interface Controller - 2640
Device ID: PCI\VEN_8086&DEV_2640&SUBSYS_00000000&REV_03\3&172E68DD&0&F8
   Driver: C:\WINDOWS\system32\DRIVERS\isapnp.sys, 5.01.2600.0000 (English), 8/17/2001 14:58:02, 35840 bytes

     Name: Intel(R) 925X PCI Express Root Port - 2585
Device ID: PCI\VEN_8086&DEV_2585&SUBSYS_00000000&REV_04\3&172E68DD&0&08
   Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.2180 (English), 8/4/2004 00:07:48, 68224 bytes

     Name: Intel(R) 925X Memory Controller Hub - 2584
Device ID: PCI\VEN_8086&DEV_2584&SUBSYS_00000000&REV_04\3&172E68DD&0&00
   Driver: n/a

     Name: Intel(R) 82801 PCI Bridge - 244E
Device ID: PCI\VEN_8086&DEV_244E&SUBSYS_00000000&REV_D3\3&172E68DD&0&F0
   Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.2180 (English), 8/4/2004 00:07:48, 68224 bytes

     Name: Broadcom NetXtreme 57xx Gigabit Controller
Device ID: PCI\VEN_14E4&DEV_1677&SUBSYS_01771028&REV_01\4&1D7EFF9E&0&00E0
   Driver: C:\WINDOWS\system32\DRIVERS\b57xp32.sys, 7.73.0000.0000 (English), 5/29/2004 18:41:54, 186112 bytes

     Name: Creative Game Port
Device ID: PCI\VEN_1102&DEV_7003&SUBSYS_00601102&REV_04\4&10416D21&0&09F0
   Driver: C:\WINDOWS\system32\DRIVERS\ctgame.sys, 5.12.0002.0100 (English), 12/30/2002 10:53:36, 12160 bytes

     Name: OHCI Compliant IEEE 1394 Host Controller
Device ID: PCI\VEN_1102&DEV_4001&SUBSYS_00101102&REV_04\4&10416D21&0&0AF0
   Driver: C:\WINDOWS\system32\DRIVERS\ohci1394.sys, 5.01.2600.2180 (English), 8/3/2004 23:10:10, 61056 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\1394bus.sys, 5.01.2600.2180 (English), 8/3/2004 23:10:08, 53248 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\nic1394.sys, 5.01.2600.2180 (English), 8/4/2004 06:00:00, 61824 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\arp1394.sys, 5.01.2600.2180 (English), 8/4/2004 06:00:00, 60800 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\enum1394.sys, 5.01.2600.0000 (English), 8/17/2001 13:46:40, 6400 bytes

     Name: Creative SB Audigy 2 (WDM)
Device ID: PCI\VEN_1102&DEV_0004&SUBSYS_10021102&REV_04\4&10416D21&0&08F0
   Driver: C:\WINDOWS\system32\ksuser.dll, 5.03.2600.2180 (English), 8/4/2004 00:56:44, 4096 bytes
   Driver: C:\WINDOWS\system32\ksproxy.ax, 5.03.2600.2180 (English), 8/4/2004 00:56:58, 130048 bytes
   Driver: C:\WINDOWS\system32\drivers\ks.sys, 5.03.2600.2180 (English), 8/3/2004 23:15:22, 140928 bytes
   Driver: C:\WINDOWS\system32\drivers\drmk.sys, 5.01.2600.2180 (English), 8/3/2004 23:08:00, 60288 bytes
   Driver: C:\WINDOWS\system32\drivers\portcls.sys, 5.01.2600.2180 (English), 8/3/2004 23:15:50, 145792 bytes
   Driver: C:\WINDOWS\system32\drivers\stream.sys, 5.03.2600.2180 (English), 8/3/2004 23:08:04, 48640 bytes
   Driver: C:\WINDOWS\system32\wdmaud.drv, 5.01.2600.2180 (English), 8/4/2004 00:56:58, 23552 bytes
   Driver: C:\WINDOWS\system32\drivers\ctac32k.sys, 5.12.0001.0444 (English), 2/23/2004 15:16:12, 645360 bytes
   Driver: C:\WINDOWS\system32\drivers\ctaud2k.sys, 5.12.0001.0444 (English), 10/18/2004 15:21:24, 371376 bytes
   Driver: C:\WINDOWS\system32\drivers\ctoss2k.sys, 5.12.0001.0441 (English), 10/8/2003 10:06:50, 178672 bytes
   Driver: C:\WINDOWS\system32\drivers\ctprxy2k.sys, 5.12.0001.0441 (English), 10/8/2003 10:08:12, 6096 bytes
   Driver: C:\WINDOWS\system32\drivers\ctsfm2k.sys, 5.12.0001.0441 (English), 10/8/2003 10:09:10, 130288 bytes
   Driver: C:\WINDOWS\system32\drivers\emupia2k.sys, 5.12.0001.0442 (English), 10/13/2003 17:42:12, 145488 bytes
   Driver: C:\WINDOWS\system32\drivers\ha10kx2k.sys, 5.12.0001.0446 (English), 2/24/2004 12:17:10, 904784 bytes
   Driver: C:\WINDOWS\system32\drivers\haP16v2k.sys, 5.12.0001.0442 (English), 10/21/2003 17:23:44, 148432 bytes
   Driver: C:\WINDOWS\system32\drivers\pfmodnt.sys, 3.00.0000.0003 (English), 3/5/2003 15:07:46, 15840 bytes
   Driver: C:\WINDOWS\system32\ctdlang.dat, 10/21/2003 17:54:50, 217272 bytes
   Driver: C:\WINDOWS\system32\ctstatic.dat, 10/21/2003 17:47:40, 298971 bytes
   Driver: C:\WINDOWS\system32\ctdaught.dat, 10/21/2003 17:47:34, 53932 bytes
   Driver: C:\WINDOWS\system32\a3d.dll, 80.00.0000.0003 (English), 10/6/2003 14:38:06, 65536 bytes
   Driver: C:\WINDOWS\system32\commonfx.dll, 5.12.0001.0440 (English), 10/6/2003 14:44:28, 114688 bytes
   Driver: C:\WINDOWS\system32\ctaudfx.dll, 5.12.0001.0442 (English), 2/18/2004 15:38:34, 585728 bytes
   Driver: C:\WINDOWS\system32\ctsblfx.dll, 5.12.0001.0440 (English), 10/6/2003 14:46:14, 606208 bytes
   Driver: C:\WINDOWS\system32\sfman32.dll, 5.12.0001.0130 (English), 8/17/2001 14:35:46, 36864 bytes
   Driver: C:\WINDOWS\system32\ctbas2w.dat, 10/21/2003 17:54:48, 140643 bytes
   Driver: C:\WINDOWS\system32\ctsbas2w.dat, 10/21/2003 17:54:42, 264466 bytes
   Driver: C:\WINDOWS\system32\SBAudigy.ico, 8/17/2001 12:42:28, 7406 bytes
   Driver: C:\WINDOWS\system32\Audigy.bmp, 11/13/2001 09:48:20, 1912 bytes
   Driver: C:\WINDOWS\system32\ctcoinst.dll, 3.00.0000.0005 (English), 2/23/2004 10:10:00, 73728 bytes
   Driver: C:\WINDOWS\system32\ctdvinst.dll, 1.82.0000.0001 (English), 6/27/2003 17:51:42, 122880 bytes
   Driver: C:\WINDOWS\system32\drivers\ctdvda2k.sys, 5.13.0001.0413 (English), 10/14/2003 11:17:56, 332800 bytes

     Name: Radeon X1800 Series Secondary
Device ID: PCI\VEN_1002&DEV_7120&SUBSYS_0B131002&REV_00\4&16EC1A1&0&0108
   Driver: C:\WINDOWS\system32\DRIVERS\ati2mtag.sys, 6.14.0010.6652 (English), 11/21/2006 22:25:08, 2829824 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ati2erec.dll, 1.00.0000.0009 (English), 11/21/2006 21:55:46, 49152 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ativvpxx.vp, 11/21/2006 22:59:55, 37920 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ativckxx.vp, 8/23/2006 17:26:56, 2096 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ativcaxx.vp, 8/23/2006 17:26:59, 929 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ativcaxx.cpa, 8/23/2006 17:26:59, 655842 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ativdkxx.vp, 8/23/2006 17:26:56, 2096 bytes
   Driver: C:\WINDOWS\system32\ati2dvag.dll, 6.14.0010.6652 (English), 11/21/2006 22:25:23, 261120 bytes
   Driver: C:\WINDOWS\system32\ati2cqag.dll, 6.14.0010.0322 (English), 11/21/2006 21:51:50, 294912 bytes
   Driver: C:\WINDOWS\system32\Ati2mdxx.exe, 6.14.0010.2495 (English), 11/21/2006 22:19:55, 26112 bytes
   Driver: C:\WINDOWS\system32\ati3duag.dll, 6.14.0010.0456 (English), 11/21/2006 22:12:27, 2526688 bytes
   Driver: C:\WINDOWS\system32\ativvaxx.dll, 6.14.0010.0130 (English), 11/21/2006 22:08:16, 1090016 bytes
   Driver: C:\WINDOWS\system32\atiicdxx.dat, 10/19/2006 10:16:05, 138101 bytes
   Driver: C:\WINDOWS\system32\ativvaxx.dat, 11/21/2006 22:07:59, 3107788 bytes
   Driver: C:\WINDOWS\system32\ATIDDC.DLL, 6.14.0010.0008 (English), 11/21/2006 22:17:58, 53248 bytes
   Driver: C:\WINDOWS\system32\atitvo32.dll, 6.14.0010.4200 (English), 11/21/2006 21:56:25, 17408 bytes
   Driver: C:\WINDOWS\system32\ativcoxx.dll, 6.13.0010.0005 (English), 11/9/2001 11:01:04, 24064 bytes
   Driver: C:\WINDOWS\system32\ati2evxx.exe, 6.14.0010.4152 (English), 11/21/2006 22:18:37, 430080 bytes
   Driver: C:\WINDOWS\system32\ati2evxx.dll, 6.14.0010.4152 (English), 11/21/2006 22:19:41, 90112 bytes
   Driver: C:\WINDOWS\system32\atipdlxx.dll, 6.14.0010.2513 (English), 11/21/2006 22:20:11, 118784 bytes
   Driver: C:\WINDOWS\system32\Oemdspif.dll, 6.14.0001.0019 (English), 11/21/2006 22:20:01, 106496 bytes
   Driver: C:\WINDOWS\system32\ati2edxx.dll, 6.14.0010.2509 (English), 11/21/2006 22:19:50, 42496 bytes
   Driver: C:\WINDOWS\system32\atikvmag.dll, 6.14.0010.0043 (English), 11/21/2006 21:57:31, 217088 bytes
   Driver: C:\WINDOWS\system32\ATIDEMGR.dll, 1.02.2516.38439 (English), 11/21/2006 21:21:19, 303104 bytes
   Driver: C:\WINDOWS\system32\atifglpf.xml, 10/17/2006 19:20:26, 6223 bytes
   Driver: C:\WINDOWS\system32\atioglxx.dll, 6.14.0010.6232 (English), 11/21/2006 22:11:19, 5279744 bytes
   Driver: C:\WINDOWS\system32\atioglx1.dll, 6.14.0010.1091 (English), 11/21/2006 21:50:55, 6684672 bytes
   Driver: C:\WINDOWS\system32\atiiiexx.dll, 6.14.0010.4004 (English), 11/21/2006 21:49:45, 307200 bytes

     Name: Radeon X1800 Series 
Device ID: PCI\VEN_1002&DEV_7100&SUBSYS_0B121002&REV_00\4&16EC1A1&0&0008
   Driver: C:\WINDOWS\system32\DRIVERS\ati2mtag.sys, 6.14.0010.6652 (English), 11/21/2006 22:25:08, 2829824 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ati2erec.dll, 1.00.0000.0009 (English), 11/21/2006 21:55:46, 49152 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ativvpxx.vp, 11/21/2006 22:59:55, 37920 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ativckxx.vp, 8/23/2006 17:26:56, 2096 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ativcaxx.vp, 8/23/2006 17:26:59, 929 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ativcaxx.cpa, 8/23/2006 17:26:59, 655842 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ativdkxx.vp, 8/23/2006 17:26:56, 2096 bytes
   Driver: C:\WINDOWS\system32\ati2dvag.dll, 6.14.0010.6652 (English), 11/21/2006 22:25:23, 261120 bytes
   Driver: C:\WINDOWS\system32\ati2cqag.dll, 6.14.0010.0322 (English), 11/21/2006 21:51:50, 294912 bytes
   Driver: C:\WINDOWS\system32\Ati2mdxx.exe, 6.14.0010.2495 (English), 11/21/2006 22:19:55, 26112 bytes
   Driver: C:\WINDOWS\system32\ati3duag.dll, 6.14.0010.0456 (English), 11/21/2006 22:12:27, 2526688 bytes
   Driver: C:\WINDOWS\system32\ativvaxx.dll, 6.14.0010.0130 (English), 11/21/2006 22:08:16, 1090016 bytes
   Driver: C:\WINDOWS\system32\atiicdxx.dat, 10/19/2006 10:16:05, 138101 bytes
   Driver: C:\WINDOWS\system32\ativvaxx.dat, 11/21/2006 22:07:59, 3107788 bytes
   Driver: C:\WINDOWS\system32\ATIDDC.DLL, 6.14.0010.0008 (English), 11/21/2006 22:17:58, 53248 bytes
   Driver: C:\WINDOWS\system32\atitvo32.dll, 6.14.0010.4200 (English), 11/21/2006 21:56:25, 17408 bytes
   Driver: C:\WINDOWS\system32\ativcoxx.dll, 6.13.0010.0005 (English), 11/9/2001 11:01:04, 24064 bytes
   Driver: C:\WINDOWS\system32\ati2evxx.exe, 6.14.0010.4152 (English), 11/21/2006 22:18:37, 430080 bytes
   Driver: C:\WINDOWS\system32\ati2evxx.dll, 6.14.0010.4152 (English), 11/21/2006 22:19:41, 90112 bytes
   Driver: C:\WINDOWS\system32\atipdlxx.dll, 6.14.0010.2513 (English), 11/21/2006 22:20:11, 118784 bytes
   Driver: C:\WINDOWS\system32\Oemdspif.dll, 6.14.0001.0019 (English), 11/21/2006 22:20:01, 106496 bytes
   Driver: C:\WINDOWS\system32\ati2edxx.dll, 6.14.0010.2509 (English), 11/21/2006 22:19:50, 42496 bytes
   Driver: C:\WINDOWS\system32\atikvmag.dll, 6.14.0010.0043 (English), 11/21/2006 21:57:31, 217088 bytes
   Driver: C:\WINDOWS\system32\ATIDEMGR.dll, 1.02.2516.38439 (English), 11/21/2006 21:21:19, 303104 bytes
   Driver: C:\WINDOWS\system32\atifglpf.xml, 10/17/2006 19:20:26, 6223 bytes
   Driver: C:\WINDOWS\system32\atioglxx.dll, 6.14.0010.6232 (English), 11/21/2006 22:11:19, 5279744 bytes
   Driver: C:\WINDOWS\system32\atioglx1.dll, 6.14.0010.1091 (English), 11/21/2006 21:50:55, 6684672 bytes
   Driver: C:\WINDOWS\system32\atiiiexx.dll, 6.14.0010.4004 (English), 11/21/2006 21:49:45, 307200 bytes

------------------
DirectX Components
------------------
   ddraw.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 266240 bytes
 ddrawex.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 27136 bytes
   dxapi.sys: 5.01.2600.0000 English Final Retail 8/4/2004 06:00:00 10496 bytes
    d3d8.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 1179648 bytes
 d3d8thk.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 8192 bytes
    d3d9.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 1689088 bytes
   d3dim.dll: 5.01.2600.0000 English Final Retail 8/4/2004 06:00:00 436224 bytes
d3dim700.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 825344 bytes
 d3dramp.dll: 5.01.2600.0000 English Final Retail 8/4/2004 06:00:00 590336 bytes
   d3drm.dll: 5.01.2600.0000 English Final Retail 8/4/2004 06:00:00 350208 bytes
  d3dxof.dll: 5.01.2600.0000 English Final Retail 8/4/2004 06:00:00 47616 bytes
d3dpmesh.dll: 5.01.2600.0000 English Final Retail 8/4/2004 06:00:00 34816 bytes
   dplay.dll: 5.00.2134.0001 English Final Retail 8/4/2004 06:00:00 33040 bytes
  dplayx.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 229888 bytes
dpmodemx.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 23552 bytes
 dpwsock.dll: 5.00.2134.0001 English Final Retail 8/4/2004 06:00:00 42768 bytes
dpwsockx.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 57344 bytes
dplaysvr.exe: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 30208 bytes
  dpnsvr.exe: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 18432 bytes
   dpnet.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 375296 bytes
dpnlobby.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 3584 bytes
 dpnaddr.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 3584 bytes
 dpvoice.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 212480 bytes
dpvsetup.exe: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 83456 bytes
  dpvvox.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 116736 bytes
  dpvacm.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 21504 bytes
dpnhpast.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 35328 bytes
dpnhupnp.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 60928 bytes
dpserial.dll: 5.00.2134.0001 English Final Retail 8/4/2004 06:00:00 53520 bytes
  dinput.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 159232 bytes
 dinput8.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 181760 bytes
   dimap.dll: 5.01.2600.0000 English Final Retail 8/4/2004 06:00:00 44032 bytes
diactfrm.dll: 5.01.2600.0000 English Final Retail 8/4/2004 06:00:00 394240 bytes
     joy.cpl: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 68608 bytes
   gcdef.dll: 5.01.2600.0000 English Final Retail 8/4/2004 06:00:00 76800 bytes
     pid.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 35328 bytes
  dsound.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 367616 bytes
dsound3d.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 1294336 bytes
  dswave.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 19456 bytes
   dsdmo.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 181760 bytes
dsdmoprp.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 71680 bytes
  dmusic.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 104448 bytes
  dmband.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 28672 bytes
dmcompos.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 61440 bytes
   dmime.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 181248 bytes
dmloader.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 35840 bytes
 dmstyle.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 105984 bytes
 dmsynth.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 103424 bytes
dmscript.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 82432 bytes
  system.dll: 1.01.4322.2032 English Final Retail 8/10/2004 14:11:14 1224704 bytes
Microsoft.DirectX.Direct3D.dll: 9.05.0132.0000 English Final Retail 1/1/2007 23:01:42 473600 bytes
Microsoft.DirectX.Direct3D.dll: 5.03.0000.0900 English Final Retail 5/28/2005 12:45:13 274432 bytes
Microsoft.DirectX.Direct3DX.dll: 5.04.0000.3900 English Final Retail 1/1/2007 15:47:11 2676224 bytes
Microsoft.DirectX.Direct3DX.dll: 9.04.0091.0000 English Final Retail 1/1/2007 15:47:12 2846720 bytes
Microsoft.DirectX.Direct3DX.dll: 9.05.0132.0000 English Final Retail 1/1/2007 15:47:12 563712 bytes
Microsoft.DirectX.Direct3DX.dll: 9.06.0168.0000 English Final Retail 1/1/2007 23:01:42 567296 bytes
Microsoft.DirectX.Direct3DX.dll: 9.07.0239.0000 English Final Retail 1/1/2007 15:47:12 576000 bytes
Microsoft.DirectX.Direct3DX.dll: 9.08.0299.0000 English Final Retail 1/1/2007 15:47:12 577024 bytes
Microsoft.DirectX.Direct3DX.dll: 9.09.0376.0000 English Final Retail 1/1/2007 15:47:13 577536 bytes
Microsoft.DirectX.Direct3DX.dll: 9.10.0455.0000 English Final Retail 1/1/2007 15:47:13 577536 bytes
Microsoft.DirectX.Direct3DX.dll: 9.11.0519.0000 English Final Retail 1/1/2007 15:47:14 578560 bytes
Microsoft.DirectX.Direct3DX.dll: 9.12.0589.0000 English Final Retail 10/7/2006 14:40:43 578560 bytes
Microsoft.DirectX.Direct3DX.dll: 5.03.0000.0900 English Final Retail 5/28/2005 12:45:13 1701376 bytes
Microsoft.DirectX.DirectDraw.dll: 5.04.0000.2904 English Final Retail 1/1/2007 23:01:42 145920 bytes
Microsoft.DirectX.DirectDraw.dll: 5.03.0000.0900 English Final Retail 5/28/2005 12:45:13 133120 bytes
Microsoft.DirectX.DirectInput.dll: 5.04.0000.2904 English Final Retail 1/1/2007 23:01:42 159232 bytes
Microsoft.DirectX.DirectInput.dll: 5.03.0000.0900 English Final Retail 5/28/2005 12:45:13 141824 bytes
Microsoft.DirectX.DirectPlay.dll: 5.04.0000.2904 English Final Retail 1/1/2007 23:01:42 364544 bytes
Microsoft.DirectX.DirectPlay.dll: 5.03.0000.0900 English Final Retail 5/28/2005 12:45:13 237056 bytes
Microsoft.DirectX.DirectSound.dll: 5.04.0000.2904 English Final Retail 1/1/2007 23:01:42 178176 bytes
Microsoft.DirectX.DirectSound.dll: 5.03.0000.0900 English Final Retail 5/28/2005 12:45:13 138752 bytes
Microsoft.DirectX.AudioVideoPlayback.dll: 5.04.0000.2904 English Final Retail 1/1/2007 23:01:42 53248 bytes
Microsoft.DirectX.AudioVideoPlayback.dll: 5.03.0000.0900 English Final Retail 5/28/2005 12:45:13 43520 bytes
Microsoft.DirectX.Diagnostics.dll: 5.04.0000.2904 English Final Retail 1/1/2007 23:01:42 12800 bytes
Microsoft.DirectX.Diagnostics.dll: 5.03.0000.0900 English Final Retail 5/28/2005 12:45:13 13824 bytes
Microsoft.DirectX.dll: 5.04.0000.2904 English Final Retail 1/1/2007 23:01:42 223232 bytes
Microsoft.DirectX.dll: 5.03.0000.0900 English Final Retail 5/28/2005 12:45:13 202752 bytes
   dx7vb.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 619008 bytes
   dx8vb.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 1227264 bytes
 dxdiagn.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 2113536 bytes
 directx.cpl: 5.04.0000.3900 English Final Retail 9/30/2004 10:17:14 135168 bytes
   mfc40.dll: 4.01.0000.6140 English Final Retail 8/4/2004 06:00:00 924432 bytes
   mfc42.dll: 6.02.4131.0000 English Final Retail 8/4/2004 06:00:00 1028096 bytes
 wsock32.dll: 5.01.2600.2180 English Final Retail 8/4/2004 06:00:00 22528 bytes
amstream.dll: 6.05.2600.2180 English Final Retail 8/4/2004 06:00:00 70656 bytes
 devenum.dll: 6.05.2600.2180 English Final Retail 8/4/2004 06:00:00 59904 bytes
  dxmasf.dll: 6.04.0009.1133 English Final Retail 8/22/2006 04:05:26 498742 bytes
mciqtz32.dll: 6.05.2600.2180 English Final Retail 8/4/2004 06:00:00 35328 bytes
 mpg2splt.ax: 6.05.2600.2180 English Final Retail 8/4/2004 06:00:00 148992 bytes
   msdmo.dll: 6.05.2600.2180 English Final Retail 8/4/2004 06:00:00 14336 bytes
  encapi.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 20480 bytes
    qasf.dll: 11.00.5721.5145 English Final Retail 10/18/2006 21:47:18 211456 bytes
    qcap.dll: 6.05.2600.2180 English Final Retail 8/4/2004 06:00:00 192512 bytes
     qdv.dll: 6.05.2600.2180 English Final Retail 8/4/2004 06:00:00 279040 bytes
    qdvd.dll: 6.05.2600.2180 English Final Retail 8/4/2004 06:00:00 385024 bytes
   qedit.dll: 6.05.2600.2180 English Final Retail 8/4/2004 06:00:00 562176 bytes
qedwipes.dll: 6.05.2600.2180 English Final Retail 8/4/2004 06:00:00 733696 bytes
  quartz.dll: 6.05.2600.2749 English Final Retail 8/29/2005 22:54:26 1287168 bytes
 strmdll.dll: 4.01.0000.3936 English Final Retail 8/21/2006 09:52:08 246814 bytes
 iac25_32.ax: 2.00.0005.0053 English Final Retail 8/4/2004 06:00:00 199680 bytes
  ir41_32.ax: 4.51.0016.0003 English Final Retail 8/4/2004 06:00:00 848384 bytes
 ir41_qc.dll: 4.30.0062.0002 English Final Retail 8/4/2004 06:00:00 120320 bytes
ir41_qcx.dll: 4.30.0064.0001 English Final Retail 8/4/2004 06:00:00 338432 bytes
 ir50_32.dll: 5.2562.0015.0055 English Final Retail 8/4/2004 06:00:00 755200 bytes
 ir50_qc.dll: 5.00.0063.0048 English Final Retail 8/4/2004 06:00:00 200192 bytes
ir50_qcx.dll: 5.00.0064.0048 English Final Retail 8/4/2004 06:00:00 183808 bytes
   ivfsrc.ax: 5.10.0002.0051 English Final Retail 8/4/2004 06:00:00 154624 bytes
mswebdvd.dll: 6.05.2600.2180 English Final Retail 8/4/2004 06:00:00 204288 bytes
      ks.sys: 5.03.2600.2180 English Final Retail 8/3/2004 23:15:22 140928 bytes
  ksproxy.ax: 5.03.2600.2180 English Final Retail 8/4/2004 00:56:58 130048 bytes
  ksuser.dll: 5.03.2600.2180 English Final Retail 8/4/2004 00:56:44 4096 bytes
  stream.sys: 5.03.2600.2180 English Final Retail 8/3/2004 23:08:04 48640 bytes
mspclock.sys: 5.03.2600.2180 English Final Retail 8/3/2004 23:58:40 5376 bytes
   mspqm.sys: 5.01.2600.2180 English Final Retail 8/3/2004 23:58:42 4992 bytes
 mskssrv.sys: 5.03.2600.2180 English Final Retail 8/3/2004 23:58:42 7552 bytes
  swenum.sys: 5.03.2600.2180 English Final Retail 8/3/2004 23:58:42 4352 bytes
mpeg2data.ax: 6.05.2600.2180 English Final Retail 8/4/2004 06:00:00 118272 bytes
msvidctl.dll: 6.05.2600.2180 English Final Retail 8/4/2004 06:00:00 1428480 bytes
  vbisurf.ax: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 30720 bytes
   msyuv.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 17408 bytes
wstdecod.dll: 5.03.2600.2180 English Final Retail 8/4/2004 06:00:00 50688 bytes

---

### Post by Heous on 2007-03-07
------------------
DirectShow Filters
------------------

DirectShow Filters:
WMAudio Decoder DMO,0x00800800,1,1,,
WMAPro over S/PDIF DMO,0x00600800,1,1,,
WMA Voice Decoder DMO,0x00600800,1,1,,
WMVideo Advanced Decoder DMO,0x00800001,1,1,,
Mpeg4s Decoder DMO,0x00800001,1,1,,
WMV Screen decoder DMO,0x00800001,1,1,,
WMVideo Decoder DMO,0x00800001,1,1,,
Mpeg43 Decoder DMO,0x00800001,1,1,,
Mpeg4 Decoder DMO,0x00800001,1,1,,
Annodex Mux Filter,0x00200000,1,0,dsfAnxMux.dll,
CMML Decode Filter,0x00800002,1,1,dsfCMMLDecoder.dll,
CMML Raw Source Filter,0x00600000,0,0,dsfCMMLRawSource.dll,
FLAC Decode Filter,0x00600000,1,1,dsfFLACDecoder.dll,
FLAC Encode Filter,0x00200000,1,1,dsfFLACEncoder.dll,
Native FLAC Source Filter,0x00600000,0,0,dsfNativeFLACSource.dll,
Ogg Demux Packet Source Filter,0x00600000,0,0,dsfOggDemux2.dll,
Ogg Mux Filter,0x00200000,1,0,dsfOggMux.dll,
OGM Decode Filter,0x00600000,1,1,dsfOGMDecoder.dll,
Speex Decode Filter,0x00600000,1,1,dsfSpeexDecoder.dll,
Speex Encode Filter,0x00200000,1,1,dsfSpeexEncoder.dll,
Subtitle VMR9 Filter,0x00800002,1,1,dsfSubtitleVMR9.dll,
Theora Decode Filter,0x00600000,1,1,dsfTheoraDecoder.dll,
Theora Encode Filter,0x00200000,1,1,dsfTheoraEncoder.dll,
Vorbis Decode Filter,0x00600000,1,1,dsfVorbisDecoder.dll,
Vorbis Encode Filter,0x00200000,1,1,dsfVorbisEncoder.dll,
Sonic Scaler,0x00200000,1,1,SonicDSScaler.ax,1.00.0000.0001
WMT MuxDeMux Filter,0x00200000,0,0,wmm2filt.dll,2.01.4026.0000
Sonic TimeStampSmoother Filter,0x00000000,0,0,,
Creative LiveRecording Filter,0x00400000,0,1,LiveRec.ax,1.02.0001.0000
Full Screen Renderer,0x00200000,1,0,quartz.dll,6.05.2600.2749
WAV Dest Trial,0x00200000,0,0,WavD2Try.dll,1.01.0000.3463
MainConcept (Sonic) DV Video Decoder,0x00600000,1,1,sonicmcdsdv.ax,2.01.0000.0004
MainConcept (Sonic) DV Video Encoder,0x00200000,1,1,sonicmcdsdv.ax,2.01.0000.0004
Creative Wave Writer,0x00200000,1,0,WavWrite.ax,1.02.0012.0000
DV Muxer,0x00400000,0,0,qdv.dll,6.05.2600.2180
Creative MLP Source Filter,0x00400000,0,1,MlpSrc.ax,1.01.0001.0000
Color Space Converter,0x00400001,1,1,quartz.dll,6.05.2600.2749
WM ASF Reader,0x00400000,0,0,qasf.dll,11.00.5721.5145
Creative NVF Filter,0x00400000,0,1,NvfSrc.ax,1.00.0006.0000
Screen Capture filter,0x00200000,0,1,wmpsrcwp.dll,11.00.5721.5145
AVI Splitter,0x00600000,1,1,quartz.dll,6.05.2600.2749
WMT AudioAnalyzer,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
VGA 16 Color Ditherer,0x00400000,1,1,quartz.dll,6.05.2600.2749
Indeo® video 5.10 Compression Filter,0x00200000,1,1,ir50_32.dll,5.2562.0015.0055
Windows Media Audio Decoder,0x00800001,1,1,msadds32.ax,8.00.0000.4487
Photo Story 2 Trial Source Filter,0x00200000,0,1,PSSF2Try.dll,1.01.0000.3463
Sonic DirectShow Tap,0x00200000,1,1,DirectShowTap.ax,1.00.0000.0000
AC3 Parser Filter,0x00600000,1,1,mpg2splt.ax,6.05.2600.2180
CT Null Render Filter,0x00200000,1,0,NullRndr.ax,1.00.0001.0000
WMT Format Conversion,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
CT Time-Scaling filter,0x00100000,1,1,TimeScal.ax,2.00.0000.0001
StreamBufferSink,0x00200000,0,0,sbe.dll,6.05.2600.2180
WMT Black Frame Generator,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
MJPEG Decompressor,0x00600000,1,1,quartz.dll,6.05.2600.2749
Indeo® video 5.10 Decompression Filter,0x00640000,1,1,ir50_32.dll,5.2562.0015.0055
WMT Screen Capture filter,0x00200000,0,1,wmm2filt.dll,2.01.4026.0000
SVM Metadata,0x001fffff,1,1,Metasvm.ax,1.00.0000.0001
Microsoft Screen Video Decompressor,0x00800000,1,1,msscds32.ax,8.00.0000.4487
MPEG-I Stream Splitter,0x00600000,1,2,quartz.dll,6.05.2600.2749
SAMI (CC) Parser,0x00400000,1,1,quartz.dll,6.05.2600.2749
MPEG Layer-3 Decoder,0x00810000,1,1,l3codecx.ax,1.05.0000.0050
MPEG-2 Splitter,0x005fffff,1,0,mpg2splt.ax,6.05.2600.2180
Sonic MPEG Audio Decoder,0x00200000,1,1,SonicMPEGAudio.DLL,2.05.0004.1406
ACELP.net Sipro Lab Audio Decoder,0x00800001,1,1,acelpdec.ax,1.04.0000.0000
RTStreamSink,0x00200000,1,0,RTStreamSink.ax,1.00.0000.0000
WMS Filter,0x00400000,0,1,CTWMSFLT.DLL,1.12.0001.0000
Internal Script Command Renderer,0x00800001,1,0,quartz.dll,6.05.2600.2749
MPEG Audio Decoder,0x03680001,1,1,quartz.dll,6.05.2600.2749
File Source (Netshow URL),0x00400000,0,1,wmpasf.dll,11.00.5721.5145
WMT Import Filter,0x00200000,0,1,wmm2filt.dll,2.01.4026.0000
DV Splitter,0x00600000,1,2,qdv.dll,6.05.2600.2180
Bitmap Generate,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Windows Media Video Decoder,0x00800000,1,1,wmvds32.ax,8.00.0000.4487
Sonic Field Switch,0x00200000,1,1,FieldSwitch.ax,1.00.0000.0000
Video Mixing Renderer 9,0x00200000,1,0,quartz.dll,6.05.2600.2749
Windows Media Video Decoder,0x00800000,1,1,wmv8ds32.ax,8.00.0000.4000
Sonic RT Stream Source Filter,0x00400000,0,1,RTStreamSourceFilter.ax,1.03.0000.0001
WMT VIH2 Fix,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Sonic DVD LPCM Converter,0x00600000,1,1,DVDLPCMConverter.ax,1.00.0000.0000
Record Queue,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Creative MP3 Source Filter,0x00400000,0,1,Mp3Src.ax,1.01.0000.0000
Windows Media Multiplexer,0x00600000,1,1,wmpasf.dll,11.00.5721.5145
ASX file Parser,0x00600000,1,1,wmpasf.dll,11.00.5721.5145
ASX v.2 file Parser,0x00600000,1,0,wmpasf.dll,11.00.5721.5145
NSC file Parser,0x00600000,1,1,wmpasf.dll,11.00.5721.5145
ACM Wrapper,0x00600000,1,1,quartz.dll,6.05.2600.2749
Windows Media source filter,0x00600000,0,2,wmpasf.dll,11.00.5721.5145
Video Renderer,0x00800001,1,0,quartz.dll,6.05.2600.2749
Frame Eater,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
MPEG-2 Video Stream Analyzer,0x00200000,0,0,sbe.dll,6.05.2600.2180
Sonic Audio Depth Converter,0x00200000,1,1,AudioDepthConverter.ax,1.00.0000.0000
Line 21 Decoder,0x00600000,1,1,qdvd.dll,6.05.2600.2180
Video Port Manager,0x00600000,2,1,quartz.dll,6.05.2600.2749
WST Decoder,0x00600000,1,1,wstdecod.dll,5.03.2600.2180
Video Renderer,0x00400000,1,0,quartz.dll,6.05.2600.2749
Creative AC3 Source Filter,0x00400000,0,1,AC3Src.ax,1.01.0000.0000
MainConcept (Sonic) MPEG Encoder,0x00200000,2,1,SonicMCESMpeg.ax,1.00.0001.0023
MainConcept (Sonic) MPEG Video Encoder,0x00200000,1,1,sonicmcevmpeg.ax,1.00.0000.0014
MainConcept (Sonic) MPEG Audio Encoder,0x00200000,1,1,sonicmceampeg.ax,1.00.0000.0007
CT SmartVolumeManagement filter,0x00100000,1,1,DSCompr.ax,1.00.0000.0001
WM ASF Writer,0x00400000,0,0,qasf.dll,11.00.5721.5145
WMT Sample Information Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
VBI Surface Allocator,0x00600000,1,1,vbisurf.ax,5.03.2600.2180
Creative MP3 Writer,0x00200000,1,0,MP3Write.ax,1.02.0001.0000
Microsoft MPEG-4 Video Decompressor,0x00800000,1,1,mpg4ds32.ax,8.00.0000.4487
File writer,0x00200000,1,0,qcap.dll,6.05.2600.2180
MainConcept (Sonic) Sample Buffer Filter,0x00200000,1,1,SonicMCSampleBuffer.ax,1.00.0000.0004
WMT Log Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
WMT Virtual Renderer,0x00200000,1,0,wmm2filt.dll,2.01.4026.0000
Sonic MPEG Video Decoder,0x00200000,2,1,SonicMPEGVideo.DLL,2.05.0004.1044
Sonic Audio SRC,0x00200000,1,1,DSAudioSRC.ax,1.00.0000.0000
DVD Navigator,0x00200000,0,2,qdvd.dll,6.05.2600.2180
Sonic Audio Offset Filter,0x00200000,1,1,Offset.ax,
Overlay Mixer2,0x00400000,1,1,qdvd.dll,6.05.2600.2180
AVI Draw,0x00600064,9,1,quartz.dll,6.05.2600.2749
.RAM file Parser,0x00600000,1,0,wmpasf.dll,11.00.5721.5145
WMT DirectX Transform Wrapper,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
G.711 Codec,0x00200000,1,1,g711codc.ax,5.01.2600.0000
MPEG-2 Demultiplexer,0x00600000,1,1,mpg2splt.ax,6.05.2600.2180
Sonic Rainbow Fix,0x00200000,1,1,SonicRainbowFix.ax,1.00.0000.0000
DV Video Decoder,0x00800000,1,1,qdv.dll,6.05.2600.2180
Creative MP3 Source Filter,0x00400000,0,1,CTMP3SFT.DLL,1.00.0010.0000
Indeo® audio software,0x00500000,1,1,iac25_32.ax,2.00.0005.0053
Windows Media Update Filter,0x00400000,1,0,wmpasf.dll,11.00.5721.5145
Noise Reduction,0x00100000,1,1,NoisRedu.ax,2.00.0000.0001
Sonic File Writer,0x00200000,1,0,SonicFileWriter.ax,
ASF DIB Handler,0x00600000,1,1,wmpasf.dll,11.00.5721.5145
ASF ACM Handler,0x00600000,1,1,wmpasf.dll,11.00.5721.5145
ASF ICM Handler,0x00600000,1,1,wmpasf.dll,11.00.5721.5145
ASF URL Handler,0x00600000,1,1,wmpasf.dll,11.00.5721.5145
ASF JPEG Handler,0x00600000,1,1,wmpasf.dll,11.00.5721.5145
ASF DJPEG Handler,0x00600000,1,1,wmpasf.dll,11.00.5721.5145
ASF embedded stuff Handler,0x00600000,1,1,wmpasf.dll,11.00.5721.5145
9x8Resize,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
WIA Stream Snapshot Filter,0x00200000,1,1,wiasf.ax,1.00.0000.0000
Allocator Fix,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
SampleGrabber,0x00200000,1,1,qedit.dll,6.05.2600.2180
Null Renderer,0x00200000,1,0,qedit.dll,6.05.2600.2180
Creative WMA Writer,0x00200000,1,0,WMAWrite.ax,1.02.0001.0000
WMT Virtual Source,0x00200000,0,1,wmm2filt.dll,2.01.4026.0000
WMT Interlacer,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
StreamBufferSource,0x00200000,0,0,sbe.dll,6.05.2600.2180
Smart Tee,0x00200000,1,2,qcap.dll,6.05.2600.2180
Creative WMA Source Filter,0x00400000,0,1,WmaSrc.ax,1.00.0007.0000
Overlay Mixer,0x00200000,0,0,qdvd.dll,6.05.2600.2180
AVI Decompressor,0x00600000,1,1,quartz.dll,6.05.2600.2749
Uncompressed Domain Shot Detection Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
AVI/WAV File Source,0x00400000,0,2,quartz.dll,6.05.2600.2749
QuickTime Movie Parser,0x00600000,1,1,quartz.dll,6.05.2600.2749
Wave Parser,0x00400000,1,1,quartz.dll,6.05.2600.2749
MIDI Parser,0x00400000,1,1,quartz.dll,6.05.2600.2749
Multi-file Parser,0x00400000,1,1,quartz.dll,6.05.2600.2749
File stream renderer,0x00400000,1,1,quartz.dll,6.05.2600.2749
XML Playlist,0x00400000,1,0,wmpasf.dll,11.00.5721.5145
NVF Filter,0x00400000,0,1,CTNVFFLT.DLL,1.00.0000.0000
CyberLink Line21 Decoder Filter,0x00200000,0,2,CLLine21.ax,4.00.0000.4418
CyberLink Video/SP Decoder DELL 5.3,0x00600000,2,3,CLVSD.ax,6.00.0000.0818
CyberLink AudioCD Filter,0x00600000,0,1,CLAudioCD.ax,5.00.0000.1305
CyberLink TimeStretch Filter,0x00200000,1,1,clauts.ax,1.00.0000.1305
CyberLink Audio Effect,0x00200000,1,1,CLAudFx.ax,5.00.0000.1305
CyberLink DVD Navigator,0x00600000,0,3,CLNavX.ax,5.03.0000.0803
CyberLink Audio Decoder,0x00601000,1,1,claud.ax,6.00.0000.0727
Sonic MPEG Splitter,0x00200000,1,2,SonicMPEGSplitter.dll,1.00.0000.0105
AVI Mux,0x00200000,1,0,qcap.dll,6.05.2600.2180
Line 21 Decoder 2,0x00600002,1,1,quartz.dll,6.05.2600.2749
File Source (Async.),0x00400000,0,1,quartz.dll,6.05.2600.2749
File Source (URL),0x00400000,0,1,quartz.dll,6.05.2600.2749
WMT DV Extract,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Sonic DV Scene Detector,0x00600000,1,1,DVSceneDetector.ax,1.00.0000.0000
Creative CDDA Source Filter,0x00400000,0,1,CDDA.ax,1.02.0008.0000
WMT Switch Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
WMT Volume,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Sonic Video Performance Monitor,0x00600000,1,1,VidPerfMonitor.ax,1.00.0000.0000
Sonic SP Video Renderer,0x00200000,1,0,SonicVideoRenderer.ax,8.01.0000.0000
Stretch Video,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Infinite Pin Tee Filter,0x00200000,1,1,qcap.dll,6.05.2600.2180
QT Decompressor,0x00600000,1,1,quartz.dll,6.05.2600.2749
MPEG Video Decoder,0x40000001,1,1,quartz.dll,6.05.2600.2749
Indeo® video 4.4 Decompression Filter,0x00640000,1,1,ir41_32.ax,4.51.0016.0003
Indeo® video 4.4 Compression Filter,0x00200000,1,1,ir41_32.ax,4.51.0016.0003

WDM Streaming Data Transforms:
Microsoft Kernel Acoustic Echo Canceller,0x00000000,0,0,,
Microsoft Kernel GS Wavetable Synthesizer,0x00200000,1,1,,5.03.2600.2180
Microsoft Kernel DLS Synthesizer,0x00200000,1,1,,5.03.2600.2180
Microsoft Kernel DRM Audio Descrambler,0x00200000,1,1,,5.03.2600.2180

Video Compressors:
WMVideo Encoder DMO,0x00600800,1,1,,
WMVideo8 Encoder DMO,0x00600800,1,1,,
MSScreen encoder DMO,0x00600800,1,1,,
WMVideo9 Encoder DMO,0x00600800,1,1,,
MSScreen 9 encoder DMO,0x00600800,1,1,,
DV Video Encoder,0x00200000,0,0,qdv.dll,6.05.2600.2180
Indeo® video 5.10 Compression Filter,0x00100000,1,1,ir50_32.dll,5.2562.0015.0055
MainConcept (Sonic) MPEG Video Encoder,0x00200000,1,1,sonicmcevmpeg.ax,1.00.0000.0014
MJPEG Compressor,0x00200000,0,0,quartz.dll,6.05.2600.2749
Cinepak Codec by Radius,0x00200000,1,1,qcap.dll,6.05.2600.2180
Fraps Video Decompressor,0x00200000,1,1,qcap.dll,6.05.2600.2180
Intel 4:2:0 Video V2.50,0x00200000,1,1,qcap.dll,6.05.2600.2180
Intel Indeo(R) Video R3.2,0x00200000,1,1,qcap.dll,6.05.2600.2180
Intel Indeo® Video 4.5,0x00200000,1,1,qcap.dll,6.05.2600.2180
Indeo® video 5.10,0x00200000,1,1,qcap.dll,6.05.2600.2180
Intel IYUV codec,0x00200000,1,1,qcap.dll,6.05.2600.2180
Microsoft H.261 Video Codec,0x00200000,1,1,qcap.dll,6.05.2600.2180
Microsoft H.263 Video Codec,0x00200000,1,1,qcap.dll,6.05.2600.2180
Microsoft MPEG-4 Video Codec V2,0x00200000,1,1,qcap.dll,6.05.2600.2180
Microsoft MPEG-4 Video Codec V1,0x00200000,1,1,qcap.dll,6.05.2600.2180
Microsoft RLE,0x00200000,1,1,qcap.dll,6.05.2600.2180
Microsoft Video 1,0x00200000,1,1,qcap.dll,6.05.2600.2180

Audio Compressors:
WMA Voice Encoder DMO,0x00600800,1,1,,
WM Speech Encoder DMO,0x00600800,1,1,,
WMAudio Encoder DMO,0x00600800,1,1,,
Indeo® audio software,0x00500000,1,1,iac25_32.ax,2.00.0005.0053
MainConcept (Sonic) MPEG Audio Encoder,0x00200000,1,1,sonicmceampeg.ax,1.00.0000.0007
IAC2,0x00200000,1,1,quartz.dll,6.05.2600.2749
Lernout & Hauspie CELP 4.8kbit/s,0x00200000,1,1,quartz.dll,6.05.2600.2749
Lernout & Hauspie SBC 8kbit/s,0x00200000,1,1,quartz.dll,6.05.2600.2749
Lernout & Hauspie SBC 12kbit/s,0x00200000,1,1,quartz.dll,6.05.2600.2749
Lernout & Hauspie SBC 16kbit/s,0x00200000,1,1,quartz.dll,6.05.2600.2749
IMA ADPCM,0x00200000,1,1,quartz.dll,6.05.2600.2749
PCM,0x00200000,1,1,quartz.dll,6.05.2600.2749
Microsoft ADPCM,0x00200000,1,1,quartz.dll,6.05.2600.2749
ACELP.net,0x00200000,1,1,quartz.dll,6.05.2600.2749
DSP Group TrueSpeech(TM),0x00200000,1,1,quartz.dll,6.05.2600.2749
Windows Media Audio V1,0x00200000,1,1,quartz.dll,6.05.2600.2749
Windows Media Audio V2,0x00200000,1,1,quartz.dll,6.05.2600.2749
GSM 6.10,0x00200000,1,1,quartz.dll,6.05.2600.2749
Microsoft G.723.1,0x00200000,1,1,quartz.dll,6.05.2600.2749
CCITT A-Law,0x00200000,1,1,quartz.dll,6.05.2600.2749
CCITT u-Law,0x00200000,1,1,quartz.dll,6.05.2600.2749
MPEG Layer-3,0x00200000,1,1,quartz.dll,6.05.2600.2749

Audio Capture Sources:
Logitech USB Headset,0x00200000,0,0,qcap.dll,6.05.2600.2180
SB Audigy 2 Audio [CCC0],0x00200000,0,0,qcap.dll,6.05.2600.2180

Midi Renderers:
Default MidiOut Device,0x00800000,1,0,quartz.dll,6.05.2600.2749
Microsoft GS Wavetable SW Synth,0x00200000,1,0,quartz.dll,6.05.2600.2749
SB Audigy 2 MIDI IO [CCC0],0x00200000,1,0,quartz.dll,6.05.2600.2749
SB Audigy 2 Sw Synth [CCC0],0x00200000,1,0,quartz.dll,6.05.2600.2749
SB Audigy 2 Synth A [CCC0],0x00200000,1,0,quartz.dll,6.05.2600.2749
SB Audigy 2 Synth B [CCC0],0x00200000,1,0,quartz.dll,6.05.2600.2749

WDM Streaming Capture Devices:
SB Audigy 2 MIDI IO [CCC0],0x00200000,2,2,,5.03.2600.2180
SB Audigy 2 Audio [CCC0],0x00200000,3,2,,5.03.2600.2180
USB Audio Device,0x00200000,3,2,,5.03.2600.2180

WDM Streaming Rendering Devices:
SB Audigy 2 DirectMusic Synthesizer [CCC0],0x00200000,1,1,,5.03.2600.2180
SB Audigy 2 Sw Synth [CCC0],0x00200000,1,1,,5.03.2600.2180
SB Audigy 2 Synth A [CCC0],0x00200000,1,1,,5.03.2600.2180
SB Audigy 2 Synth B [CCC0],0x00200000,1,1,,5.03.2600.2180
SB Audigy 2 MIDI IO [CCC0],0x00200000,2,2,,5.03.2600.2180
SB Audigy 2 Audio [CCC0],0x00200000,3,2,,5.03.2600.2180
USB Audio Device,0x00200000,3,2,,5.03.2600.2180

WDM Streaming Mixer Devices:
Microsoft Kernel Wave Audio Mixer,0x00000000,0,0,,

BDA CP/CA Filters:
Decrypt/Tag,0x00600000,1,0,encdec.dll,6.05.2600.2180
Encrypt/Tag,0x00200000,0,0,encdec.dll,6.05.2600.2180
XDS Codec,0x00200000,0,0,encdec.dll,6.05.2600.2180

Audio Renderers:
Logitech USB Headset,0x00200000,1,0,quartz.dll,6.05.2600.2749
CyberLink Audio Renderer,0x00200000,1,0,cladr.ax,6.00.0000.0818
Default DirectSound Device,0x00800000,1,0,quartz.dll,6.05.2600.2749
Default WaveOut Device,0x00200000,1,0,quartz.dll,6.05.2600.2749
DirectSound: Logitech USB Headset,0x00200000,1,0,quartz.dll,6.05.2600.2749
DirectSound: SB Audigy 2 Audio [CCC0],0x00200000,1,0,quartz.dll,6.05.2600.2749
SB Audigy 2 Audio [CCC0],0x00200000,1,0,quartz.dll,6.05.2600.2749

WDM Streaming System Devices:
SB Audigy 2 DirectMusic Synthesizer [CCC0],0x00200000,1,1,,5.03.2600.2180
SB Audigy 2 Sw Synth [CCC0],0x00200000,1,1,,5.03.2600.2180
SB Audigy 2 Synth A [CCC0],0x00200000,11,2,,5.03.2600.2180
SB Audigy 2 Synth B [CCC0],0x00200000,1,1,,5.03.2600.2180
SB Audigy 2 MIDI IO [CCC0],0x00200000,2,2,,5.03.2600.2180
SB Audigy 2 Audio [CCC0],0x00200000,13,2,,5.03.2600.2180
USB Audio Device,0x00200000,4,2,,5.03.2600.2180

---

### Post by Heous on 2007-03-07
Bump.  I hope this isn't against the rules, but I really need help with this problem.

---

### Post by Heous on 2007-03-07
Bump. I can't start up Ubuntu, and any help would be appreciated.

---

### Post by Heous on 2007-03-08
Bump.  I STILL can't get this to work properly, and I don't want to have to reinstall Ubuntu just to fix it.

---

### Post by Heous on 2007-03-08
*sigh* Bump.  I guess this is the last time I'll request help for this.  If this topic sinks back to the second page I'll just have to re-install Ubuntu.

---

### Post by bobbob1016 on 2007-05-30
I think part of the reason this thread went unanswered was that you posted your 3 or 4 post DXDIAG when no one is going to read it.  Also, bumping 4 times in two days isn't something you should do either.

It sounds like your xserver was reconfigured incorrectly, you'd just have to get into recovery mode (you press escape at boot up if you only have ubuntu on the system and select recovery mode for the newest kernel), and do "sudo dpkg-reconfigure xserver-xorg" again.  Make sure you have the correct settings there.

---

