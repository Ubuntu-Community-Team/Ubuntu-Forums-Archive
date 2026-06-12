---
title: "Using Unshield X or Alien - I dont know what I am doing Help"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by dnguyen527 on 2007-03-31
Hey,

A bunch of guys helped me install Alien all morning so I could follow these directions to install Belkin f5d6050 USB network card.

[http://www.astahost.com/info.php/con...er_t14333.html](http://www.astahost.com/info.php/con...er_t14333.html)

Download the driver. Extract to a new directory using unzip. Extract the CAB files (DATA1.CAB, DATA1.HDR, DATA2.CAB) using "unshield x" . cd Drivers/WINXP . edit bkusb.in_ and uncomment the CopyFile.XP.Sys section. Run ndiswrapper -i bkusb.in_ as root followed by ndiswrapper -m . modprobe ndiswrapper. ifdown wlan0. ifup wlan0 and you are there.

So I had to get Alien to install Unshield X - I extracted the CAB files by going to the Terminal and typing - Unshield X "drag the CAB file in" then pressed enter and it extracted - No idea where but it did.

So then I typed:

cd Drivers/WINXP .edit bkusb.in_

Now I dont know what to do. I think i am on this step:

uncomment the CopyFile.XP.Sys section

^ what does that mean and whats the command 

I also setup ndiswrappers last night - took me hours!!!

Maybe I am doing everything wrong but PLEASE help me. I cant get online, I've been downloading files on my laptop and using my flash drive to transfer files - I think I am about to break it : /

I'd love to get online but if I cant - I am going to have to go back to XP : (

---

### Post by jfinkels on 2007-03-31
> **dnguyen527 said:**
> 

cd Drivers/WINXP .edit bkusb.in_

[...]

uncomment the CopyFile.XP.Sys section


After you change into the *Drivers/WINXP* directory by typing this
```

cd Drivers/WINXP

```
you're going to have to edit the file called *bkusb.in_*. To do this, type the following in the terminal:
```

gedit bkusb.in_

```
When the program "gedit" opens, look for a section in the text named "CopyFile.XP.Sys". If you can, post the contents of this section on this thread so we can take a look at how to uncomment the code. You will have to change the text a bit.

---

### Post by dnguyen527 on 2007-03-31
Stay here for a minute. I am working on copying the contents here.

---

### Post by jfinkels on 2007-03-31
> **dnguyen527 said:**
> Stay here for a minute. I am working on copying the contents here.

Don't bother, I found it myself: Here's what you need to do:

Search for the section in the file named "Win XP Section". It will be surrounded by a bunch of asterisks.

```

;******************************************************************************\
*
; Win XP section
;******************************************************************************\
*
[DrvInstXP.Ndi1.NTx86]
Characteristics = 0x84                     ; NCF_HAS_UI | NCF_PHYSICAL
BusType         = 15                       ; USB
AddReg          = WinXP.Reg, WinXP.Params
;CopyFiles       = CopyFile.XP.Sys
[...]

```

Where it says ";CopyFiles       = CopyFile.XP.Sys", delete the semicolon at the beginning of that line.

---

### Post by annda on 2007-03-31
a friendly advice: please do not double post. this is really confusing for people trying to help you.

if you don't get answers (you can't expect that in 7 minutes), bump the thread - just post another message on THE SAME thread.

we would like to help, and it will be much easier if we can talk to you and get information back in one place. see you soon!

---

### Post by dnguyen527 on 2007-03-31
";UNT-bkusb.inf
;*******************************************************************************
; Copyright 2003 Belkin Components.
; INF file for Belkin 11Mbps Wireless USB Network Adapter
;
; Supported OS: Windows 98/Me/2000/XP
;
; Belkin version: 2.9.8.311
;*******************************************************************************

[Version]
Signature = "$Chicago$"
Compatible = 1
Class = Net
ClassGUID = {4d36e972-e325-11ce-bfc1-08002be10318}
MillenniumPreferred = .ME
Provider = %VENDOR%
CatalogFile = bkusb.cat
DriverVer = 04/09/2003,2.9.8.311

[Manufacturer]
%VENDOR% = Belkin, NT.5.1

[ControlFlags]
ExcludeFromSelect = *

[Belkin]
%DeviceDesc% = DrvInst.Ndi1,USB\VID_0D5C&PID_A002
%DeviceDesc% = DrvInst.Ndi2,USB\VID_083A&PID_3501
%DeviceDesc% = DrvInst.Ndi3,USB\VID_050D&PID_0050
[Belkin.NT.5.1]
%DeviceDesc% = DrvInstXP.Ndi1,USB\VID_0D5C&PID_A002
%DeviceDesc% = DrvInstXP.Ndi2,USB\VID_083A&PID_3501
%DeviceDesc% = DrvInstXP.Ndi3,USB\VID_050D&PID_0050

;*******************************************************************************
; Windows 98 section
;*******************************************************************************
[DrvInst.Ndi1]
AddReg    = Win9x.Reg1, Win9x2k.Params
;CopyFiles = CopyFile.Sys
DriverVer = 04/09/2003,2.9.8.311

