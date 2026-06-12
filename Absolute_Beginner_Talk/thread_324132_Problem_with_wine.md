---
title: "Problem with wine"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by Doug11 on 2006-12-23
Im trying to run my apollo divx to dvd proggry but when i keep getting this error from the cammand>
doug@doug-laptop:~$ wine "C:\Program Files\Apollo DVD Creator\Apollo DVD Creator.exe"
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\Apollo DVD Creator\\Apollo DVD Creator.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Apollo DVD Creator\\Apollo DVD Creator.exe" failed, status c0000135
doug@doug-laptop:~$ 

I have dowloaded the mfc42.dll but am not quite sure where to put it.

---

### Post by rlozano on 2006-12-23
that's an MS library, and i would assume that will be in the systems32 folder if you are in windows OS.

---

### Post by Doug11 on 2006-12-23
im using this app in wine. just wondering where i should extract this .dll to

---

### Post by scrooge_74 on 2006-12-23
Do as rlozano said about putting the file in system32.

What is the exact name of the exe file?

Try changing directory until yo get to where the .exe file is, wine could get confuse with that long address (or you cuold get confused)

---

