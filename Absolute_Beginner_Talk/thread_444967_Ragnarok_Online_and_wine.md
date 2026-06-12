---
title: "Ragnarok Online and wine"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by h2z on 2007-05-15
Trying to run the game "ragnarok online" using wine, the game load but is really slow and the terminal produces the following "fixme":

```

fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x1621a0)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x1621a0)->(1,(nil)): Stub

```

The message repeats itself several times per second without an apparent end (kept getting the error for 10 mins untill I closed wine).  My question is this; could this have something to do with vsync option? I havent found a way to set if off yet :confused: 



This is what I get right after running the game with wine;

```

stefan@stefan:~/Ragnarok-Online$ wine CrescendoRO.exe -1rag1
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x177710) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1621a0)->(0x10024,00000c08)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel DirectDraw is not thread safe yet
fixme:d3d:IWineD3DDeviceImpl_SetMultithreaded No thread safety in wined3d yet
err:d3d_surface:d3dfmt_convert_surface Unsupported conversation type 9
fixme:d3d_surface:surface_download_data Read back converted textures unsupported
err:d3d_surface:d3dfmt_convert_surface Unsupported conversation type 9
fixme:d3d_surface:surface_download_data Read back converted textures unsupported
err:d3d_surface:d3dfmt_convert_surface Unsupported conversation type 9
fixme:d3d_surface:surface_download_data Read back converted textures unsupported
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:imm:ImmReleaseContext (0x10024, 0x162dc8): stub
fixme:imm:ImmReleaseContext (0x10024, 0x162dc8): stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x1621a0)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x1621a0)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x1621a0)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x1621a0)->(1,(nil)): Stub

```


This is when closing the program:

```

fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x1621a0)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x1621a0)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1621a0)->(0x10024,00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1621a0)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
err:ole:CoUninitialize Mismatched CoUninitialize

```

---

### Post by blazercist on 2007-05-16
This has nothing to do with vsync, these are Direct3d errors because wine obviously has very limited D3d support, only the bare essentials.

The slowness is probably a result of all those messages being plastered across the terminal window, start the game with 

WINEDEBUG=-all wine game.exe 

this will keep those messages from appearing and will speed up the game.

---

### Post by Beta_Solution on 2007-05-25
Soo.... Is there a way to fix WINE so it can run Direct3d a bit better then?

---

