---
title: "Wine, Java (JRE), and Yahoo SiteBuilder"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by geektyme on 2006-08-18
Hello all!

First I want to say that I am learning a lot just by reading these posts and past posts. I also purchased a book "Ubuntu Hacks" and that is of great help also.

But I am having a issue with Wine loading JRE and Yahoo SiteBuilder instead of me rambling on about the issues I will just paste them below. So far what I did was:

1: loaded Firefox in wine (successful)
2: Loaded (or tried to) j2re-1_4_2_12-windows-i586-p.exe in wine (got errors that will be pasted
3: Loaded (or tried to) ysitebuilder.exe in wine (got errors that will be posted below)

any help will be appriciated

xxxx@xxxx-laptop:~$ wine "j2re-1_4_2_12-windows-i586-p.exe"
fixme:msi:MsiGetProductInfoW L"" L"PackageCode" 0x7fd4c738 0x7fb9d8b0
fixme:msi:MsiInstallProductW L"c:\\windows\\profiles\\xxxx\\Local Settings\\Application Data\\{7148F0A6-6813-11D6-A77B-00B0D0142120}\\Java 2 Runtime Environment, SE v1.4.2_12.msi" L" TRANSFORMS=C:\\windows\\temp\\_is40c\\1033.MST SETUPEXEDIR=Z:\\home\\xxxx"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"ValidateProductID"
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\widctlpar"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\aspalpha"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\aspnum"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\faauto"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\adjustright"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\rin0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\lin0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\itap0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfe1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\cgrid"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langnp1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfenp1033"
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\sbauto1"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\saauto1"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\widctlpar"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\aspalpha"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\aspnum"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\faauto"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\adjustright"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\rin0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\lin0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\itap0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfe1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\cgrid"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langnp1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfenp1033"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"ValidateProductID"
err:msi:deformat_environment Unknown environment variable L"ALLUSERSPROFILE"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveExistingProducts"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnpublishComponents"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnpublishFeatures"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterTypeLibraries"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveODBC"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveRegistryValues"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterClassInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterExtensionInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterProgIdInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterMIMEInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveShortcuts"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveDuplicateFiles"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveFolders"fixme:msi:ACTION_HandleStandardAction unhandled standard action L"InstallODBC"
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
err:heap:HEAP_ValidateInUseArena Heap 0x7fcf0000: in-use arena 0x7fd464f8 next block has PREV_FREE flag

xxxx@xxxx-laptop:~$ wine "ysitebuilder.exe"
fixme:win:SetWindowTextA setting text "Yahoo! SiteBuilder Setup" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Yahoo! SiteBuilder Setup" of other process window (nil) should not use SendMessage
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:richedit:RichEditANSIWndProc EM_EXLIMITTEXT: stub
fixme:shell:SHAutoComplete SHAutoComplete stub
err:heap:HEAP_ValidateInUseArena Heap 0x7fcf0000: in-use arena 0x7fd46220 next block has PREV_FREE flag
keytool error: java.lang.Exception: Certificate not imported, alias <mykey> already exists
err:heap:HEAP_ValidateInUseArena Heap 0x7fcf0000: in-use arena 0x7fd46230 next block has PREV_FREE flag
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb7b5f4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x7fb7b5f4,0x00000000), stub!
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7d4bf680)->((nil),00001008)
Exception in thread "main" java.lang.UnsatisfiedLinkError: getPublicJres
        at com.sun.deploy.panel.PlatformSpecificUtils.getPublicJres(Native Method)
        at com.sun.deploy.config.PluginJavaInfo.initialize(Unknown Source)
        at com.sun.deploy.config.Config.refreshProps(Unknown Source)
        at com.sun.deploy.config.Config.initialize(Unknown Source)
        at com.sun.deploy.config.Config.<clinit>(Unknown Source)
        at com.sun.javaws.Main.main(Unknown Source)
