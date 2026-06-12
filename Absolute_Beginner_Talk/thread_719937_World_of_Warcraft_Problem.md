---
title: "World of Warcraft Problem"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by tikas on 2008-03-09
Hello, I am a relatively new user to Ubuntu but have played around with it before - this time I've gone all the way and switched my laptop to Ubuntu completely, I have sorted out most of my major problems by searching around the forums, but this problem I have not encountered (even after following many help tutorials on the internet and this forum and searching around for along time):

when running world of warcraft under wine the animations/graphics are "split" into certain parts - for example on the character the body will twist but the arms will stay still and disconnect from the main body, Also the world itself is textured incorrectly and my spell icons do not appear correctly. There is also severe FPS lag.
I know this laptop can play WoW as it played it without any problems on windows XP.

Here is a screen shot of the game running:
[http://www.cubeupload.com/files/1e9141screenshot.png](http://www.cubeupload.com/files/1e9141screenshot.png)
(My Character is facing the screen)

Here is my config.wtf file
```
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x768"
SET gxRefresh "60"
SET hwDetect "0"
SET doodadAnim "0"
SET lodDist "100.000000"
SET SmallCull "0.010000"
SET DistCull "350.000000"
SET frillDensity "8"
SET farclip "357"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "0.900000"
SET movie "0"
SET realmList "eu.logon.worldofwarcraft.com"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enGB"
SET gxMultisampleQuality "0.000000"
SET accountName "tikas001"
SET expansionMovie "0"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET readTerminationWithoutNotice "1"
SET coresDetected "1"
SET videoOptionsVersion "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET patchlist "eu.version.worldofwarcraft.com"
SET realmName "Arathor"
SET lastCharacterIndex "2"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET gameTip "5"
SET gxWindow "1"
SET gxCursor "0"
SET checkAddonVersion "0"
SET Gamma "1.000000"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET groundEffectDist "70"
SET minimapZoom "0"
SET uiScale "1"
```and here is what happens when I run the Game in the terminal using the same command the launcher was given as default:
```
user@name-laptop:~$ env WINEPREFIX="/home/sam/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe" 
fixme:shdocvw:WebBrowser_QueryInterface (0x12b6e8)->({bd1ae5e0-a6ae-11ce-bd37-504200c10000} 0x33e450) interface not supported
fixme:shdocvw:PersistStreamInit_Load (0x12b6e8)->(0x33e41c)
fixme:shdocvw:OleControl_FreezeEvents (0x12b6e8)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x12b6e8)->(0)
fixme:shell:IShellLinkA_fnGetPath (0x12d1d8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x12d1b8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x12d1b8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x12dac8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x12d1b8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x12d1b8): WIN32_FIND_DATA is not yet filled.
err:module:map_image Could not map section .text, file probably truncated
err:module:import_dll Loading library smime3.dll (which is needed by L"C:\\windows\\gecko\\0.1.0\\wine_gecko\\components\\pipnss.dll") failed (error c000007b).
err:module:map_image Could not map section .text, file probably truncated
err:module:import_dll Loading library smime3.dll (which is needed by L"C:\\windows\\gecko\\0.1.0\\wine_gecko\\components\\pipnss.dll") failed (error c000007b).
err:module:map_image Could not map section .text, file probably truncated
fixme:iphlpapi:NotifyAddrChange (Handle 0x78a039f8, overlapped 0x78a039dc): stub
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x12b77c)->((null) 1 0x33dbbc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12b77c)->((null) 25 2 0x33dbd0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12b77c)->((null) 26 2 0x33dbd0 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x12b77c)->(0x33dc0c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12b77c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33dcc8 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x143818)->(L"" L"" 0 0x33dcfc)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0x143818)->(0x33dd00 0x33dd10)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12b77c)->((null) 29 2 0x33e9a4 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x12b77c)
fixme:shdocvw:ClientSite_GetContainer (0x12b77c)->(0x33e9c4)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12b77c)->(0xb7eef109)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12b77c)->((null) 25 2 0x33e8f8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12b77c)->((null) 26 2 0x33e8f8 (nil))
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:shdocvw:ClOleCommandTarget_Exec (0x12b77c)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12b77c)->((null) 28 2 0x33e950 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12b77c)->((null) 26 2 0x33e984 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12b77c)->((null) 29 2 0x33e994 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12b77c)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12b77c)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12b77c)->(0x7bc9e6cd)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x12b6e8)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x143d50)->((nil))
fixme:shdocvw:OleObject_Close (0x12b6e8)->(1)
fixme:shell:DllCanUnloadNow stub
user@name-laptop:~$ fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed84,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34ecac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f40c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f580,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f55c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x34f124,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:reg:GetNativeSystemInfo (0x374027e4) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x780cf4a4) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x34d1a4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34d200,0x00000000), stub!
fixme:imm:ImmAssociateContextEx (0x3004a, (nil), 16): stub
user@name-laptop:~$ 

```More information can be given at request.
Any help appreciated,
Many Thanks,
Tikas

---

### Post by JoshuaRL on 2008-03-09
I don't run WOW, so I'm not sure if this will help, but I saw a DLL error in there.  Go [here to download it,](http://www.dll-files.com/dllindex/dll-files.shtml?smime3) and put it in "C:\\Windows\system32".  That might help.

Also, if you have a screenshot or any other large picture to post you might want to attach it instead of posting directly.  In the post page near the bottom there's a Manage Attachments button.  You can use that to attach things.

---

### Post by tikas on 2008-03-09
thank you for your help but unfortunately that did not solve my graphics problem, but it did eliminate one of the errors, I'll now look through the other .dll's that it errord with and will see if that works

and next time i will bear in mind the image attachment rather than a large image filling the screen

thanks again
tikas

---

### Post by JoshuaRL on 2008-03-09
I would suggest you try messing around with the settings in Applications->Wine->Configure Wine.  Doesn't always work, but sometimes it does.

---

### Post by tikas on 2008-03-09
That didn't seem to work either :(

---

### Post by tikas on 2008-03-10
I don't Know if this will help but I am running wine-0.9.46
The problem is still there, any help appreciated
has anyone else ever had this problem?

Tikas

---

### Post by merlyn on 2008-03-10
I don't have a direct answer to your problem, sorry.

However any hassles with WoW & wine that I experienced in the past have been resolved by browsing / posting on [this]("http://ubuntuforums.org/showthread.php?t=579378") thread.

It's quite a long thread by now as a moderator decided to merge a number of WoW related threads.

Cheers.

---

### Post by tikas on 2008-03-10
Yay! fixed it, just renamed my config.wtf file to config1111.wtf and allowed Wow to create a new one. this seems to of fixed the problem, however it no-longer runs in Open Gl mode....  this seems to cause a problem with FPS

---

### Post by gi2k15 on 2008-03-10
OpenGL is recommended when running WoW on Linux. You can start the game using OpenGL using the command:

```
wine wow.exe -opengl
```

inside your game's folder. Or you can edit your config.wtf and add the line:

```
SET gxApi "opengl"
```

---

### Post by tikas on 2008-03-10
humm, with the ```
SET gxApi "opengl" 
```it goes back to the same animation rendering problem
without it, the game runs... but it has terrible fps advraging 5 or 6 max....
anyone have any ideas of how to overcome this problem? do I need to install something for open gl or whatever?

any help appreciated
thanks
tikas

---

### Post by tikas on 2008-03-11
update on the problem - open gl produces thing like the image above, without it there is 4 fps and even setting it to  d3d (direct3d) still has major lag issues... I have messed around with settings in wine and in the config.wtf file but nothing seems to have worked yet. perhaps someone can think of settings that work..... I thought this may be of use to some of you:

```
user@name-laptop:~$ lshw
name-laptop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 502MB
     *-cpu
          product: Intel(R) Celeron(R) M CPU        440  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.14.12
          serial: 0000-06EC-0000-0000-0000-0000
          size: 400MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc up pni monitor tm2 xtpr
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: BCM94311MCG wlan mini-PCI
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth1
                version: 01
                serial: 00:19:7e:a3:d0:e6
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic ip=192.168.1.180 latency=0 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 1
                bus info: pci@0000:06:01.0
                logical name: eth0
                version: 02
                serial: 00:16:d4:e4:74:26
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=b44 driverversion=1.01 latency=64 module=b44 multicast=yes
           *-pcmcia
                description: CardBus bridge
                product: CB-712/4 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0000:06:04.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-memory:0 UNCLAIMED
                description: FLASH memory
                product: ENE PCI Memory Stick Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.1
                bus info: pci@0000:06:04.1
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: cap_list
                configuration: latency=0 maxlatency=4 mingnt=1
           *-system
                description: Generic system peripheral
                product: ENE PCI Secure Digital Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.2
                bus info: pci@0000:06:04.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=64 maxlatency=72 mingnt=32 module=sdhci
           *-memory:1 UNCLAIMED
                description: FLASH memory
                product: FLASH memory: ENE Technology Inc:
                vendor: ENE Technology Inc
                physical id: 4.3
                bus info: pci@0000:06:04.3
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: cap_list
                configuration: latency=0 maxlatency=4 mingnt=1
           *-memory:2
                description: FLASH memory
                product: SD/MMC Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.4
                bus info: pci@0000:06:04.4
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: cap_list
                configuration: driver=sdhci latency=0 maxlatency=72 mingnt=32 module=sdhci
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

```I would also like to repeat that this worked fine when the same laptop was on XP
I was wondering if it was the drivers for the graphics? i am using the  "intel experimental" one which is the default.
any one have any ideas?
Tikas

---

### Post by PmDematagoda on 2008-03-11
Please bear in mind that large pictures may not be used on Ubuntu Forum threads.

The picture has been removed with the link still left intact.

---

### Post by tikas on 2008-03-11
sorry, didnt realise it would come up as big, and couldnt work out what to do with it once it was

Wow still not working :( been trying diffrent things for ages

---

### Post by merlyn on 2008-03-11
> **tikas said:**
> sorry, didnt realise it would come up as big, and couldnt work out what to do with it once it was

Wow still not working :( been trying diffrent things for ages

Have you checked the thread that I mentioned in my earlier post?

That is where you will find the most comprehensive range of solutions to WoW problems running under Wine.

---

### Post by tikas on 2008-03-13
sorry, didnt notice it was a hyper link!
 
reading it now, will post back with how it goes.

---

### Post by tikas on 2008-03-23
I haven't quite got the Fps Problems fixed, but if i run it with wine debug at the same time it removes a lot of the errors,
 also if the launcher i am clicking has
 -opengl at the end of it it sorts out the graphis problem. (all these ideas i have from the post mentioned by merlyn) I have also got rid of visual effects and that increased my fps too, is there any other things anyone can think of that will up my fps?

---

