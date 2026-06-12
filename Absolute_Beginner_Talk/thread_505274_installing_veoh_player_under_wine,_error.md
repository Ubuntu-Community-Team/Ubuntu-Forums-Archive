---
title: "installing veoh player under wine, error"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by natakim on 2007-07-20
i'm trying to install veoh player through wine. get to the end of the install but it fails. this is what i get in terminal, any thoughts/experiences with this...

> natakim@natakim-desktop:~$ wine /home/natakim/desktop/VeohSetup-3.2.1.1073.exe
fixme:advapi:LookupAccountNameW (null) L"natakim" (nil) 0x338a24 (nil) 0x338a28 0x338a1c - stub
fixme:advapi:LookupAccountNameW (null) L"natakim" 0x17d388 0x338a24 0x17d068 0x338a28 0x338a1c - stub
fixme:process:IsWow64Process (0xffffffff 0x3397b0) stub!
err:msi:deformat_environment Unknown environment variable L"ALLUSERSPROFILE"
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 1 ignored L"Upgrade" table values
fixme:process:IsWow64Process (0xffffffff 0x339c1c) stub!
fixme:process:IsWow64Process (0xffffffff 0x339088) stub!
fixme:process:IsWow64Process (0xffffffff 0x339178) stub!
fixme:process:IsWow64Process (0xffffffff 0x32ccf4) stub!
fixme:process:IsWow64Process (0xffffffff 0x32cd0c) stub!
fixme:process:IsWow64Process (0xffffffff 0x32cddc) stub!
fixme:process:IsWow64Process (0xffffffff 0x32d0d0) stub!
fixme:reg:GetNativeSystemInfo (0x32d0ac) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c34) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c34) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c34) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338a7c) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c20) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c84) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c84) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c84) stub!
fixme:process:IsWow64Process (0xffffffff 0x338a74) stub!
fixme:process:IsWow64Process (0xffffffff 0x338be0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338a74) stub!
fixme:process:IsWow64Process (0xffffffff 0x338be0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c34) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e44) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c34) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c24) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c84) stub!
fixme:process:IsWow64Process (0xffffffff 0x32ca90) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c7c) stub!
fixme:process:IsWow64Process (0xffffffff 0x32ca90) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c7c) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c7c) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c84) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c50) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c50) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c50) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c50) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c84) stub!
fixme:process:IsWow64Process (0xffffffff 0x338be0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c24) stub!
fixme:process:IsWow64Process (0xffffffff 0x32ca90) stub!
fixme:process:IsWow64Process (0xffffffff 0x32c8a0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c50) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c50) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c84) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c50) stub!
fixme:process:IsWow64Process (0xffffffff 0x338c50) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e28) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e28) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e28) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338134) stub!
fixme:x11drv:X11DRV_SetWindowRgn not supported on other thread window 0x1003c
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: missing style name
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
fixme:font:WineEngCreateFontInstance Untranslated charset 77
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338e74) stub!
fixme:sync:CreateJobObjectW (nil) L""
fixme:sync:AssignProcessToJobObject (nil) 0x148
wine: Call from 0x7b844210 to unimplemented function KERNEL32.dll.QueryInformationJobObject, aborting
fixme:advapi:LookupAccountNameW (null) L"natakim" (nil) 0x338bdc (nil) 0x338be0 0x338bd4 - stub
fixme:advapi:LookupAccountNameW (null) L"natakim" 0x99bbf8 0x338bdc 0x99b8d8 0x338be0 0x338bd4 - stub
fixme:advapi:LookupAccountNameW (null) L"natakim" (nil) 0x34eb98 (nil) 0x34eb9c 0x34eb90 - stub
fixme:advapi:LookupAccountNameW (null) L"natakim" 0x178990 0x34eb98 0x1791b8 0x34eb9c 0x34eb90 - stub
fixme:process:IsWow64Process (0xffffffff 0x34ef5c) stub!
fixme:process:IsWow64Process (0xffffffff 0x34e4bc) stub!
fixme:process:IsWow64Process (0xffffffff 0x34e5ac) stub!
err:msi:remove_tracked_tempfiles failed to delete L"C:\\windows\\temp\\msid341.tmp"
fixme:process:IsWow64Process (0xffffffff 0x34ecc0) stub!
fixme:process:IsWow64Process (0xffffffff 0x34ef38) stub!
fixme:process:IsWow64Process (0xffffffff 0x34ef48) stub!
fixme:process:IsWow64Process (0xffffffff 0x34f0d0) stub!
err:msi:remove_tracked_tempfiles failed to delete L"C:\\windows\\temp\\msid1e5.tmp"
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x338dd0) stub!
fixme:process:IsWow64Process (0xffffffff 0x339ae0) stub!
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1000-000008000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x80070108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1000-000008000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x80070108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1000-000008000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x80070108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1000-000008000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x80070108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1000-000008000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x80070108
fixme:process:IsWow64Process (0xffffffff 0x33afe8) stub!

---

### Post by AlexenderReez on 2007-07-20
i don't what kind of answer do you expect..but it seems when we want to use windows application using wine that need proxy or internet connection,it is quite difficult to handle...i suggest you to find alternative like miro ([http://news.softpedia.com/news/Democracy-Player-Is-Now-Known-As-Miro-60328.shtml](http://news.softpedia.com/news/Democracy-Player-Is-Now-Known-As-Miro-60328.shtml))..

---

### Post by natakim on 2007-07-20
> **AlexenderReez said:**
> i don't what kind of answer do you expect..but it seems when we want to use windows application using wine that need proxy or internet connection,it is quite difficult to handle...i suggest you to find alternative like miro ([http://news.softpedia.com/news/Democracy-Player-Is-Now-Known-As-Miro-60328.shtml](http://news.softpedia.com/news/Democracy-Player-Is-Now-Known-As-Miro-60328.shtml))..

that's a pretty useful response right there, thanks. i didn't think of internet as the problem.

cheers

---

### Post by AlexenderReez on 2007-07-20
> **natakim said:**
> that's a pretty useful response right there, thanks. i didn't think of internet as the problem.

cheers

hm...it is not internet problem..but wine will give error if the application that you want to install try to detect your internet connection like IDM ....
:)

wine is just a layer...it won't work with all windows application.....

---

### Post by natakim on 2007-07-20
> **AlexenderReez said:**
> hm...it is not internet problem..but wine will give error if the application that you want to install try to detect your internet connection like IDM ....
:)

wine is just a layer...it won't work with all windows application.....

sorry i didn't literally mean it was an internet problem, but rather it didn't occur to me that because the program requires a connect it could cause problems elsewhere. cheers again

---

### Post by natakim on 2007-08-04
so i got it to work. i ended up just copying the veoh folder from programs in my xp partition to the wine c drive. (before hand i deleted evrying on the linux drive that had veoh content) now bingo, it works under wine.

:)

---

