---
title: "how can I start an application installed with wine?"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-04-28
I installed wine, then downloaded an "exe" package ... I know the path to the EXE file after the install is done. now I am trying to start this application, but I don't know the command for this ... can somebody help me please?

---

### Post by frodon on 2006-04-28
The command is : ```
wine path_to_the_exe
```A double click on the .exe in nautilus (the GNOME file browser) also works.

---

### Post by Isoss on 2006-04-28
oh, thought wine command is just for installing .. ok ... it worked and opened the program but the program seems not to work properly ... it gave me 3 errors (can't open file *** ) is it just the program? or that exe files are not really executable in linux systems?

---

### Post by Isoss on 2006-04-28
I also wanna know how to uninstall a program that was installed with wine. Thanks

---

### Post by frodon on 2006-04-28
The wine command is not just for installing things, it allows you to run  .exe files and therefore it is used to starts the programs too.

To uninstall the program just run the uninstall.exe file of the program with wine.

For your error could you post the terminal output you get ?

---

### Post by Isoss on 2006-04-28
OK ... first, it's a bible program called e-sword, I searched online for a linux package but couldn't find anything but someone asking for it and someone else telling how to install it on linux, and that it worked. 
So as I run the prog, it displays it's launching logo like any other program attempting to open, while terminal is working, three errors alerts pop up:
1. Error encountered opening bible file: C:\Program Files\e-Sword\kjv+.bbl
2. Error encountered opening bible file: C:\Program Files\e-Sword\strong.dct
3. Automation error: 2147221168

The terminal output is pretty long, so I'll just post the bottom part of it:

```
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x7fdfa3a4), stub!
fixme:ole:OLEFontImpl_Invoke property put for Size with vt 3 unsupported!
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGING: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGED: stub
fixme:richedit:RichEditANSIWndProc EM_SETTARGETDEVICE: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGING: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGED: stub
err:ole:CoGetClassObject class {00000100-0000-0010-8000-00aa006d2ea4} not registered
err:ole:create_server class {00000100-0000-0010-8000-00aa006d2ea4} not registered
err:ole:CoGetClassObject class {00000100-0000-0010-8000-00aa006d2ea4} not registered
err:ole:create_server class {00000100-0000-0010-8000-00aa006d2ea4} not registered

```

And ofcourse the logo isappears and terminal freezes and doesn't do anything untill I press Ctrl+C

---

### Post by frodon on 2006-04-28
mmm, the terminal output is not really explicit :( don't know what is the problem here.
Here are some links i found on the topic : 
[http://ubuntuforums.org/showthread.php](http://ubuntuforums.org/showthread.php)
[http://frankscorner.org/index.php?p=e-sword](http://frankscorner.org/index.php?p=e-sword)
[http://appdb.winehq.org/appview.php?appId=1341](http://appdb.winehq.org/appview.php?appId=1341)
[http://appdb.winehq.org/appview.php?versionId=1877](http://appdb.winehq.org/appview.php?versionId=1877)

By the way if you don't use the latest verion of wine i advice you toinstall it : [http://doc.gwos.org/index.php/Wine](http://doc.gwos.org/index.php/Wine)

---

### Post by Isoss on 2006-04-28
Alright .. I also found this while searching [http://frankscorner.org/index.php?p=e-sword](http://frankscorner.org/index.php?p=e-sword)

so this page says that I need to edit ~/.wine.conf 
but I couldn't find this file! even when set to show hidden files!

---

### Post by frodon on 2006-04-28
sorry the link to the forum thread was broken, here it is : [http://ubuntuforums.org/showthread.php?t=151708](http://ubuntuforums.org/showthread.php?t=151708)

Gnomesword seems a good alternative.

---

### Post by Isoss on 2006-04-28
I need a multilingual bible ... I use English, Arabic, Turkish, Hebrew, Greek ... and E-sword also has dictionaries for the original languages and great comentaries as well ... does Gnomesword have the same?

---

