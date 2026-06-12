---
title: "Help with wine - 0x80040154 error"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by davidtv on 2007-08-09
I am installing Image Grabber II (win) through Wine, and the install went fine. But when I tried to run the program, I just get "error 0x80040154". I think I am missing some .dll-files, and searching the net gave me multiple responses on which files I was missing. I downloaded the dll-files, and placed them in my .wine/drive_c/windows/system32/ folder. But I still get the same error message. Is there something I need to do, rather than just placing the files in the dir?

---

### Post by splintercellguy on 2007-08-09
Can you tell me what version of Wine you are running, and the full terminal output when you try to run the application in the Terminal?

---

### Post by protenniser on 2008-02-14
Hi,
It is rather an old topic but I am getting the same error.
Here is the info:
```

kmuslu@kmuslu-laptop:~/Net Loader downloads/Lesbicky akce 1$ wine --version
wine-0.9.44

```
and output in terminal:
```

kmuslu@kmuslu-laptop:~/Net Loader downloads/Lesbicky akce 1$ wine /home/kmuslu/.wine/drive_c/Program\ Files/Image\ Grabber\ II/Image\ Grabber\ II.exe 
err:ole:CoGetClassObject class {51b4abf3-748f-4e3b-a276-c828330e926a} not registered
err:ole:CoGetClassObject class {51b4abf3-748f-4e3b-a276-c828330e926a} not registered
err:ole:CoGetClassObject no class object {51b4abf3-748f-4e3b-a276-c828330e926a} could be created for context 0x3
fixme:quartz:AMGetErrorTextA (80040154,0x33fa28,160) stub

```
It would be really great if I could run image grabber II on linux, thanks...

---

