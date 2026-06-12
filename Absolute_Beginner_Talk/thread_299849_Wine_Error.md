---
title: "Wine Error"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-11-14
So I downloaded a .zip, extracted it in my home folder, it created a file called Setup.exe, so I ran a "wine Setup.exe", and I get this:

sam@sam-laptop:~$ wine Setup.exe
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"H:\\Setup.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"H:\\Setup.exe" failed, status c0000135

---

### Post by voodoonirvana on 2006-11-14
Anybody?

---

### Post by That_Geek on 2006-11-14
well, for one, .exes dont work on linux

try using syaptic

(find it under system--> admin ---> synaptic)

if you dont like looking for it in synaptic

go to terminal (--> apps ---> accessories --> Terminal)
type in 

```
 sudo apt-get install wine 
```

---

### Post by CatKiller on 2006-11-14
I'm sure you're aware of the order of magnitude of the number of distinct files called "Setup.exe" there are in the world. Check the [WineHQ Applications Database]("http://appdb.winehq.org/") for whatever it was you downloaded. If someone says they got it to work, do what they did. If no one does, then it probably doesn't.

Don't bump your messages after such a short time. It's really rude. Half an hour? Come on...

---

### Post by 3rdalbum on 2006-11-14
If you still have a Windows partition, find the file "MSVBVM60.DLL" on there, and put it into ~/.wine/drive_c/system/.

This is the way I do it, but I've always thought that there's been a cleaner way of getting Wine to use your existing Windows DLLs.

---

