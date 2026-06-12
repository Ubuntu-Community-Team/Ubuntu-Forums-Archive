---
title: "Can't load some websites on Windows PC that connect just fine on Laptop"
date: 2011-05-05
forum: Any Other OS
---

### Post by eldonkr on 2011-05-05
I wasn't sure if I should post this in this section or not. I wasn't even sure if I should post this on this forum or not, but this is the only forum that I'm a member of, I don't like signing up for new things :-?.

Anyway, I'm not entirely certain when this problem first started occurring. I do almost all of my web browsing on this netbook. At first I just noticed a few sites wouldn't load and didn't think anything of it and moved to the other computer. At first I thought it was just certain media type websites. (Websites for the local video store, some movie and video game sites, a few online stores). I'm just now realizing the full extent of it, my cousin comes over to use my computer from time to time. Lately it's been to fill out job applications and check on his unemployment online, and he's unable to connect to a lot of the sites to fill out applications, and some of the .gov websites for his unemployment time out, too.

A friend of mine started playing this new game online, and since he lives in Texas I've started playing a lot of the same games he does to stay in touch and the website for this game can't be connected to by my Windows box either and therefore I can't access their servers to play the game either.

I'm not sure what is going on but it's really starting to bother me.

---

### Post by wojox on 2011-05-05
I upgraded to IE9 and found some incompatibility issues. Loaded Firefox and it went smooth. Do you run ccleaner? It's a pretty cool application to clean up.

---

### Post by eldonkr on 2011-05-06
Yes, I have CCleaner. I don't use IE or Firefox, I use Google Chrome. Over the last four years or so the only thing I ever used Internet Explorer for was to download Firefox, but I switched to Chrome a few months ago. The problem persists over all the browsers though. When I try to ping the websites that time out it tells me that it can't be reached.

---

### Post by slooksterpsv on 2011-05-06
Google chrome used to use it's own DNS servers not sure if it still does. I would test the sites with Internet Explorer and see if they load, if they don't you probably have either a DNS issue with your ISP or a DNS hijacker on the computer (virus/spyware), or corrupt dns cache.

