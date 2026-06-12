---
title: "Ubuntu slowing down"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by spacefreak86 on 2008-02-20
I've noticed in the past day or so that Ubuntu seems sluggish ... almost to the point of being XP with its virus scan, firewall, etc etc. Is there a way to clean out un-needed files, delete temp files, and perhaps streamline things a bit? If so, how?

---

### Post by jan quark on 2008-02-20
you can remove not needed packages with

```
sudo apt-get autoremove
```

it is very unusual for linux system to become sluggish

did you install anything unusual the last days?

---

### Post by philinux on 2008-02-20
Running ubuntu since last July never noticed a slow down.

Run top from the terminal see what's eating resources. Or system monitor.

---

### Post by spacefreak86 on 2008-02-20
The other option would be to increase the size of the swap file. I've got 2 GB of RAM and Ubuntu is installed on a 102 GB HD, but I forgot how big I made the swap file. How do I check it and make it bigger?

---

### Post by spiderbatdad on 2008-02-20
sounds like a job for gparted livecd

---

### Post by spacefreak86 on 2008-02-20
> **spiderbatdad said:**
> sounds like a job for gparted livecd

Um, okay. I downloaded it using terminal (sudo apt-get gparted), and installed it. But its saying I have to be root as gparted is a weapon of mass destruction.

---

### Post by ImThatNerd on 2008-02-20
> **spacefreak86 said:**
> The other option would be to increase the size of the swap file. I've got 2 GB of RAM and Ubuntu is installed on a 102 GB HD, but I forgot how big I made the swap file. How do I check it and make it bigger?

I am a linux noob, so idk if I am right. But I know for sure you can check with the LiveCD, by putting it in and going into partion editor to show you.

---

### Post by spiderbatdad on 2008-02-20
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by robkeys on 2008-02-20
I had a similar issue a few weeks back with my ancient desktop. Between azureus, firefox and pidgin running round the clock my little pentium 4 couldn't hack it. I switched to xubuntu and started using swiftfox: i've never looked back (although i do miss adblock).

---

### Post by carlinuxlearner on 2008-02-20
I don't think you need a swap file with 2GB of RAM unless the system monitor is saying that it's using it all up.(I have one but it never uses it). I have 2GB and I've NEVER seen it use more than 1GB. So I think it's some other problem.

C@RL

---

### Post by oilchangeguy on 2008-02-20
> **spacefreak86 said:**
> The other option would be to increase the size of the swap file. I've got 2 GB of RAM and Ubuntu is installed on a 102 GB HD, but I forgot how big I made the swap file. How do I check it and make it bigger?

if you've got 2gb of ram you don't need any more swap!!

---

### Post by spacefreak86 on 2008-02-20
Will this damage the current partitions at all?

---

### Post by spacefreak86 on 2008-02-20
> **oilchangeguy said:**
> if you've got 2gb of ram you don't need any more swap!!

Then why can't I get a single game that involves graphics (beyond watching movies or playing music) to work?

This is what I get from terminal when I enter the command: free:

:~$ free
             total       used       free     shared    buffers     cached
Mem:       2059740    2007328      52412          0      63552    1619120
-/+ buffers/cache:     324656    1735084
Swap:       498004          0     498004

---

### Post by robkeys on 2008-02-20
> **spacefreak86 said:**
> The other option would be to increase the size of the swap file. I've got 2 GB of RAM and Ubuntu is installed on a 102 GB HD, but I forgot how big I made the swap file. How do I check it and make it bigger?

Also with 2 GB's of ram you probably also aren't on a pentium 4, so there goes my advice...

---

### Post by jken146 on 2008-02-20
Type ```
free
``` to see RAM and swap usage.

---

### Post by robkeys on 2008-02-20
> **spacefreak86 said:**
> Then why can't I get a single game that involves graphics (beyond watching movies or playing music) to work?

This is what I get from terminal when I enter the command: free:

:~$ free
             total       used       free     shared    buffers     cached
Mem:       2059740    2007328      52412          0      63552    1619120
-/+ buffers/cache:     324656    1735084
Swap:       498004          0     498004

What GFX card do you have, and what driver are you using?

---

