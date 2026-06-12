---
title: "How do I install starcraft?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by pbatoon on 2007-06-26
Hello, this is my first time using a linux distro and its very intimidating. Last night I kind of got the hang of house to change the themes, add icons, listen to music, add packages and stuff but now I wanna try to get starcraft up and running on this box.

So i used Wine and got it installed successfully only thing is that I installed in 
"c:\program files\starcraft"

was I supposed to do that or install it someplace else, since this computer does not have windows installed?

Anyway, i got it installed and I got it running using the wine browser, by just searching for the file in the C: directory.

Game loads but it runs slow. Is there some kind of fix for that? Also, how do I make it run windowed?

---

### Post by MoxJet on 2007-06-26
You might be able to run it windowed by running winecfg and emulating a virtual desktop under graphics.

I have got starcraft working and playing over WAN via hamachi-LAN on ubuntu some year ago. It is a widely installed game on Linux, so there should be lots of information covering it, example:
[http://appdb.winehq.org/appview.php?iAppId=72](http://appdb.winehq.org/appview.php?iAppId=72)

And by the way, if you look around in your winecfg it says that C:\ points to something like /home/dan/.wine/drive_c/

If you want to be able to view hidden files, beginning with a . (dot), press ctrl+h in nautilus, or do ls -a. 

Good luck!

---

### Post by deadgobby on 2007-06-26
[http://koti.mbnet.fi/~hoppq/sc-howto.html](http://koti.mbnet.fi/~hoppq/sc-howto.html)
 You may not met the ram or vid requirements.
Gobby
PS there is a gaming section in Ubie forums that may best to look for the answers to you questions.

---

### Post by MoxJet on 2007-06-26
Seems hard not to meet the requirements for starcraft and yet reach those for ubuntu <^^

---

### Post by pbatoon on 2007-06-26
aha sweet thanks guys! i shall report my trials in the morning.

---

### Post by xbubbax on 2007-06-26
winecfg
put it the compatabality mode set for the system the game requires ( xp 2000 98 ) 
install and enjoy.....PS....make shure your graphcs card can hanle it hehe... :)

---

### Post by Enverex on 2007-06-26
> **xbubbax said:**
> winecfg
put it the compatabality mode set for the system the game requires ( xp 2000 98 ) 
install and enjoy.....PS....make shure your graphcs card can hanle it hehe... :)

Never touch the Wine compatability mode unless something explicitly complains.

I also wouldn't recommend that FAQ, it looks horribly old and needlessly over complicated.

Starcraft works perfectly in Wine. If it seems too slow on your machine (and you DO have your graphics card drivers properly installed then run "wine regedit" and import this file: [http://winehq.atomnet.co.uk/reg/EnableOpenGLDDraw.reg](http://winehq.atomnet.co.uk/reg/EnableOpenGLDDraw.reg) That will fix the speed issues.

As mentioned before, to run it in windowed mode run "winecfg" and set Virtual Desktop to 1024x768 or something like that.

---

### Post by pbatoon on 2007-06-26
omg thanks enverex! i looked at that tutorial and i was like O_O what the F*** is this?!?!?! I dont even know how to comprehend it.  lol sry deadgobby.

I got a GeForce 6600. Heh im sure it can handle sc. Hell it even played the new elder scrolls when this box was running windows. :p

Thanks if i have any trouble. ill report back.

---

### Post by pbatoon on 2007-06-27
ok well apparently the game still runs a little laggy and theres no sound. Here is whats going on in the terminal.

```
batoon@batoon-desktop:~$ wine /media/cdrom1/setup.exe
batoon@batoon-desktop:~$ fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x17fb38) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x17f818)->(0x20024,00000013)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer
err:seh:setup_exception stack overflow 264 bytes in thread 0013 eip 7bc4518e esp 00240ef8 stack 0x241000-0x350000

```

I tried installing xwine, but i didnt know how to use it. so im back to wine. I just dont know how to get back those shortcuts I had on the start menu thing..the launcher.

---

### Post by Enverex on 2007-06-27
XWine is like a 3 year old version of Cedega. You're lucky you didn't break anything.

Did you see my - "If it seems too slow on your machine (and you DO have your graphics card drivers properly installed then run "wine regedit" and import this file: [http://winehq.atomnet.co.uk/reg/EnableOpenGLDDraw.reg](http://winehq.atomnet.co.uk/reg/EnableOpenGLDDraw.reg) That will fix the speed issues." post?

---

### Post by pbatoon on 2007-06-28
yeah the regedit import, i did first thing. surprisingly it didnt do anything.

---