[Win9x.Reg1]
HKR,Ndi,DeviceID,0,"USB\VID_0D5C&PID_A002"
HKR,Ndi,CardType,,"PNP"
HKR,,DevLoader,0,"*ndis"
HKR,,DeviceVxDs,0,"bkusb98.sys"

; NDIS Info
HKR,NDIS,MajorNdisVersion,1,05
HKR,NDIS,MinorNdisVersion,1,00
HKR,NDIS,LogDriverName,,%ServiceName%(R)

; Interfaces
HKR,Ndi\Interfaces,DefUpper,,"ndis3"
HKR,Ndi\Interfaces,DefLower,,"ethernet"
HKR,Ndi\Interfaces,UpperRange,,"ndis3"
HKR,Ndi\Interfaces,LowerRange,,"ethernet"

HKR,Ndi,HelpText,,%Help_Text%

[DrvInst.Ndi2]
AddReg    = Win9x.Reg2, Win9x2k.Params
;CopyFiles = CopyFile.Sys
DriverVer = 04/09/2003,2.9.8.311

[Win9x.Reg2]
HKR,Ndi,DeviceID,0,"USB\VID_083A&PID_3501"
HKR,Ndi,CardType,,"PNP"
HKR,,DevLoader,0,"*ndis"
HKR,,DeviceVxDs,0,"bkusb98.sys"

; NDIS Info
HKR,NDIS,MajorNdisVersion,1,05
HKR,NDIS,MinorNdisVersion,1,00
HKR,NDIS,LogDriverName,,%ServiceName%(R)

; Interfaces
HKR,Ndi\Interfaces,DefUpper,,"ndis3"
HKR,Ndi\Interfaces,DefLower,,"ethernet"
HKR,Ndi\Interfaces,UpperRange,,"ndis3"
HKR,Ndi\Interfaces,LowerRange,,"ethernet"

HKR,Ndi,HelpText,,%Help_Text%

[DrvInst.Ndi3]
AddReg    = Win9x.Reg3, Win9x2k.Params
;CopyFiles = CopyFile.Sys
DriverVer = 04/09/2003,2.9.8.311

[Win9x.Reg3]
HKR,Ndi,DeviceID,0,"USB\VID_050D&PID_0050"
HKR,Ndi,CardType,,"PNP"
HKR,,DevLoader,0,"*ndis"
HKR,,DeviceVxDs,0,"bkusb98.sys"

; NDIS Info
HKR,NDIS,MajorNdisVersion,1,05
HKR,NDIS,MinorNdisVersion,1,00
HKR,NDIS,LogDriverName,,%ServiceName%(R)

; Interfaces
HKR,Ndi\Interfaces,DefUpper,,"ndis3"
HKR,Ndi\Interfaces,DefLower,,"ethernet"
HKR,Ndi\Interfaces,UpperRange,,"ndis3"
HKR,Ndi\Interfaces,LowerRange,,"ethernet"

HKR,Ndi,HelpText,,%Help_Text%


;[CopyFile.Sys]
;bkusb98.sys,,,2

;*******************************************************************************
; Windows Me section
;*******************************************************************************
[DrvInst.ndi1.ME]
Characteristics = 0x84                         ; NCF_HAS_UI | NCF_PHYSICAL
BusType         = 15                           ; USB
AddReg          = WinMe.Reg, Win9x2k.Params
;CopyFiles       = CopyFile.Me.Sys

[DrvInst.ndi2.ME]
Characteristics = 0x84                         ; NCF_HAS_UI | NCF_PHYSICAL
BusType         = 15                           ; USB
AddReg          = WinMe.Reg, Win9x2k.Params
;CopyFiles       = CopyFile.Me.Sys

[DrvInst.ndi3.ME]
Characteristics = 0x84                         ; NCF_HAS_UI | NCF_PHYSICAL
BusType         = 15                           ; USB
AddReg          = WinMe.Reg, Win9x2k.Params
;CopyFiles       = CopyFile.Me.Sys

[DrvInst.ndi1.ME.Services]
AddService = %VENDOR% %ServiceName%(R), 2, FVNETusbMe.Service, FVNETusb.EventLog

[DrvInst.ndi2.ME.Services]
AddService = %VENDOR% %ServiceName%(R), 2, FVNETusbMe.Service, FVNETusb.EventLog

[DrvInst.ndi3.ME.Services]
AddService = %VENDOR% %ServiceName%(R), 2, FVNETusbMe.Service, FVNETusb.EventLog

[WinMe.Reg]
HKR,Ndi,Service,0,%VENDOR% %ServiceName%(R)
HKR,,DevLoader,0,*ndis
HKR,,DeviceVxDs,0,bkusb98.sys
HKR,,EnumPropPages,0,"netdi.dll,EnumPropPages"

; NDIS Info
HKR,NDIS,MajorNdisVersion,1,05
HKR,NDIS,MinorNdisVersion,1,00
HKR,NDIS,LogDriverName,,%ServiceName%(R)

