---
title: "Intel VS Wine/WoW, another conflict"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by VyseV1 on 2008-02-04
Hallo all,

This is really my big time real use of Linux. In high school we over rid the school computers so we could program in java (the java tools on our school system was a joke). I believed we  used DSL, and for reasearch projects we used knoppix. So from there I picked up some basic linux skills. Now I have a shiny new Kubuntu OS as well as XP cause Vista annoyed me :mad: 

Now this is a topic I've seen come up before, but mine seems different then the one in this thread: [http://ubuntuforums.org/showthread.php?t=638885](http://ubuntuforums.org/showthread.php?t=638885)

Trying to get yee olde WoW running, works fine till the opening movie ends, at which point it just dies a terrible death, and 5 clicking sounds for some odd reason. After it dies it makes my screen go all fuzzy. Here's what the console puts out:

fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed78,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34eccc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f26c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f3d0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f57c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f574,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34efd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f118,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x132608) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x134c00) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x34efd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f118,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
Mesa 7.0.1 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22

The heart of the problem being the Msea 7.0.1 issue. I followed the guide for the WoW install on wowwiki found here:[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

Now after reading the thread up above, I got rid of the openGL dealie just to see what it would do and still nothing. It also mentions the directX helps however I'm unsure how to get it to install correctly via wine.

My current Wine version is 0.9.54, running off of the integrated intel graphics chip 945.

Any help or advice you could offer would be great and it is a pleasure to work with you guys.

Thanks in advance :KS

---

### Post by VyseV1 on 2008-02-04
If it helps any, im on patch 2.3.0 on WoW

---

