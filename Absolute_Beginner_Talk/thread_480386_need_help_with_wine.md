---
title: "need help with wine"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by drsyntax on 2007-06-21
when i try to run Army men RTS (Game) using wine i got this on my terminal window and the game doesn't run

```
tamer@bello:~/.wine/drive_c/Program Files/ARMYMEN$ wine ahmrts.exe
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x16fbf0) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x16dcd0)->(0x10024,00001008)
fixme:ddraw:IDirectDrawImpl_CreateSurface Wanted to get surface dimensions from window 0x10024, but it has only a size of 0x0. Using full screen dimensions
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x16dcd0)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x16dcd0)->(0x10024,00001008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x16dcd0)->(0x10024,00001013)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
Segmentation fault (core dumped)
```

any one can help??

---

### Post by EagleRock on 2007-06-21
Honestly, I don't think I can help you much, but the error you're getting seems to indicate that it's trying to switch from 32bit to 16bit rendering.  I don't know much about the Army Men game, but if there's a config file where you can specify the rendering type, you might be able to bypass it that way.

Unfortunately, that's about all I can think of.  I just didn't want to keep you hanging.  :-)

---

### Post by FleetAdmiral74 on 2007-06-21
[http://appdb.winehq.org/appview.php?iAppId=5055](http://appdb.winehq.org/appview.php?iAppId=5055)

Wine DB does not seem to have support for it right now. General advice would be to double check video and audio settings in your wine config.

---