; Interfaces
HKR,Ndi\Interfaces,DefUpper,0,"ndis5"
HKR,Ndi\Interfaces,DefLower,0,"ethernet"
HKR,Ndi\Interfaces,UpperRange,0,"ndis5"
HKR,Ndi\Interfaces,LowerRange,0,"ethernet"

; Install sections
;HKR, Ndi\Install,       ndis3,              0, "FVNETusb.ndis5me"

;[FVNETusb.ndis5me]
;CopyFiles       = CopyFile.Me.Sys

;[CopyFile.Me.Sys]
;bkusb98.sys

[FVNETusbMe.Service]
DisplayName    = %VENDOR% %ServiceName%(R) Service for %DeviceDesc%
ServiceType    = 1
StartType      = 3
ErrorControl   = 1
ServiceBinary  = %11%\bkusb98.sys
LoadOrderGroup = NDIS


;*******************************************************************************
; Win 2000 section
;*******************************************************************************
[DrvInst.Ndi1.NTx86]
Characteristics = 0x84                     ; NCF_HAS_UI | NCF_PHYSICAL
BusType     = 15                           ; USB
AddReg      = Win2k.Reg, Win9x2k.Params
;CopyFiles   = CopyFile.2k.Sys

[DrvInst.Ndi1.NTx86.Services]
AddService = %VENDOR% %ServiceName%(R), 2, FVNETusb2k.Service, FVNETusb.EventLog

[DrvInst.Ndi2.NTx86]
Characteristics = 0x84                     ; NCF_HAS_UI | NCF_PHYSICAL
BusType     = 15                           ; USB
AddReg      = Win2k.Reg, Win9x2k.Params
;CopyFiles   = CopyFile.2k.Sys

[DrvInst.Ndi2.NTx86.Services]
AddService = %VENDOR% %ServiceName%(R), 2, FVNETusb2k.Service, FVNETusb.EventLog

[DrvInst.Ndi3.NTx86]
Characteristics = 0x84                     ; NCF_HAS_UI | NCF_PHYSICAL
BusType     = 15                           ; USB
AddReg      = Win2k.Reg, Win9x2k.Params
;CopyFiles   = CopyFile.2k.Sys

[DrvInst.Ndi3.NTx86.Services]
AddService = %VENDOR% %ServiceName%(R), 2, FVNETusb2k.Service, FVNETusb.EventLog

[Win2k.Reg]
; Interfaces
HKR, Ndi\Interfaces, LowerRange, 0, "ethernet"
HKR, Ndi\Interfaces, UpperRange, 0, "ndis5"
HKR, Ndi,            Service,    0, "%VENDOR% %ServiceName%(R)"

;[CopyFile.2k.Sys]
;bkusb98.sys,,,2


;*******************************************************************************
; Win XP section
;*******************************************************************************
[DrvInstXP.Ndi1.NTx86]
Characteristics = 0x84                     ; NCF_HAS_UI | NCF_PHYSICAL
BusType         = 15                       ; USB
AddReg          = WinXP.Reg, WinXP.Params
;CopyFiles       = CopyFile.XP.Sys

[DrvInstXP.Ndi1.NTx86.Services]
AddService = %VENDOR% %ServiceName%(R), 2, FVNETusbXP.Service, FVNETusb.EventLog

[DrvInstXP.Ndi2.NTx86]
Characteristics = 0x84                     ; NCF_HAS_UI | NCF_PHYSICAL
BusType         = 15                       ; USB
AddReg          = WinXP.Reg, WinXP.Params
;CopyFiles       = CopyFile.XP.Sys

[DrvInstXP.Ndi2.NTx86.Services]
AddService = %VENDOR% %ServiceName%(R), 2, FVNETusbXP.Service, FVNETusb.EventLog

[DrvInstXP.Ndi3.NTx86]
Characteristics = 0x84                     ; NCF_HAS_UI | NCF_PHYSICAL
BusType         = 15                       ; USB
AddReg          = WinXP.Reg, WinXP.Params
;CopyFiles       = CopyFile.XP.Sys

[DrvInstXP.Ndi3.NTx86.Services]
AddService = %VENDOR% %ServiceName%(R), 2, FVNETusbXP.Service, FVNETusb.EventLog

[WinXP.Reg]
; Interfaces
HKR, Ndi\Interfaces, LowerRange, 0, "ethernet"
HKR, Ndi\Interfaces, UpperRange, 0, "ndis5"
HKR, Ndi,            Service,    0, "%VENDOR% %ServiceName%(R)"

;[CopyFile.XP.Sys]
;bkusbxp.sys,,,2

;*******************************************************************************
; Win 2000 service section
;*******************************************************************************
[FVNETusb2k.Service]
DisplayName    = %VENDOR% %ServiceName%(R) Service for %DeviceDesc%
ServiceType    = 1
StartType      = 3
ErrorControl   = 1
ServiceBinary  = %12%\bkusb98.sys
LoadOrderGroup = NDIS

