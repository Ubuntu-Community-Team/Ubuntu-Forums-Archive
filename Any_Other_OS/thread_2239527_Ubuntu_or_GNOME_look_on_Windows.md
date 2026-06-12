---
title: "Ubuntu or GNOME look on Windows"
date: 2014-08-14
forum: Any Other OS
---

### Post by Jonathan Precise on 2014-08-14
Hello forums community!

I'm stuck dual-booting Ubuntu 14.04 LTS with Windows 8.1, with Ubuntu as the primary OS. However, there are some apps that only exist in Windows. One great example is Sony PC Companion, which is the software to update my phone, as my phone does not support OTA upgrades. Another great example is PortableApps. So I'm stuck with windows until they make alternatives for these programs (And no, I don't want the **WIN**dows **E**mulator. If viruses infect my PC, at least let it only infect Windows! Not my perfectly good Ubuntu installation). However, I don't like the Windows 8 look and feel. For the past year I've dealt with it, until I found out about SkinPack.

SkinPack is an app to change completely the look and feel of my Windows. There are themes that they make, and one installs the themes to make windows look the way the person designs them. One theme is the "Ubuntu" theme. So I figured that I should make windows look like ubuntu, so I could feel right at home. It unfortunately **told me to turn off any antivirus during the installation, as it would detect it as a false positive due to modifying system files**. However, since I heard all Avast AVs had less false positives than its competitors, I decided to keep Avast Internet Security on. Unfortunately, during the download, an Avast notification came saying "Download blocked: Threat Win32:Malware.Gen" or something similar. Checking through HerdProtect online, it says it is a **P**otentially **U**nwanted **P**rogram

My question is: Who should I trust? Is it a false positive or is it malware/virus/spyware, etc.? Has anyone used this before and tell my if it is a virus/malware, etc.?

Thanks in advance.

-Jonathan

---

### Post by PondPuppy on 2014-08-15
I don't know exactly where you attempted to download the skinpack application. Some versions apparently install adware of some kind: [http://www.herdprotect.com/skinpack-installer8-win8-ver8_downloader-4dlfevco.exe-64c1fe91916f76db44ff0c9a0fbce3d50570716b.aspx](http://www.herdprotect.com/skinpack-installer8-win8-ver8_downloader-4dlfevco.exe-64c1fe91916f76db44ff0c9a0fbce3d50570716b.aspx) 

You may be able to find a 'clean' version somewhere. I don't have any first-hand experience to offer, though.

---

### Post by sffvba[e0rt on 2014-08-16
You decided to install and use the AV and Mallware applications, not taking heed when they warn you seems a bit silly.

Oh, and **W**ine **I**s **N**ot an **E**mulator ;)

---

### Post by Jonathan Precise on 2014-08-16
> **PondPuppy said:**
> I don't know exactly where you attempted to download the skinpack application. Some versions apparently install adware of some kind: [http://www.herdprotect.com/skinpack-installer8-win8-ver8_downloader-4dlfevco.exe-64c1fe91916f76db44ff0c9a0fbce3d50570716b.aspx](http://www.herdprotect.com/skinpack-installer8-win8-ver8_downloader-4dlfevco.exe-64c1fe91916f76db44ff0c9a0fbce3d50570716b.aspx) 

You may be able to find a 'clean' version somewhere. I don't have any first-hand experience to offer, though.

I found it on [SkinPack.com]("http://skinpacks.com/download/windows-7/ubuntu-skin-pack/"). Would that be the clean version?

---

### Post by Jonathan Precise on 2014-08-16
> **not found said:**
> You decided to install and use the AV and Malware applications, not taking heed when they warn you seems a bit silly.

Oh, and **W**ine **I**s **N**ot an **E**mulator ;)

Yeah it does seem a bit silly, but I've had cases where I'm going to a legitimate website (not by clicking a url, but by typing the site in the url bar), and my AV saying that it's a phishing website. I wanted to know if this is the same.

Thanks for the replies!

