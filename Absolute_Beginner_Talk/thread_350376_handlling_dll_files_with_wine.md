---
title: "handlling dll files with wine"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2007-01-31
I am using dappler drake. I insisted for a while not to use any windows application but I gave up finally. I installed wine last week and I run two small very specific applications.
it worked just fine. But today I wanted to run another windows application and I got the following error message:

> ozkaynak@ozkaynak:~$ wine ~/CW-Cryptic.exe
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"Z:\\home\\mozkaynak\\CW-Cryptic.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\mozkaynak\\CW-Cryptic.exe" failed, status c0000135


the message is pretty clear: I am lacking a specific DLL file.
I dont know how to install DLL files or is there any other way to handle these kinds of problems.

at this point I try not to use vmware because my notebook is not a good one.any solution without vmware or telling me that I have to use vmware will be highly appreciated.

---

### Post by machoo02 on 2007-01-31
Head on over to [http://www.dll-files.com/dllindex/dll-files.shtml?msvbvm60]("http://www.dll-files.com/dllindex/dll-files.shtml?msvbvm60") to grab yourself a copy, and drop it into ~/.wine/drive_c/windows/system32

Hopefully, that should do the trick.

---

### Post by the_darkside_986 on 2007-01-31
I heard that one can use real windows dll files for wine... Is it a good idea to copy a couple of dll's from my win32 partition and drop them there? I want to play Deer Avenger 4 on wine because I almost had it working yesterday until it got to the part where the gameplay starts. The sound doesn't work. I think I might need to copy a direct3d and directsound dll into wine's folder.

---