;*******************************************************************************
; Win XP service section
;*******************************************************************************
[FVNETusbXP.Service]
DisplayName    = %VENDOR% %ServiceName%(R) Service for %DeviceDesc%
ServiceType    = 1
StartType      = 3
ErrorControl   = 1
ServiceBinary  = %12%\bkusbxp.sys
LoadOrderGroup = NDIS

;*******************************************************************************
; Win Me/2000/XP common section
;*******************************************************************************
[FVNETusb.EventLog]
AddReg = FVNETusb.AddEventLog.Reg

[FVNETusb.AddEventLog.Reg]
HKR, , EventMessageFile, 0x00020000, %%SystemRoot%%\System32\netevent.dll
HKR, , TypesSupported  , 0x00010001, 7


;*******************************************************************************
; Destination directories
;*******************************************************************************
;[DestinationDirs]
;DefaultDestDir   = 12 ; Drivers directory
;CopyFile.Sys     = 11
;CopyFile.2k.Sys  = 12
;CopyFile.Me.Sys  = 11
;CopyFile.XP.Sys  = 12

[SourceDisksNames]
1=%DriverDiskName%,,

;[SourceDisksFiles]
;bkusbxp.sys=1
;bkusb98.sys=1
;bkusbxp.sys=1,.,bkusbxp.sys,10000
;bkusb98.sys=1,.,bkusb98.sys,10000


;*******************************************************
; Driver parameters for Win9x,2k
;*******************************************************
[Win9x2k.Params]
HKR, Ndi\params\PreambleType,                     ParamDesc,           0, "Preamble Type"
HKR, Ndi\params\PreambleType,                     default,             0, "2"
HKR, Ndi\params\PreambleType,                     type,                0, "enum"
HKR, Ndi\params\PreambleType\enum,                0,                   0, "Long"
HKR, Ndi\params\PreambleType\enum,                1,                   0, "Short"
HKR, Ndi\params\PreambleType\enum,                2,                   0, "Auto"
HKR, ,                                            PreambleType,        0, "2"

HKR, Ndi\params\Channel,                          ParamDesc,           0, "Channel"
HKR, Ndi\params\Channel,                          default,             0, "10"
HKR, Ndi\params\Channel,                          type,                0, "int"
HKR, Ndi\params\Channel,                          min,                 0, "1"
HKR, Ndi\params\Channel,                          max,                 0, "14"
HKR, Ndi\params\Channel,                          step,                0, "1"
HKR, ,                                            Channel,             0, "10"

HKR, Ndi\params\Rate,                             ParamDesc,           0, "TX Rate (Mbps)"
HKR, Ndi\params\Rate,                             default,             0, "4"
HKR, Ndi\params\Rate,                             type,                0, "enum"
HKR, Ndi\params\Rate\enum,                        0,                   0, "1 Mbps"
HKR, Ndi\params\Rate\enum,                        1,                   0, "2 Mbps"
HKR, Ndi\params\Rate\enum,                        2,                   0, "5.5 Mbps"
HKR, Ndi\params\Rate\enum,                        3,                   0, "11 Mbps"
HKR, Ndi\params\Rate\enum,                        4,                   0, "Auto"
HKR, ,                                            Rate,                0, "4"

HKR, Ndi\params\RTS_Threshold,                    ParamDesc,           0, "RTS Threshold"
HKR, Ndi\params\RTS_Threshold,                    default,             0, "2347"
HKR, Ndi\params\RTS_Threshold,                    type,                0, "int"
HKR, Ndi\params\RTS_Threshold,                    min,                 0, "0"
HKR, Ndi\params\RTS_Threshold,                    max,                 0, "2347"
HKR, Ndi\params\RTS_Threshold,                    step,                0, "1"
HKR, ,                                            RTS_Threshold,       0, "2347"

HKR, Ndi\params\Frag_Threshold,                   ParamDesc,           0, "Fragmentation Threshold"
HKR, Ndi\params\Frag_Threshold,                   default,             0, "2346"
HKR, Ndi\params\Frag_Threshold,                   type,                0, "int"
HKR, Ndi\params\Frag_Threshold,                   min,                 0, "256"
HKR, Ndi\params\Frag_Threshold,                   max,                 0, "2346"
HKR, Ndi\params\Frag_Threshold,                   step,                0, "1"
HKR, ,                                            Frag_Threshold,      0, "2346"

HKR, Ndi\params\Operating_Mode,                   ParamDesc,           0, "Operating Mode"
HKR, Ndi\params\Operating_Mode,                   default,             0, "1"
HKR, Ndi\params\Operating_Mode,                   type,                0, "enum"
HKR, Ndi\params\Operating_Mode\enum,              0,                   0, "Ad-Hoc"
HKR, Ndi\params\Operating_Mode\enum,              1,                   0, "Infrastructure"
HKR, ,                                            Operating_Mode,      0, "1"

HKR, Ndi\params\InternationalRoaming,             ParamDesc,           0, "International Roaming"
HKR, Ndi\params\InternationalRoaming,             default,             0, "0"
HKR, Ndi\params\InternationalRoaming,             type,                0, "enum"
HKR, Ndi\params\InternationalRoaming\enum,        0,                   0, "Disabled (Reg. Domain)"
HKR, Ndi\params\InternationalRoaming\enum,        1,                   0, "Enabled (Int. Roaming)"
HKR, ,                                            InternationalRoaming,0, "0"