-Jonathan

---

### Post by NilPointer on 2014-08-22
Well, Malware.Gen indicates heurestic analysis. Since what SkinPack seems to do is change look and fell, there's probably a lot of code that intercepts input events and drawing routines, which might seem suspicious to the AV. I can suggest you checking the file on the VirusTotal. If only 2-3 AVs detect it as malware, then it's probably a false positive. If there more detections (or even majority of AVs detect it as a malware), then there is a very high likelihood, that it is indeed a malware.

---

### Post by Jonathan Precise on 2014-08-22
17/49 say it's a virus:

[QUOTE=VirusTotal][TABLE="class: grid, width: 500, align: center"]
[TR]
[TD]Avast[/TD]
[TD]Win32:Malware-gen[/TD]
[TD]20140822[/TD]
[/TR]
[TR]
[TD]CAT-QuickHeal[/TD]
[TD]Trojan.Vflooder.g8[/TD]
[TD]20140822[/TD]
[/TR]
[TR]
[TD]Commtouch[/TD]
[TD]W32/Trojan.SCNE-6301[/TD]
[TD]20140822[/TD]
[/TR]
[TR]
[TD]DrWeb[/TD]
[TD]Trojan.DownLoader11.14929[/TD]
[TD]20140822[/TD]
[/TR]
[TR]
[TD]ESET-NOD32[/TD]
[TD]Win32/Somoto.L[/TD]
[TD]20140822[/TD]
[/TR]
[TR]
[TD]F-Prot[/TD]
[TD]W32/Trojan3.IZC[/TD]
[TD]20140822[/TD]
[/TR]
[TR]
[TD]Fortinet[/TD]
[TD]Riskware/Sim[/TD]
[TD]20140822[/TD]
[/TR]
[TR]
[TD]GData[/TD]
[TD]Win32.Trojan.Agent.021DZE[/TD]
[TD]20140822[/TD]
[/TR]
[TR]
[TD]Ikarus[/TD]
[TD]Trojan.Win32.Kryptik[/TD]
[TD]20140822[/TD]
[/TR]
[TR]
[TD]Kaspersky[/TD]
[TD]HEUR:Trojan.Win32.Generic[/TD]
[TD]20140822[/TD]
[/TR]
[TR]
[TD]Malwarebytes[/TD]
[TD]Trojan.Agent[/TD]
[TD]20140822[/TD]
[/TR]
[TR]
[TD]McAfee[/TD]
[TD]Artemis!3B41F559D566[/TD]
[TD]20140822[/TD]
[/TR]
[TR]
[TD]McAfee-GW-Edition[/TD]
[TD]Artemis!3B41F559D566[/TD]
[TD]20140822[/TD]
[/TR]
[TR]
[TD]NANO-Antivirus[/TD]
[TD]Trojan.Win32.Inject1.ddzkkr[/TD]
[TD]20140822[/TD]
[/TR]
[TR]
[TD]Qihoo-360[/TD]
[TD]Win32/Trojan.e6d[/TD]
[TD]20140822[/TD]
[/TR]
[TR]
[TD]Symantec[/TD]
[TD]WS.Reputation.1[/TD]
[TD]20140822[/TD]
[/TR]
[TR]
[TD]TrendMicro-HouseCall[/TD]
[TD]TROJ_GEN.R0CBB01HC14[/TD]
[TD]20140822[/TD]
[/TR]
[/TABLE][/QUOTE]

As I'm seeing, most of them detect it as a virus/malware. Does anyone know of another program that does this function? (other than seamless VirtualBox mode)

Thanks for the online virus scanner!

-Jonathan

---

### Post by Jonathan Precise on 2014-08-25
Update: Tried rocket launcher. No ubuntu-ish theme that I saw or searched for in their themes site, so uninstalled.

Any suggestions?

---

### Post by Jonathan Precise on 2014-12-24
Please?

EDIT: Since I don't use Windows as much as I used it before, I shall mark this as solved.

---

