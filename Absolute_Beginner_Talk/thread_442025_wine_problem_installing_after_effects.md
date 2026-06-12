---
title: "wine problem installing after effects"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by degro on 2007-05-13
hi there, i am trying to install adobe after effects using wine, and at first i had an msxml error which i tried to correct by overriding the msxml3 native dll library.

Now it seems not to load:

```
degro@glue:~/winshare/After_Effects_7_0_Tryout.zip_FILES$ wine Setup.exe
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"msxml3.dll"
err:ole:create_server class {2933bf90-7b36-11d2-b20e-00c04f983e60} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {2933bf90-7b36-11d2-b20e-00c04f983e60} could be created for context 0x17
```

Can anybody help me or at least tell me what the error means?

Thanks, 
     Dan.

---

### Post by mejy on 2007-05-13
After Effects is a very complex and specialised piece of software that simply isn't perfected yet.  WINE isn't a perfect implementation of Windows by any means - hell WinXP wasn't a perfect implementation of Win98, and they had access to the source and all teh documentation they could wish for.  If you want to run it, your best bet is to run Windows in VMWare, Virtualbox or Qemu and install After Effects in that.  With virtual box you can even get 'seamless intergration' (or something like that) so it doesn't even feel like it's running in Windows.

---

### Post by degro on 2007-05-13
yeah, i ran it under vmware server (the free one) and shared a mapped folder with samba... the sharing worked for a few days and then just crashed :). i heard other cases like that before.. then qemu just wrecked up my ubuntu!! hell knows why, it fkt up my gdm, that just wouldn't start, i removed it, and virtualbox only runs on 32 bit. i am on amd64. know any other opensource vm software that smoothly runs on feisty 64bit?

---

### Post by lakersforce on 2007-05-13
You night want to consider running Cinelerra-CV instead. It is not anywhere as advanced as After Effects, but it got quite a big library of effects.

---

### Post by degro on 2007-05-13
i am trying to install it, but there's no package for feisty 64 and the edgy 64 packages don't work. i mean, i installed it, but when i try to import any video, it crashes.

there either doesn't seem to be any i386 packages. only for i686.

i am so sick of this. :)

anyone got any ideas how to make cinelerra run on **ubuntu 7.04 64 bit** ?! pleaaaaase.

---

### Post by mech7 on 2007-05-13
Yeah wish AE worked on WINE i can't even get it to run when i copy over the files. it asks me to register and then it tells me i don't have enough rights or that i need to reinstall it because components are missing :(

In the terminal it says this:

> err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:win:EnumDisplayDevicesW ((null),0,0x83e9ac,0x00000000), stub!
fixme:advapi:QueryServiceObjectSecurity 0x1af778 4 0x1af7c0 0 0x83e1c4
fixme:advapi:SetEntriesInAclA 1 0x83e154 0x1af748 0x83e1bc
fixme:advapi:SetServiceObjectSecurity 0x1af778 4 0x83e140
err:advapi:service_handle_start service is not stopped
err:wintab32:X11DRV_LoadTabletInfo Unable to initialized the XInput library.
chris@chris-laptop:~$ 


---

### Post by anubis4d on 2008-07-20
After FX 6.5 is working now!
[IMG]http://www.freewebs.com/mdpsistemas/foros/after6.5.jpg[/IMG]

(I have ubuntu 64 and wine)
Marquitux
[http://gvfx.blogspot.com/](http://gvfx.blogspot.com/)

---