HKR, Ndi\params\ESSID,                            ParamDesc,           0, "ESSID"
HKR, Ndi\params\ESSID,                            default,             0, ""
HKR, Ndi\params\ESSID,                            type,                0, "edit"
HKR, Ndi\params\ESSID,                            LimitText,           0, "32"
HKR, Ndi\params\ESSID,                            UpperCase,           0, "0"
HKR, ,                                            ESSID,               0, ""

HKR, Ndi\params\AuthenticationType,               ParamDesc,           0, "Authentication Type"
HKR, Ndi\params\AuthenticationType,               default,             0, "2"
HKR, Ndi\params\AuthenticationType,               type,                0, "enum"
HKR, Ndi\params\AuthenticationType\enum,          0,                   0, "Open System"
HKR, Ndi\params\AuthenticationType\enum,          1,                   0, "Shared Key"
HKR, Ndi\params\AuthenticationType\enum,          2,                   0, "Auto"
HKR, ,                                            AuthenticationType,  0, "2"

HKR, Ndi\params\PowerMgmtMode,                    ParamDesc,           0, "802.11 Power Save"
HKR, Ndi\params\PowerMgmtMode,                    type,                0, "enum"
HKR, Ndi\params\PowerMgmtMode,                    default,             0, "0"
HKR, Ndi\params\PowerMgmtMode\enum,               0,                   0, "Disabled"
HKR, Ndi\params\PowerMgmtMode\enum,               1,                   0, "Enabled"
HKR, ,                                            PowerMgmtMode,       0, "0"

HKR, Ndi\params\WEP_Mode,                         ParamDesc,           0, "Encrypted Data Mode"
HKR, Ndi\params\WEP_Mode,                         default,             0, "0"
HKR, Ndi\params\WEP_Mode,                         type,                0, "enum"
HKR, Ndi\params\WEP_Mode\enum,                    0,                   0, "Mandatory"
HKR, Ndi\params\WEP_Mode\enum,                    1,                   0, "Optional"
HKR, ,                                            WEP_Mode,            0, "0"

HKR, Ndi\params\EncryptionLevel,                  ParamDesc,           0, "Encryption Level"
HKR, Ndi\params\EncryptionLevel,                  type,                0, "enum"
HKR, Ndi\params\EncryptionLevel,                  default,             0, "0"
HKR, Ndi\params\EncryptionLevel\enum,             0,                   0, "None"
HKR, Ndi\params\EncryptionLevel\enum,             1,                   0, "64-bit encryption"
HKR, Ndi\params\EncryptionLevel\enum,             2,                   0, "128-bit encryption"
HKR, ,                                            EncryptionLevel,     0, "0"

HKR, Ndi\params\WEP_KEY_INDEX,                    ParamDesc,           0, "WEP Key to use"
HKR, Ndi\params\WEP_KEY_INDEX,                    type,                0, "enum"
HKR, Ndi\params\WEP_KEY_INDEX,                    default,             0, "0"
HKR, Ndi\params\WEP_KEY_INDEX\enum,               0,                   0, "Key #1"
HKR, Ndi\params\WEP_KEY_INDEX\enum,               1,                   0, "Key #2"
HKR, Ndi\params\WEP_KEY_INDEX\enum,               2,                   0, "Key #3"
HKR, Ndi\params\WEP_KEY_INDEX\enum,               3,                   0, "Key #4"
HKR, ,                                            WEP_KEY_INDEX,       0, "0"

HKR, Ndi\params\WEP_KEY_1,                        ParamDesc,           0, "WEP Key #1"
HKR, Ndi\params\WEP_KEY_1,                        default,             0, "00000000000000000000000000"
HKR, Ndi\params\WEP_KEY_1,                        type,                0, "edit"
HKR, Ndi\params\WEP_KEY_1,                        LimitText,           0, "26"
HKR, Ndi\params\WEP_KEY_1,                        UpperCase,           0, "1"
HKR, ,                                            WEP_KEY_1,           0, "00000000000000000000000000"

HKR, Ndi\params\WEP_KEY_2,                        ParamDesc,           0, "WEP Key #2"
HKR, Ndi\params\WEP_KEY_2,                        default,             0, "00000000000000000000000000"
HKR, Ndi\params\WEP_KEY_2,                        type,                0, "edit"
HKR, Ndi\params\WEP_KEY_2,                        LimitText,           0, "26"
HKR, Ndi\params\WEP_KEY_2,                        UpperCase,           0, "1"
HKR, ,                                            WEP_KEY_2,           0, "00000000000000000000000000"