err:heap:HEAP_ValidateInUseArena Heap 0x7fcf0000: in-use arena 0x7fd470d8 next block has PREV_FREE flag
Java Web Start splash screen process exiting .....
Bad installation. Error invoking Java VM (execv)
c:\Program Files\Java\jre1.5.0_08\bin\javaw.exe: No such file or directory
tLast WinSock Error: 0
fixme:msvcrt:_spawnve only trying .exe when no extension given
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb7b5f4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x7fb7b5f4,0x00000000), stub!
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7d4c0920)->((nil),00001008)
Exception in thread "main" java.lang.UnsatisfiedLinkError: getPublicJres
        at com.sun.deploy.panel.PlatformSpecificUtils.getPublicJres(Native Method)
        at com.sun.deploy.config.PluginJavaInfo.initialize(Unknown Source)
        at com.sun.deploy.config.Config.refreshProps(Unknown Source)
        at com.sun.deploy.config.Config.initialize(Unknown Source)
        at com.sun.deploy.config.Config.<clinit>(Unknown Source)
        at com.sun.javaws.Main.main(Unknown Source)
err:heap:HEAP_ValidateInUseArena Heap 0x7fcf0000: in-use arena 0x7fd47228 next block has PREV_FREE flag
Java Web Start splash screen process exiting .....
Bad installation. Error invoking Java VM (execv)
c:\Program Files\Java\jre1.5.0_08\bin\javaw.exe: No such file or directory
tLast WinSock Error: 0
fixme:win:SetWindowTextA setting text "Delete file: C:\\windows\\temp\\nsj5b9.tmp\\System.dll" of other process window 0x3004a should not use SendMessage
fixme:win:SetWindowTextA setting text "Delete file: C:\\windows\\temp\\nsj5b9.tmp\\jre.ini" of other process window 0x3004a should not use SendMessage
fixme:win:SetWindowTextA setting text "Delete file: C:\\windows\\temp\\nsj5b9.tmp\\jreFailed.ini" of other process window 0x3004a should not use SendMessage
fixme:win:SetWindowTextA setting text "Delete file: C:\\windows\\temp\\nsj5b9.tmp\\ioSpecial.ini" of other process window 0x3004a should not use SendMessage
fixme:win:SetWindowTextA setting text "Delete file: C:\\windows\\temp\\nsj5b9.tmp\\modern-wizard.bmp" of other process window 0x3004a should not use SendMessagefixme:win:SetWindowTextA setting text "Delete file: C:\\windows\\temp\\nsj5b9.tmp\\InstallOptions.dll" of other process window 0x3004a should not use SendMessage
fixme:win:SetWindowTextA setting text "Remove folder: C:\\windows\\temp\\nsj5b9.tmp\\" of other process window 0x3004a should not use SendMessage

Thanks again I know this looks like a foreign language to me but to some of you it looks like plain english.

---

### Post by bodhi.zazen on 2006-08-18
Interesting. What are you trying to do exactly?

Firefox runs in Linux, no need to run it in wine.

You can also install JAVA in Linux and do not need to run in in wine.

Not sure what ysitebuilder.exe is or if there is a Linux equivalent.

---

### Post by geektyme on 2006-08-18
You are right all works dandy in Linux however I have a generic site builder Yahoo Site Builder and it will not run in Linux so low and behold I am trying in wine so I do not have to restart in WinXP trying to ween myself out of Windows

wow have to love run on sentences..hehehe

---

### Post by bodhi.zazen on 2006-08-18
See if you can get help at wineHQ:

[http://www.winehq.com/](http://www.winehq.com/)

search for the name of your application in their data base.

I had a similar problem with a different application, It took me a year to hack (ie set up) wine. Wine is complex. Did you use winetools to configure wine?

If so, try again, this time configure wine with sidenet:

[http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)

The package you need is at the bottom of the page.

Otherwise, is there any Linux alternate? I would be surprised if there were not, but I am not familiar with your application.

---

### Post by geektyme on 2006-08-18
Thanks for the help I am sure that there is a alternate proggie, but I am still a noob. 

All I am trying to do is make a new website with yahoo. I was using 1and1 for my hosting and they are being butt-monkies so buisness is going elsewhere.

One more question does NetObjects Fusion run on Linux? If you do not know I will look that up in that site you gave me also.

Again thanks for your help. This has to be one of the best help forums I have ever experienced.

---

### Post by bodhi.zazen on 2006-08-18
I am afraid I have already told you more then I know.

I was thinking I may be able to help with wine....

But I am just not familiar enough with your applications to be of much help.

Sorry.

I almost forgot.....

Welcome to Linux.

---

