---
title: "CounterStrike Condition zero on Wine"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-08-02
i have installed it:

```

shoaibi@golden-eagle:/media/sda6/Entertainment/Games/CounterStrike 1.6 + ConditionZero English+Russian$ wine CounterStrike\ 1.6+ConditionZero_build2738.exe err:ole:TLB_ReadTypeLib Loading of typelib L"c:\\Program Files\\Common Files\\InstallShield\\Professional\\RunTime\\IsProBE.tlb" failed with error 2
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
fixme:shell:IShellLinkA_fnGetPath (0x1a315a8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1a315a8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1a31378): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1a31378): WIN32_FIND_DATA is not yet filled.
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
fixme:ntdll:NtQuerySecurityObject (0x68,0x00000004,(nil),0x00000000,0x34df94) stub!
fixme:ntdll:NtQuerySecurityObject (0x68,0x00000004,0x328fcd0,0x0000005c,0x34df94) stub!
fixme:advapi:SetFileSecurityW (L"c:\\Program Files\\InstallShield Installation Information\\{A6B06FBE-783A-4322-9532-5BCC16CD8554}\\setup.ilg") : stub
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1000-00000a000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x80070108
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1000-00000a000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x80070108
fixme:shell:DllCanUnloadNow stub
fixme:menubuilder:SaveIconResAsXPM Unsupported color depth 24-bit
shoaibi@golden-eagle:/media/sda6/Entertainment/Games/CounterStrike 1.6 + ConditionZero English+Russian$ fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub                                                                        shoaibi@golden-eagle:/media/sda6/Entertainment/Games/CounterStrike 1.6 + ConditionZero English+Russian$ 


```


problems:
1. if i press F1, its open ubuntu help, rather then selecting the best weapon packahge.
2. almost all is test is invible, include the bravery, co-operation, tutor, information about mission while loading etc...
3. no sound. i have two sound cards, the builtin one doesnt work, while the other does, the working is selected as default in ubuntu and works fine, what should i do to enable sounds?




This is what i get when i click audio tab in the winecfg

```

fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet

```

---

### Post by apswartz on 2007-08-02
Maybe there aren't many Counterstrike players here. Have you checked in any of the Wine support areas?

[http://www.winehq.org/site/getting_help](http://www.winehq.org/site/getting_help)

---

### Post by Rocket2DMn on 2007-08-02
Have a look here, this is a pretty good guide to getting games (specifically HL-based games) working through steam.
Sounds like you need the tahoma font and might need to use OSS instead of ALSA for sound.  There is something about using a different OLE, not sure if it still applies though.
You already have steam installed, so you can probably skip that part of the tutorial (except for the microsoft core fonts part).
[http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/](http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/)
PS: You might get better framerates if you turn off Beryl/Compiz-Fusion when you play.  I also use wine 0.9.39 because I had a sound delay in later versions when I play counter-strike 1.6

---

### Post by shoaibi on 2007-11-09
Thanks, i followed your link and have been successful, but facing these problems:

1] How to install gecko inside wine behind proxy, i searched google and download the cab file, extracted it, moved it, and ran wineboot, but it doesn't recognise that, while it can't also recognize the proxy.
2] Game is running with some kind of jitter, not exactly jitter but for every frame a certain  amount of frames is skipped, i mean that if i take a 360 turn, i am able to see it as 4 different picture being slided into one another.
3] sound is playing strange, its like its running really fast, i read and tried to stop esd and artsd, i tried to run start-stop-daemon under root privilages, but it gave me strange errors.

Need your guidance, and is there any free software better then wine, something like Cadega?

---