HKR, Ndi\params\WEP_KEY_3,                        ParamDesc,           0, "WEP Key #3"
HKR, Ndi\params\WEP_KEY_3,                        default,             0, "00000000000000000000000000"
HKR, Ndi\params\WEP_KEY_3,                        type,                0, "edit"
HKR, Ndi\params\WEP_KEY_3,                        LimitText,           0, "26"
HKR, Ndi\params\WEP_KEY_3,                        UpperCase,           0, "1"
HKR, ,                                            WEP_KEY_3,           0, "00000000000000000000000000"

HKR, Ndi\params\WEP_KEY_4,                        ParamDesc,           0, "WEP Key #4"
HKR, Ndi\params\WEP_KEY_4,                        default,             0, "00000000000000000000000000"
HKR, Ndi\params\WEP_KEY_4,                        type,                0, "edit"
HKR, Ndi\params\WEP_KEY_4,                        LimitText,           0, "26"
HKR, Ndi\params\WEP_KEY_4,                        UpperCase,           0, "1"
HKR, ,                                            WEP_KEY_4,           0, "00000000000000000000000000"

HKR, Ndi\params\BasicRates,                       ParamDesc,           0, "Basic Rates"
HKR, Ndi\params\BasicRates,                       type,                0, "enum"
HKR, Ndi\params\BasicRates,                       default,             0, "1"
HKR, Ndi\params\BasicRates\enum,                  0,                   0, "1,2 Mbps"
HKR, Ndi\params\BasicRates\enum,                  1,                   0, "1,2,5.5,11 Mbps"
HKR, ,                                            BasicRates,          0, "1"

HKR, Ndi\params\BeaconPeriod,                     ParamDesc,           0, "Beacon Period"
HKR, Ndi\params\BeaconPeriod,                     type,                0, "int"
HKR, Ndi\params\BeaconPeriod,                     default,             0, "100"
HKR, Ndi\params\BeaconPeriod,                     min,                 0, "20"
HKR, Ndi\params\BeaconPeriod,                     max,                 0, "1000"
HKR, Ndi\params\BeaconPeriod,                     step,                0, "1"
HKR,,                                             BeaconPeriod,        0, "100"

HKR, Ndi\params\UseWZCS,                          ParamDesc,           0, "API to use"
HKR, Ndi\params\UseWZCS,                          type,                0, "enum"
HKR, Ndi\params\UseWZCS,                          default,             0, "1"
HKR, Ndi\params\UseWZCS\enum,                     0,                   0, "Custom API"
HKR, Ndi\params\UseWZCS\enum,                     1,                   0, "WZCS API"
HKR, ,                                            UseWZCS,             0, "1"

HKR,Ndi\params\RadioOnOff,                        ParamDesc,           0, "Radio On/Off"
HKR,Ndi\params\RadioOnOff,                        type,                0, "enum"
HKR,Ndi\params\RadioOnOff,                        default,             0, "1"
HKR,Ndi\params\RadioOnOff\enum,                   0,                   0, "OFF"
HKR,Ndi\params\RadioOnOff\enum,                   1,                   0, "ON"
HKR,,                                             RadioOnOff,          0, "1"


;*******************************************************
; Driver parameters for WinXP
;*******************************************************
[WinXP.Params]
HKR, ,                                            Operating_Mode,      0, "1"
HKR, ,                                            ESSID,               0, ""
HKR, ,                                            EncryptionLevel,     0, "0"

HKR, Ndi\params\PreambleType,                     ParamDesc,           0, "Preamble Type"
HKR, Ndi\params\PreambleType,                     default,             0, "2"
HKR, Ndi\params\PreambleType,                     type,                0, "enum"
HKR, Ndi\params\PreambleType\enum,                0,                   0, "Long"
HKR, Ndi\params\PreambleType\enum,                1,                   0, "Short"
HKR, Ndi\params\PreambleType\enum,                2,                   0, "Auto"
HKR, ,                                            PreambleType,        0, "2"

HKR, Ndi\params\Rate,                             ParamDesc,           0, "Rate (Mbps)"
HKR, Ndi\params\Rate,                             default,             0, "4"
HKR, Ndi\params\Rate,                             type,                0, "enum"
HKR, Ndi\params\Rate\enum,                        0,                   0, "1"
HKR, Ndi\params\Rate\enum,                        1,                   0, "2"
HKR, Ndi\params\Rate\enum,                        2,                   0, "5.5"
HKR, Ndi\params\Rate\enum,                        3,                   0, "11"
HKR, Ndi\params\Rate\enum,                        4,                   0, "Auto"
HKR, ,                                            Rate,                0, "4"

HKR, Ndi\params\RTS_Threshold,                    ParamDesc,           0, "RTS Threshold"
HKR, Ndi\params\RTS_Threshold,                    default,             0, "2347"
HKR, Ndi\params\RTS_Threshold,                    type,                0, "int"
HKR, Ndi\params\RTS_Threshold,                    min,                 0, "0"
HKR, Ndi\params\RTS_Threshold,                    max,                 0, "2347"
HKR, Ndi\params\RTS_Threshold,                    step,                0, "1"
HKR, ,                                            RTS_Threshold,       0, "2347"