### Post by spacefreak86 on 2008-02-20
Graphics Card? Um.... that one that is attached to the mobo?  82865G Integrated Graphics Controller.

System Specs:

P4 i386  2.8 GHz
2 GB RAM
80 GB HD (Two partitions, WinXP on the first)
320 GB HD (Three partions, Ubuntu on the second)
CD-RW Drive
DVD-ROM Drive

(Ethernet and 6 USB ports attached to mobo)

---

### Post by Moop on 2008-02-20
> **robkeys said:**
> I had a similar issue a few weeks back with my ancient desktop. Between azureus, firefox and pidgin running round the clock my little pentium 4 couldn't hack it. I switched to xubuntu and started using swiftfox: i've never looked back (although i do miss adblock).

Use Swiftweasel. All the firefox extensions work with it. [http://swiftweasel.tuxfamily.org/]("http://swiftweasel.tuxfamily.org/")

*sorry about the off topic post but I couldn't resist*

---

### Post by carlinuxlearner on 2008-02-20
Run one of the games your talking about from the terminal, and post the output here.

example:
carl@carl-desktop:~/games/sauerbraten$ sh runsauerbraten.sh
init: sdl
init: enet
init: video: mode
init: video: misc
init: gl
Renderer: GeForce 7025 / NVIDIA nForce 630a/PCI/SSE2 (NVIDIA Corporation)
Driver: 2.1.2 NVIDIA 169.09
Rendering using the OpenGL 1.5 GLSL shader path.
init: console
init: world
init: sound
init: cfg
init: localconnect
init: mainloop
read map packages/base/metl4.ogz (0.1 seconds)
Mining Station by metlslime
game mode is ffa/default

C@RL

---

### Post by spacefreak86 on 2008-02-22
```
bdizzle86@MINE:~$ wine "c:\\Program Files\\Microsoft Games\\Halo\\halo.exe"
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d510,0x00000000), stub!
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x12f7c0, L"dwDirectXVersionMajor", 0x33d948)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x12f7c0, L"dwDirectXVersionMinor", 0x33d948)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x12f7c0, L"szDirectXVersionLetter", 0x33d948)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x12f7c0, L"szDirectXVersionEnglish", 0x33d948)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x12f7c0, L"szDirectXVersionLongEnglish", 0x33d948)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x12f7c0, L"bDebug", 0x33d948)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x12f7a0, L"DxDiag_SystemInfo", 0x12f7c0)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x12f7a0, L"DxDiag_SystemDevices", 0x1301a8)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x12f7a0, L"DxDiag_LogicalDisks", 0x130218)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x130280,L"ddraw.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szPath", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szName", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bExists", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szVersion", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szAttributes", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szLanguageEnglish", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeHigh", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeLow", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bBeta", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bDebug", 0x33cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x130280,L"dplayx.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szPath", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szName", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bExists", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szVersion", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szAttributes", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szLanguageEnglish", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeHigh", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeLow", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bBeta", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bDebug", 0x33cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x130280,L"dpnet.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szPath", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szName", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bExists", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szVersion", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szAttributes", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szLanguageEnglish", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeHigh", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeLow", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bBeta", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bDebug", 0x33cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x130280,L"dinput.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szPath", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szName", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bExists", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szVersion", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szAttributes", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szLanguageEnglish", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeHigh", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeLow", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bBeta", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bDebug", 0x33cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x130280,L"dinput8.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szPath", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szName", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bExists", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szVersion", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szAttributes", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szLanguageEnglish", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeHigh", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeLow", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bBeta", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bDebug", 0x33cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x130280,L"dsound.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szPath", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szName", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bExists", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szVersion", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szAttributes", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szLanguageEnglish", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeHigh", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeLow", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bBeta", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bDebug", 0x33cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x130280,L"dswave.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szPath", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szName", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bExists", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szVersion", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szAttributes", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szLanguageEnglish", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeHigh", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeLow", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bBeta", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bDebug", 0x33cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x130280,L"d3d8.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szPath", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szName", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bExists", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szVersion", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szAttributes", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szLanguageEnglish", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeHigh", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeLow", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bBeta", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bDebug", 0x33cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x130280,L"d3d9.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szPath", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szName", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bExists", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szVersion", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szAttributes", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szLanguageEnglish", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeHigh", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeLow", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bBeta", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bDebug", 0x33cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x130280,L"dmband.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szPath", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szName", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bExists", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szVersion", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szAttributes", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szLanguageEnglish", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeHigh", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeLow", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bBeta", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bDebug", 0x33cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x130280,L"dmcompos.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szPath", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szName", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bExists", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szVersion", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szAttributes", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szLanguageEnglish", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeHigh", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeLow", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bBeta", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bDebug", 0x33cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x130280,L"dmime.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szPath", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szName", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bExists", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szVersion", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szAttributes", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szLanguageEnglish", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeHigh", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeLow", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bBeta", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bDebug", 0x33cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x130280,L"dmloader.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szPath", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szName", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bExists", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szVersion", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szAttributes", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szLanguageEnglish", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeHigh", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeLow", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bBeta", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bDebug", 0x33cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x130280,L"dmscript.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szPath", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szName", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bExists", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szVersion", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szAttributes", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szLanguageEnglish", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeHigh", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeLow", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bBeta", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bDebug", 0x33cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x130280,L"dmstyle.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szPath", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szName", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bExists", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szVersion", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szAttributes", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szLanguageEnglish", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeHigh", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeLow", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bBeta", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bDebug", 0x33cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x130280,L"dmsynth.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szPath", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szName", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bExists", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szVersion", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szAttributes", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szLanguageEnglish", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeHigh", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeLow", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bBeta", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bDebug", 0x33cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x130280,L"dmusic.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szPath", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szName", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bExists", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szVersion", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szAttributes", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szLanguageEnglish", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeHigh", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeLow", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bBeta", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bDebug", 0x33cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x130280,L"devenum.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szPath", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szName", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bExists", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szVersion", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szAttributes", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szLanguageEnglish", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeHigh", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeLow", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bBeta", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bDebug", 0x33cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x130280,L"quartz.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szPath", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szName", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bExists", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szVersion", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szAttributes", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"szLanguageEnglish", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeHigh", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"dwFileTimeLow", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bBeta", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x130280, L"bDebug", 0x33cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x12f7a0, L"DxDiag_DirectXFiles", 0x130280)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x1368f0, L"0", 0x136910)
fixme:win:EnumDisplayDevicesW ((null),0,0x33d1e8,0x00000000), stub!
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136910, L"szDeviceName", 0x33cf58)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136910, L"szDescription", 0x33cf48)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136910, L"szDisplayMemoryLocalized", 0x33cf38)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136910, L"szDisplayMemoryEnglish", 0x33cf28)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136910, L"dwWidth", 0x33cf18)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136910, L"dwHeight", 0x33cf08)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136910, L"dwBpp", 0x33cef8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136910, L"szVendorId", 0x33cee8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136910, L"szDeviceId", 0x33ced8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136910, L"szKeyDeviceKey", 0x33cec8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136910, L"szKeyDeviceID", 0x33ceb8)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x12f7a0, L"DxDiag_DisplayDevices", 0x1368f0)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x137088, L"DxDiag_SoundDevices", 0x1370a8)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x137088, L"DxDiag_SoundCaptureDevices", 0x1370f8)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x12f7a0, L"DxDiag_DirectSound", 0x137088)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x12f7a0, L"DxDiag_DirectMusic", 0x1371b8)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x12f7a0, L"DxDiag_DirectInput", 0x137220)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x12f7a0, L"DxDiag_DirectPlay", 0x137288)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x137620)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x137620, 1, 0x137638)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szCatName", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidCat", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidFilter", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwMerit", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwInputs", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwOutputs", 0x33ce88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x137620, 1, 0x137650)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szCatName", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidCat", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidFilter", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwMerit", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwInputs", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwOutputs", 0x33ce88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x137620, 1, 0x137ac8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szCatName", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidCat", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidFilter", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwMerit", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwInputs", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwOutputs", 0x33ce88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x137620, 1, 0x137eb8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szCatName", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidCat", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidFilter", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwMerit", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwInputs", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwOutputs", 0x33ce88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x137620, 1, 0x1384a0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szCatName", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidCat", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidFilter", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwMerit", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwInputs", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwOutputs", 0x33ce88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x137620, 1, 0x1388c8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szCatName", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidCat", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidFilter", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwMerit", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwInputs", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwOutputs", 0x33ce88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x137620, 1, 0x138d20)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szCatName", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidCat", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidFilter", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwMerit", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwInputs", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwOutputs", 0x33ce88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x137378)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x137378)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x1373e0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1373e0, 1, 0x1373f8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szCatName", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidCat", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Realtek ALC655 rev 0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidFilter", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwMerit", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwInputs", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwOutputs", 0x33ce88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x1373a8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1373a8, 1, 0x1373c0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szCatName", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidCat", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Midi Through Port-0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidFilter", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwMerit", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwInputs", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwOutputs", 0x33ce88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x1373d8)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x1373d8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1373d8, 1, 0x139e80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szCatName", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidCat", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"DirectSound: Realtek ALC655 rev 0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidFilter", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwMerit", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwInputs", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwOutputs", 0x33ce88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1373d8, 1, 0x139e98)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szCatName", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidCat", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Realtek ALC655 rev 0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szClsidFilter", 0x33cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"szName", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwMerit", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwInputs", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1372f0, L"dwOutputs", 0x33ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x12f7a0, L"DxDiag_DirectShowFilters", 0x1372f0)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x12f7a0, L"DxDiag_DirectSound.DxDiag_SoundDevices", 0x33d9cc)
bdizzle86@MINE:~$ 


```

---

### Post by vinutux on 2008-02-22
i am also face such problem. my problem fixing whn i am install correct driver for my graphics card  and uninstall all ***[COLOR="Red"]unwanted linux kernals[/COLOR]*** and modules using synaptic

---

### Post by sailor2001 on 2008-02-22
[http://ubuntuforums.org/showthread.php?t=664742&highlight=clean+old+files](http://ubuntuforums.org/showthread.php?t=664742&highlight=clean+old+files)   #4

---

### Post by carlinuxlearner on 2008-02-23
@spacefreak86
I see you tried running a game through "wine". Wine doesn't always work with all games, and some times you have to configure it to make it work. 

So instead, try running some of the Screensavers (System>>Preferences>>Screensavers), many of them are 3D (Skyrocket, and Engine would be a good test) so if they run smoothly it's a WINE problem, if they don't run smoothly (or don't run at all) then it's a driver (or lack there of) problem. 

So please post the results of trying to run those Screensavers. (just tell me if they worked well or horribly {or not at all})

C@RL

---

### Post by ruicovelo on 2008-02-24
Hi!

I'm also find my Ubuntu installation sluggish and it's annoying. Well, it's ok overall but when I'm, for instance, updating the system or loading a page under firefox, the mouse gets all jumpy. Don't blame it on firefox please. I know firefox may be a memory and CPU hog but a jumpy mouse makes ubuntu seem sluggish and I don't think this is acceptable for a desktop environment and this must not be normal (please tell me this is not normal). I was previously using Gentoo and this also happened to me in the past but went away with linux 2.6 and the new scheduler. I have also seen things like this happening when dma of a ide disk is inactive but I have a sata disk drive and I don't think this can be a problem.

Any ideas?

---

### Post by ruicovelo on 2008-05-21
> **ruicovelo said:**
> Hi!

I'm also find my Ubuntu installation sluggish and it's annoying. Well, it's ok overall but when I'm, for instance, updating the system or loading a page under firefox, the mouse gets all jumpy. Don't blame it on firefox please. I know firefox may be a memory and CPU hog but a jumpy mouse makes ubuntu seem sluggish and I don't think this is acceptable for a desktop environment and this must not be normal (please tell me this is not normal). I was previously using Gentoo and this also happened to me in the past but went away with linux 2.6 and the new scheduler. I have also seen things like this happening when dma of a ide disk is inactive but I have a sata disk drive and I don't think this can be a problem.

Any ideas?

My problems went away when I upgraded to 8.04

---

### Post by cooldudevamsee on 2008-05-21
Could be because of this bug.
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/213854](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/213854)

Please clear your recent documents.

---