Either way here's what to test first:
Try IE to access the sites, if you can, it's an issue with Chrome, if not continue
Try flushing your DNS and checking your dns settings, to flush the DNS do the following:
Click Start -> Type in CMD, right-click on CMD and choose run as administrator, type in the following commands:
```

ipconfig /flushdns
ipconfig /release
ipconfig /renew
ipconfig /registerdns
netsh int ip reset reset.txt
netsh winsock reset catalog

```
Restart the computer, try the sites again, if it still fails continue.
Go to Start -> Control Panel -> Classic (or Small Icon View) -> Network and Sharing Center -> Manage Network Connections (Change Adapter Settings) -> Right-click on your device (wireless or local area connection) -> Go to Properties -> Double-click on Internet Protocol (TCP/IP) version 4 (or single click then go to properties). Make sure DNS isn't set there (there's also an advanced button you can check the DNS there as well). If those aren't set continue to the next area.
Download HiJackThis (google it) and run it, you should be able to scan and save to a log, post the results here an I can look through it and see if there's any bad items that are hijacking your computer (limited, but still valuable).
Download Malwarebytes from [http://www.malwarebytes.org/](http://www.malwarebytes.org/) and SuperAntiSpyware from [http://www.superantispyware.com/](http://www.superantispyware.com/) - Install both of these applications and run a full scan. Wait about 2-4 hours, if it finds any issues, clean them out, restart and try again.
If none of those fix your issues and you've scanned with your own antivirus, contact your ISP and see if they're having DNS issues, otherwise try an OpenDNS server and set your DNS manually (see above for where we checked the network settings).

That's a lot of information and it varies what direction to head depending on what happens with what step.

---

### Post by eldonkr on 2011-05-06
I'll try all of that when I get back home. I'm currently at the hospital with a friend. It just blows me away that I can get support for WINDOWS on here.

---

### Post by eldonkr on 2011-05-23
I get as far as ipconfig /release and it gives me the following message:

```

no operation can be performed on bluetooth network connection while it has it's media disconnected

```

---

### Post by eldonkr on 2011-05-24
I decided to uninstall the bluetooth stuff in Device manager because I was only using bluetooth to test out a new bluetooth adapter I bought with a wireless keyboard I have. I was also using the keyboard to watch TV shows on my computer without getting out of bed when I was sick earlier in the month. 

While trying to uninstall them Device Manager hangs and after I click uninstall. The only one left in DM is the Generic Bluetooth Radio and it hangs when I click uninstall and after I use task manager to force quit the application and bring it back up its still there. I go to CMD type in ipconfig /release, thinking it would work if there wasn't anymore bluetooth for it to throw a fit over and now it says:

```

The operation failed as no adapter is in the state permissible for this operation.


```

And to make matters even more awesome, I can't do a system restore. I was thinking that I could roll the system back to before this problem started, but my system restore only goes as far back as halfway through last month.

---

### Post by eldonkr on 2011-05-24
Last two posts probably irrelevant now. Fixed with: [http://www.techsupportforum.com/forums/f137/internet-ip-error-the-operation-failed-182285.html](http://www.techsupportforum.com/forums/f137/internet-ip-error-the-operation-failed-182285.html)


to clarify, it didn't fix my problem entirely, it allowed me to use ipconfig /release without error. Still trying to solve the original problem.

Edit again: TCIP/IP  properties has the DNS set, should I switch it to obtain automatically?

Another Edit: Hijackthis log:

```

Logfile of Trend Micro HijackThis v2.0.4
Scan saved at 2:29:43 AM, on 5/24/2011
Platform: Windows XP SP3 (WinNT 5.01.2600)
MSIE: Internet Explorer v8.00 (8.00.6001.18702)
Boot mode: Normal

Running processes:
C:\WINDOWS\System32\smss.exe
C:\WINDOWS\system32\winlogon.exe
C:\WINDOWS\system32\services.exe
C:\WINDOWS\system32\lsass.exe
C:\WINDOWS\system32\Ati2evxx.exe
C:\WINDOWS\system32\svchost.exe
c:\Program Files\Microsoft Security Client\Antimalware\MsMpEng.exe
C:\WINDOWS\System32\svchost.exe
C:\WINDOWS\system32\svchost.exe
C:\WINDOWS\system32\Ati2evxx.exe
C:\WINDOWS\system32\spoolsv.exe
C:\Program Files\Belkin\Router Setup and Monitor\BelkinService.exe
C:\Program Files\Common Files\Apple\Mobile Device Support\AppleMobileDeviceService.exe
C:\Program Files\Belkin\Belkin USB Print and Storage Center\BkBackupScheduler.exe
C:\Program Files\Belkin\Belkin USB Print and Storage Center\Bkapcs.exe
C:\Program Files\Bonjour\mDNSResponder.exe
C:\Program Files\Java\jre6\bin\jqs.exe
C:\WINDOWS\System32\spool\DRIVERS\W32X86\3\lxduserv.exe
C:\WINDOWS\system32\lxducoms.exe
C:\Program Files\TestOut\Orbis\OrbisClient.Services.exe
C:\WINDOWS\system32\svchost.exe
D:\Installations\Programs\TVersity\Media Server\MediaServer.exe
C:\Program Files\Viewpoint\Common\ViewpointService.exe
D:\Installations\Diagnostic\TightVNC\WinVNC.exe
C:\Program Files\Common Files\Microsoft Shared\Windows Live\WLIDSVC.EXE
C:\Program Files\Common Files\Microsoft Shared\Windows Live\WLIDSvcM.exe
C:\WINDOWS\Explorer.EXE
C:\WINDOWS\SOUNDMAN.EXE
C:\WINDOWS\ALCWZRD.EXE
D:\Installations\Programs\Elaborate Bytes\VirtualCloneDrive\VCDDaemon.exe
C:\Program Files\Belkin\Router Setup and Monitor\BelkinRouterMonitor.exe
C:\WINDOWS\vsnpstd3.exe
C:\Program Files\Microsoft Security Client\msseces.exe
D:\Installations\Programs\iTunes\iTunesHelper.exe
C:\WINDOWS\system32\rundll32.exe
C:\WINDOWS\System32\svchost.exe
C:\Program Files\Belkin\Belkin USB Print and Storage Center\connect.exe
C:\Program Files\Belkin\Router Setup and Monitor\BelkinSetup.exe
D:\Installations\Programs\utorrent\uTorrent.exe
D:\Installations\Programs\RocketDock\RocketDock.exe
D:\Installations\Programs\PeerBlock\peerblock.exe
C:\Documents and Settings\Eldon KR\Local Settings\Application Data\Google\Update\1.3.21.53\GoogleCrashHandler.exe
C:\Program Files\iPod\bin\iPodService.exe
D:\Installations\Programs\Rainmeter\Rainmeter.exe
C:\WINDOWS\system32\ctfmon.exe
C:\WINDOWS\system32\wuauclt.exe
D:\Files\My Documents\Downloads\Downloads from the net\HijackThis.exe

R1 - HKLM\Software\Microsoft\Internet Explorer\Main,Default_Page_URL = http://go.microsoft.com/fwlink/?LinkId=69157
R1 - HKLM\Software\Microsoft\Internet Explorer\Main,Default_Search_URL = http://go.microsoft.com/fwlink/?LinkId=54896
R1 - HKLM\Software\Microsoft\Internet Explorer\Main,Search Page = http://go.microsoft.com/fwlink/?LinkId=54896
R0 - HKLM\Software\Microsoft\Internet Explorer\Main,Start Page = http://go.microsoft.com/fwlink/?LinkId=69157
R1 - HKCU\Software\Microsoft\Internet Connection Wizard,ShellNext = http://windowsupdate.microsoft.com/
R1 - HKCU\Software\Microsoft\Internet Explorer\Main,Window Title = Windows Internet Explorer provided by MSN & Bing
R1 - HKCU\Software\Microsoft\Windows\CurrentVersion\Internet Settings,ProxyOverride = *.local
R3 - URLSearchHook: Yahoo! Toolbar - {EF99BD32-C1FB-11D2-892F-0090271D4F88} - C:\Program Files\Yahoo!\Companion\Installs\cpn0\yt.dll
O2 - BHO: &Yahoo! Toolbar Helper - {02478D38-C3F9-4efb-9B51-7695ECA05670} - C:\Program Files\Yahoo!\Companion\Installs\cpn0\yt.dll
O2 - BHO: AcroIEHelperStub - {18DF081C-E8AD-4283-A596-FA578C2EBDC3} - C:\Program Files\Common Files\Adobe\Acrobat\ActiveX\AcroIEHelperShim.dll
O2 - BHO: Windows Live ID Sign-in Helper - {9030D464-4C02-4ABF-8ECC-5164760863C6} - C:\Program Files\Common Files\Microsoft Shared\Windows Live\WindowsLiveLogin.dll
O2 - BHO: Java(tm) Plug-In 2 SSV Helper - {DBC80044-A445-435b-BC74-9C25C1C588A9} - C:\Program Files\Java\jre6\bin\jp2ssv.dll
O2 - BHO: JQSIEStartDetectorImpl - {E7E6F031-17CE-4C07-BC86-EABFE594F69C} - C:\Program Files\Java\jre6\lib\deploy\jqs\ie\jqs_plugin.dll
O2 - BHO: SingleInstance Class - {FDAD4DA1-61A2-4FD8-9C17-86F7AC245081} - C:\Program Files\Yahoo!\Companion\Installs\cpn0\YTSingleInstance.dll
O3 - Toolbar: Yahoo! Toolbar - {EF99BD32-C1FB-11D2-892F-0090271D4F88} - C:\Program Files\Yahoo!\Companion\Installs\cpn0\yt.dll
O4 - HKLM\..\Run: [SoundMan] SOUNDMAN.EXE
O4 - HKLM\..\Run: [AlcWzrd] ALCWZRD.EXE
O4 - HKLM\..\Run: [Alcmtr] ALCMTR.EXE
O4 - HKLM\..\Run: [WinVNC] "D:\Installations\Diagnostic\TightVNC\WinVNC.exe" -servicehelper
O4 - HKLM\..\Run: [VirtualCloneDrive] "D:\Installations\Programs\Elaborate Bytes\VirtualCloneDrive\VCDDaemon.exe" /s
O4 - HKLM\..\Run: [InstaLAN] "C:\Program Files\Belkin\Router Setup and Monitor\BelkinRouterMonitor.exe" startup
O4 - HKLM\..\Run: [snpstd3] C:\WINDOWS\vsnpstd3.exe
O4 - HKLM\..\Run: [Adobe Reader Speed Launcher] "D:\Installations\System\Adobe\Reader\Reader_sl.exe"
O4 - HKLM\..\Run: [Adobe ARM] "C:\Program Files\Common Files\Adobe\ARM\1.0\AdobeARM.exe"
O4 - HKLM\..\Run: [MSC] "c:\Program Files\Microsoft Security Client\msseces.exe" -hide -runkey
O4 - HKLM\..\Run: [AppleSyncNotifier] C:\Program Files\Common Files\Apple\Mobile Device Support\AppleSyncNotifier.exe
O4 - HKLM\..\Run: [iTunesHelper] "D:\Installations\Programs\iTunes\iTunesHelper.exe"
O4 - HKLM\..\Run: [BluetoothAuthenticationAgent] rundll32.exe bthprops.cpl,,BluetoothAuthenticationAgent
O4 - HKCU\..\Run: [uTorrent] "D:\Installations\Programs\utorrent\uTorrent.exe"
O4 - HKCU\..\Run: [RocketDock] "D:\Installations\Programs\RocketDock\RocketDock.exe"
O4 - HKCU\..\Run: [PeerBlock] D:\Installations\Programs\PeerBlock\peerblock.exe
O4 - HKCU\..\Run: [Google Update] "C:\Documents and Settings\Eldon KR\Local Settings\Application Data\Google\Update\GoogleUpdate.exe" /c
O4 - HKCU\..\Run: [MSMSGS] "C:\Program Files\Messenger\msmsgs.exe" /background
O4 - HKCU\..\Run: [ctfmon.exe] C:\WINDOWS\system32\ctfmon.exe
O4 - HKUS\S-1-5-19\..\RunOnce: [_nltide_3] rundll32 advpack.dll,LaunchINFSectionEx nLite.inf,C,,4,N (User 'LOCAL SERVICE')
O4 - HKUS\S-1-5-20\..\RunOnce: [_nltide_3] rundll32 advpack.dll,LaunchINFSectionEx nLite.inf,C,,4,N (User 'NETWORK SERVICE')
O4 - HKUS\S-1-5-18\..\RunOnce: [_nltide_3] rundll32 advpack.dll,LaunchINFSectionEx nLite.inf,C,,4,N (User 'SYSTEM')
O4 - HKUS\.DEFAULT\..\RunOnce: [_nltide_3] rundll32 advpack.dll,LaunchINFSectionEx nLite.inf,C,,4,N (User 'Default user')
O4 - Global Startup: Rainmeter.lnk = D:\Installations\Programs\Rainmeter\Rainmeter.exe
O8 - Extra context menu item: Append Link Target to Existing PDF - res://C:\Program Files\Common Files\Adobe\Acrobat\ActiveX\AcroIEFavClient.dll/AcroIEAppendSelLinks.html
O9 - Extra button: (no name) - {e2e2dd38-d088-4134-82b7-f2ba38496583} - C:\WINDOWS\Network Diagnostic\xpnetdiag.exe
O9 - Extra 'Tools' menuitem: @xpsp3res.dll,-20001 - {e2e2dd38-d088-4134-82b7-f2ba38496583} - C:\WINDOWS\Network Diagnostic\xpnetdiag.exe
O9 - Extra button: Messenger - {FB5F1910-F110-11d2-BB9E-00C04F795683} - C:\Program Files\Messenger\msmsgs.exe
O9 - Extra 'Tools' menuitem: Windows Messenger - {FB5F1910-F110-11d2-BB9E-00C04F795683} - C:\Program Files\Messenger\msmsgs.exe
O16 - DPF: {30528230-99f7-4bb4-88d8-fa1d4f56a2ab} - C:\Program Files\Yahoo!\Common\Yinsthelper.dll
O16 - DPF: {6414512B-B978-451D-A0D8-FCFDF33E833C} (WUWebControl Class) - http://update.microsoft.com/windowsupdate/v6/V5Controls/en/x86/client/wuweb_site.cab?1269662165781
O16 - DPF: {6E32070A-766D-4EE6-879C-DC1FA91D2FC3} (MUWebControl Class) - http://www.update.microsoft.com/microsoftupdate/v6/V5Controls/en/x86/client/muweb_site.cab?1269658987031
O17 - HKLM\System\CCS\Services\Tcpip\..\{54AC6303-234C-4EAF-A9EC-C1D36C50E221}: NameServer = 216.135.0.10,216.135.1.10
O18 - Protocol: skype4com - {FFC8B962-9B40-4DFF-9458-1830C7DD7F5D} - C:\PROGRA~1\COMMON~1\Skype\SKYPE4~1.DLL
O22 - SharedTaskScheduler: Browseui preloader - {438755C2-A8BA-11D1-B96B-00A0C90312E1} - C:\WINDOWS\system32\browseui.dll
O22 - SharedTaskScheduler: Component Categories cache daemon - {8C7461EF-2B13-11d2-BE35-3078302C2030} - C:\WINDOWS\system32\browseui.dll
O23 - Service: AffinegyService - Affinegy, Inc. - C:\Program Files\Belkin\Router Setup and Monitor\BelkinService.exe
O23 - Service: Apple Mobile Device - Apple Inc. - C:\Program Files\Common Files\Apple\Mobile Device Support\AppleMobileDeviceService.exe
O23 - Service: Ati HotKey Poller - ATI Technologies Inc. - C:\WINDOWS\system32\Ati2evxx.exe
O23 - Service: ATI Smart - Unknown owner - C:\WINDOWS\system32\ati2sgag.exe
O23 - Service: Belkin Local Backup Service - Unknown owner - C:\Program Files\Belkin\Belkin USB Print and Storage Center\BkBackupScheduler.exe
O23 - Service: Belkin Network USB Helper - Unknown owner - C:\Program Files\Belkin\Belkin USB Print and Storage Center\Bkapcs.exe
O23 - Service: Bonjour Service - Apple Inc. - C:\Program Files\Bonjour\mDNSResponder.exe
O23 - Service: iPod Service - Apple Inc. - C:\Program Files\iPod\bin\iPodService.exe
O23 - Service: Java Quick Starter (JavaQuickStarterService) - Sun Microsystems, Inc. - C:\Program Files\Java\jre6\bin\jqs.exe
O23 - Service: lxduCATSCustConnectService - Lexmark International, Inc. - C:\WINDOWS\System32\spool\DRIVERS\W32X86\3\\lxduserv.exe
O23 - Service: lxdu_device -   - C:\WINDOWS\system32\lxducoms.exe
O23 - Service: NBService - Nero AG - C:\Program Files\Nero\Nero 7\Nero BackItUp\NBService.exe
O23 - Service: LabSim Configuration and Security (OrbisClient.Services) - Unknown owner - C:\Program Files\TestOut\Orbis\OrbisClient.Services.exe
O23 - Service: TVersityMediaServer - Unknown owner - D:\Installations\Programs\TVersity\Media Server\MediaServer.exe
O23 - Service: Viewpoint Manager Service - Viewpoint Corporation - C:\Program Files\Viewpoint\Common\ViewpointService.exe
O23 - Service: VNC Server (winvnc) - TightVNC Group - D:\Installations\Diagnostic\TightVNC\WinVNC.exe

--
End of file - 10089 bytes

```

---