HKR, Ndi\params\Frag_Threshold,                   ParamDesc,           0, "Fragmentation Threshold"
HKR, Ndi\params\Frag_Threshold,                   default,             0, "2346"
HKR, Ndi\params\Frag_Threshold,                   type,                0, "int"
HKR, Ndi\params\Frag_Threshold,                   min,                 0, "256"
HKR, Ndi\params\Frag_Threshold,                   max,                 0, "2346"
HKR, Ndi\params\Frag_Threshold,                   step,                0, "1"
HKR, ,                                            Frag_Threshold,      0, "2346"

HKR, Ndi\params\PowerMgmtMode,                    ParamDesc,           0, "802.11 Power Save"
HKR, Ndi\params\PowerMgmtMode,                    type,                0, "enum"
HKR, Ndi\params\PowerMgmtMode,                    default,             0, "0"
HKR, Ndi\params\PowerMgmtMode\enum,               0,                   0, "Disabled"
HKR, Ndi\params\PowerMgmtMode\enum,               1,                   0, "Enabled"
HKR, ,                                            PowerMgmtMode,       0, "0"

HKR, Ndi\params\UseWZCS,                          ParamDesc,           0, "API to use"
HKR, Ndi\params\UseWZCS,                          type,                0, "enum"
HKR, Ndi\params\UseWZCS,                          default,             0, "0"
HKR, Ndi\params\UseWZCS\enum,                     0,                   0, "Custom API"
HKR, Ndi\params\UseWZCS\enum,                     1,                   0, "WZCS API"
HKR, ,                                            UseWZCS,             0, "0"

;*******************************************************************************
; Strings Section
;*******************************************************************************
[Strings]
VENDOR         = "Belkin"
DeviceDesc     = "Belkin 11Mbps Wireless USB Network Adapter"
ServiceName    = "Belkin 11Mbps Wireless USB Network Adapter"
DriverDiskName = "Belkin 11Mbps Wireless USB Network Adapter Installation Disk"
Help_Text      = "Belkin 11Mbps Wireless USB Network Adapter lets you set up easily and operate a Wireless LAN compliant with 802.11 Standard. It operates in the license free 2.4 GHz ISM band and achieves a peak data rate of 11Mbps.""

---

### Post by dnguyen527 on 2007-03-31
> **jfinkels said:**
> Don't bother, I found it myself: Here's what you need to do:

Search for the section in the file named "Win XP Section". It will be surrounded by a bunch of asterisks.

```

;******************************************************************************\
*
; Win XP section
;******************************************************************************\
*
[DrvInstXP.Ndi1.NTx86]
Characteristics = 0x84                     ; NCF_HAS_UI | NCF_PHYSICAL
BusType         = 15                       ; USB
AddReg          = WinXP.Reg, WinXP.Params
;CopyFiles       = CopyFile.XP.Sys
[...]

```

Where it says ";CopyFiles       = CopyFile.XP.Sys", delete the semicolon at the beginning of that line.

Alright, I found that. Do I just do it for that 1st one. There is 2 more that look the same. 

The person who told me about Double Posting - I thought my first one didnt work. I am really sorry abou that. I understand.

---

### Post by jfinkels on 2007-03-31
see my post above this one.

ps. You might consider editing the post that i told you to make so that it won't be so long (my mistake for telling you to post a long file! :D)

---

### Post by dnguyen527 on 2007-03-31
What do I do after that? Do I just save?

---

### Post by jfinkels on 2007-03-31
> **dnguyen527 said:**
> Alright, I found that. Do I just do it for that 1st one. There is 2 more that look the same. 

The person who told me about Double Posting - I thought my first one didnt work. I am really sorry abou that. I understand.

It's okay! We're here to help :).

According to the directions on the site you posted, just delete the semicolon for the line that says "CopyFile.XP.Sys" in the Win XP Section. Don't worry about the others.

> 
What do I do after that? Do I just save?


Yes, just save it, then follow the rest of the directions.

---

### Post by dnguyen527 on 2007-03-31
Err - It says I cant save it.

