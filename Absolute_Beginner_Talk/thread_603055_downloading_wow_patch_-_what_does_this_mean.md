---
title: "downloading wow patch - what does this mean?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Serisis on 2007-11-04
I got this.  I think it's downloading really slow...whats up with it?
```

fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7cc50000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cc50000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ede4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ed18,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f34c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f554,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f540,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f05c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmAssociateContextEx (0x30024, (nil), 16): stub
christine@ubuntu:~$ fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4

http error code = 404
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
err:ole:CoGetClassObject class {e2085f28-feb7-404a-b8e7-e659bdeaaa02} not registered
err:ole:CoGetClassObject class {e2085f28-feb7-404a-b8e7-e659bdeaaa02} not registered
err:ole:create_server class {e2085f28-feb7-404a-b8e7-e659bdeaaa02} not registered
err:ole:CoGetClassObject no class object {e2085f28-feb7-404a-b8e7-e659bdeaaa02} could be created for context 0x7
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4

christine@ubuntu:~$ fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
```

---

### Post by rudeboyskunk on 2007-11-04
It's timing out, so the server from which you are downloading must be down.  Just wait a few minutes and keep trying.

Are you playing WoW with wine or Cedega?

---

### Post by Serisis on 2007-11-04
> **rudeboyskunk said:**
> It's timing out, so the server from which you are downloading must be down.  Just wait a few minutes and keep trying.

Are you playing WoW with wine or Cedega?

it says it should be done downloading in about an hour...should i cancel and try again later or find another site to get the patches off of them?  

i found this site: [http://www.wowwiki.com/Patch_mirrors](http://www.wowwiki.com/Patch_mirrors) but should i be scared of the disclaimer?  "DISCLAIMER: Patch mirrors are neither guaranteed to be working, nor to be virus or trojan free!

    * WoWWiki cannot be held responsible for any damage these files may cause to your computer. USE THEM AT YOUR OWN RISK. "

i'm using wine.

---

### Post by rudeboyskunk on 2007-11-04
Ordinarily I would say do not worry about viruses, but wine warns you explicitly to worry about them because they are implementing the Windows API, and your system could break (or at least all of your Windows programs running in wine).

I run WoW using wine also, and usually whenever it takes a long time to download the patches, I just wait 15-20 minutes and try again.  Nighttimes are always toughest because EVERYBODY AND THEIR MOTHER wants to play.  But a little patience will help.  If it doesn't solve your problem, I apologize in advance for wasting your time :(

---

### Post by Serisis on 2007-11-04
> **rudeboyskunk said:**
> Ordinarily I would say do not worry about viruses, but wine warns you explicitly to worry about them because they are implementing the Windows API, and your system could break (or at least all of your Windows programs running in wine).

I run WoW using wine also, and usually whenever it takes a long time to download the patches, I just wait 15-20 minutes and try again.  Nighttimes are always toughest because EVERYBODY AND THEIR MOTHER wants to play.  But a little patience will help.  If it doesn't solve your problem, I apologize in advance for wasting your time :(


Oh man... thanks though.  Maybe i'll just suffer the long download...

---

### Post by Colro on 2007-11-04
I'd -REALLY- reccomend you to download the patch from a third party place such as Fileshack or Fileplanet, the official downloader is a bit buggy with WINE.

---

### Post by mivo on 2007-11-04
> **Serisis said:**
> i found this site: [http://www.wowwiki.com/Patch_mirrors](http://www.wowwiki.com/Patch_mirrors) but should i be scared of the disclaimer?  "DISCLAIMER: Patch mirrors are neither guaranteed to be working, nor to be virus or trojan free!

The patch files have checksums. Back when I still played WoW, I downloaded perhaps two patches in two years through the official downloader, and all the others from alternate sites and mirrors. The official downloader was always painfully slow and buggy.

---

### Post by Serisis on 2007-11-04
> **Colro said:**
> I'd -REALLY- reccomend you to download the patch from a third party place such as Fileshack or Fileplanet, the official downloader is a bit buggy with WINE.

Okay so let's say I go to that site and download the patches...how do i know what patches i need? Is  World of Warcraft Manual Patch 2.2.2 to 2.2.3 - US/AUS
 enough from fileshack?

---

### Post by Serisis on 2007-11-04
Okay well i looked on those two sites file shack and fileplanet and i got some patches, but i need an even earlier patch to use those.  so then i tried the blizzard downloader again and i got this message

```
 Blizzard Updater was unable to read the file "C:\Program Files\World of Warcraft\Data\common.MPQ". This error may be caused by problems with the media or drive at C:\--for example, a scratched or dirty CD-ROM/DVD-ROM, hard drive corruption, or a networking problem while downloading the update. (The data being read was "Item\ObjectComponents\HEAD\Helm_Goggles_C_01_GnM.m2", and the error code was 0.) If this problem persists, you may be able to solve it by uninstalling and then reinstalling the game. If you are unable to correct this problem, please contact Blizzard Technical Support. (Converter::Load)
 To check this installation for problems, click the "Repair" button. The Repair tool can automatically fix many update errors.

```

I'm guessing thats becuase wine is buggy with it?

What do i do now? google some patch names or does anyone know of a good site thats got earlier patches?

---

### Post by anson123 on 2008-04-02
Hi,

I have Ubuntu 7.10 32 bit.

I am trying to update from WOW 2.0.0 to 2.4.0

The WOW updater successfully downloaded the 2.4.0 patch, but then when the installer comes up, the installer flashes the message:

   "Waiting for files to close..."

I try to close any open windows, to no avail.

Can anyone help me out??

Thanks!

---

### Post by cykotiktek on 2008-04-02
This is how i update my WoW i start the downloader and just copy the exact name of the file that it is downloading.  hit cancel punch the name into google and search I have never had a problem with 3rd party downloads.  Even on windows i do this because i can grab a huge patch in a couple of minutes instead of an hour.

---