I'll start over again. I've been doing this for like 10 hours now. : (

---

### Post by dnguyen527 on 2007-03-31
Are there suppose to be "Lock" images over all these unzipped files? I think that might be a problem for the saving. Can I unlock it?

---

### Post by dnguyen527 on 2007-03-31
Ok, Ignore those top 2 posts. I saved it. 

Now I typed the command:

ndiswrapper -i bkusb.in_

Then this list comes up telling me all these comands

Then I typed: 

ndiswrapper -m 

modprobe config already contains alias directive

Then I typed 

modprobe ndiswrapper 

Then a huge error copes up and says Operation not permitted

Then I just continued and typed ifdown wlan0 

Permission Denied

Linux hates me.

---

### Post by jfinkels on 2007-03-31
You know what, I think I was wrong, I am truly sorry:

At the bottom of the Win XP Section there is some code that looks like this
```

;[CopyFile.XP.Sys]
;bkusbxp.sys,,,2

```
Remove the semicolons so that it looks like this:
```

[CopyFile.XP.Sys]
bkusbxp.sys,,,2

```
I am not sure about the three lines that look like this:
```

;CopyFiles       = CopyFile.XP.Sys

```
The directions are vague. I would say, remove the semicolon on all three.

EDIT: STAY TUNED and I will go through very clearly how to perform the commands required in a another post.

---

### Post by annda on 2007-03-31
also, for modprobe and ifdown/ifup i suggets using sudo, as those commands should be run as root. so:

sudo modprobe .......
sudo ifdown ...........

---

### Post by dnguyen527 on 2007-03-31
Ok, I made those edits.

---

### Post by jfinkels on 2007-03-31
After removing the semicolons from that file, type the following command in the terminal:
```

sudo ndiswrapper -i bkusb.in_

```
Type your password if it asks for it. If there are problems, post them here. 

Then type the following in the terminal:
```

sudo ndiswrapper -m

```

Then type this:
```

sudo modprobe ndiswrapper

```
This loads the ndiswrapper driver.

Then type the following to reset your wireless connection: 
```

sudo ifdown wlan0 && sudo ifup wlan0

```

---

### Post by dnguyen527 on 2007-03-31
> **jfinkels said:**
> After removing the semicolons from that file, type the following command in the terminal:
```

sudo ndiswrapper -i bkusb.in_

```
Type your password if it asks for it. If there are problems, post them here. 


- Ok here it says - bkusb.in_ is already in use. Use -e to remove it (I've tried that before and it said permission denied or somewhere on the lines of that)

Then type the following in the terminal:
```

sudo ndiswrapper -m

```

When I typed that after getting the message above it says:

modprobe config already contains alias directive

Then type this:
```

sudo modprobe ndiswrapper

```
This loads the ndiswrapper driver.

When I typed this it said: FATEL: Error inserting ndiswrapper (lib/moduels/2.6.17-10-generic/kernal/drivers/net/ndiswrapper/ndiswrapper.ko) invalid argument

Then type the following to reset your wireless connection: 
```

sudo ifdown wlan0 && sudo ifup wlan0

```

I didnt try that yet because of all the errors

---

### Post by dnguyen527 on 2007-03-31
So I continued even with the erros and typed this code:

sudo ifdown wlan0 && sudo ifup wlan0

and now it is currently listening and doing some Discover stuff

It says

No DHCPOFFERS received
No working leases in presistent database - sleeping.

---

### Post by jfinkels on 2007-03-31
EDIT: oh i see your errors are inside the quote

EDIT:

Okay, well, I don't know anything about ndiswrapper beyond what it's function is, so hopefully someone else will come along that know about it.

To remove bkusb.in, type:
```

sudo ndiswrapper -e bksub.in_

```

After that, try to install it again:
```

sudo ndiswrapper -i bkusb.in_

```

---

### Post by dnguyen527 on 2007-03-31
I started over again and deleted all the drivers in ndiswrapper from all my screw ups.

I redid the code

sudo ndiswrapper -i bkusb.in_

Then it said it installed.

I continued on with the directions

sudo ndiswrapper -m
sudo modprobe ndiswrapper

then the ifdown codes

Got the same errors on all of them that I posted above.

---

### Post by dnguyen527 on 2007-03-31
I am pretty sure I have ndiswrapper installed.

i can type it in the Terminal and I get the list of its commands like

-e delete
-L list
-i Install

Etc. 

Anyway to check? 

Not given up on me yet are you? Haha thanks so much so far

---

### Post by jfinkels on 2007-03-31
yes you have it installed, and yes I want to see this work :)

type ```
ndiswrapper -l
``` and post the output here. It will list installed drivers. Note that there's a little button with a sharp symbol ("#") when you're posting a new message to the forum. click that and two little tags pop up in the message box that look like this but with square brackets: <CODE></CODE>. Post any output that you copy from your system inside these tags, so that we can distinguish it from message text.

---

### Post by dnguyen527 on 2007-03-31
Ok It says:


```


Installed ndis drivers:

bkusb.in_   driver present, hardware present


```

Sounds good? :)

---

### Post by jfinkels on 2007-03-31
> **dnguyen527 said:**
> Ok It says:
```

Installed ndis drivers:

bkusb.in_   driver present, hardware present

```
Sounds good? :)

Sounds very good, but unfortunately, I don't think I can help you from here. I think the best thing you can do is copy and paste the error message you get when you try the next command ("sudo ndiswrapper -m"), and wait and see if somebody else posts. In the meantime try searching with Google, look at [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/), and if you can't figure it out in a day or so, post a new topic in the forum, with a link to this thread :D

---

### Post by dnguyen527 on 2007-03-31
Oh man.

Alright, thanks!

---

### Post by dnguyen527 on 2007-03-31
Hey,

Now instead of an error, nothing comes up when I put in the code

```
sudo modprobe ndiswrapper
```

Whats going on?????????

---

### Post by goghgoner on 2007-03-31
This usb card must be a big pain. Looks like someone got this to work another way:

[http://ubuntuforums.org/showthread.php?t=5164](http://ubuntuforums.org/showthread.php?t=5164)

If that doesn't work and you are breaking down, maybe try PCLinuxOS.

---

