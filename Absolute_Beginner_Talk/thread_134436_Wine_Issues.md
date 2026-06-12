---
title: "Wine Issues"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by BitTorrentBuddha on 2006-02-21
While running wine, I can't install a program right, these are the errors I get
```
fixme:win:SetWindowTextA setting text "Notepad++ v3.4 Setup" of other process window (nil) should not use SendMessage
err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\username\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\username\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\username\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\username\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\username\\Desktop"'.
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\Notepad++\\nppshellext.dll") not found
err:module:import_dll Library MSVCR71.dll (which is needed by L"C:\\Program Files\\Notepad++\\nppshellext.dll") not found
err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\username\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\username\\Desktop"'.
fixme:win:SetWindowTextA setting text "Delete file: C:\\windows\\temp\\nsh17cb.tmp\\LangDLL.dll" of other process window 0x50042 should not use SendMessage
fixme:win:SetWindowTextA setting text "Delete file: C:\\windows\\temp\\nsh17cb.tmp\\ioSpecial.ini" of other process window 0x50042 should not use SendMessage
fixme:win:SetWindowTextA setting text "Delete file: C:\\windows\\temp\\nsh17cb.tmp\\modern-wizard.bmp" of other process window 0x50042 should not use SendMessage
fixme:win:SetWindowTextA setting text "Delete file: C:\\windows\\temp\\nsh17cb.tmp\\InstallOptions.dll" of other process window 0x50042 should not use SendMessage
fixme:win:SetWindowTextA setting text "Remove folder: C:\\windows\\temp\\nsh17cb.tmp\\" of other process window 0x50042 should not use SendMessage
```
(I have tried this on multiple usernames thus replaced the usernames with "username")
(The program is [notepad++](http://sourceforge.net/projects/notepad-plus) and is open source, but I've been told can't be compiled into a binary for linux, if this is wrong, please tell me.)

---

### Post by gord on 2006-02-21
wine isn't a perfect emulator of the win32 api, in other words a lot (most) windows programs won't work, generally the ones that work are the most popular since they get the most attention.

id suggest checking out the Application Database at [www.winehq.org](www.winehq.org). it lists what applications have been confermed to work (or not) and any workarounds you might need to do.

---

### Post by nalmeth on 2006-02-22
as you'll read on winehq, wine is a windows compatibility layer, continually in development. It is not complete, but a lot of things work, or can be tweaked to work. I have had things work in wine that were listed as unuseable on winehq, too, so don't give up too easy

---

### Post by o_fortuna on 2006-02-22
[QUOTE=BitTorrentBuddha]While running wine, I can't install a program right, these are the errors I get
```
fixme:win:SetWindowTextA setting text "Notepad++ v3.4 Setup" of other process window (nil) should not use SendMessage
err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\username\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\username\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\username\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\username\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\username\\Desktop"'.
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\Notepad++\\nppshellext.dll") not found
err:module:import_dll Library MSVCR71.dll (which is needed by L"C:\\Program Files\\Notepad++\\nppshellext.dll") not found
err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\username\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\username\\Desktop"'.
fixme:win:SetWindowTextA setting text "Delete file: C:\\windows\\temp\\nsh17cb.tmp\\LangDLL.dll" of other process window 0x50042 should not use SendMessage
fixme:win:SetWindowTextA setting text "Delete file: C:\\windows\\temp\\nsh17cb.tmp\\ioSpecial.ini" of other process window 0x50042 should not use SendMessage
fixme:win:SetWindowTextA setting text "Delete file: C:\\windows\\temp\\nsh17cb.tmp\\modern-wizard.bmp" of other process window 0x50042 should not use SendMessage
fixme:win:SetWindowTextA setting text "Delete file: C:\\windows\\temp\\nsh17cb.tmp\\InstallOptions.dll" of other process window 0x50042 should not use SendMessage
fixme:win:SetWindowTextA setting text "Remove folder: C:\\windows\\temp\\nsh17cb.tmp\\" of other process window 0x50042 should not use SendMessage
```
(I have tried this on multiple usernames thus replaced the usernames with "username")
(The program is [notepad++](http://sourceforge.net/projects/notepad-plus) and is open source, but I've been told can't be compiled into a binary for linux, if this is wrong, please tell me.)[/QUOTE]
Looking at the error messages, try putting ```
MSVCP71.dll
``` into the google search engine. Download the dll and put it in /home/username/.wine/drive_c/windows/system32. This will at least solve one of the problems. Also, make sure you have run winecfg and the settings are correct for the drives (press the autodetect button).

---

### Post by BitTorrentBuddha on 2006-02-22
so the chances of getting this program running are slim to none then?

---

### Post by NicePics13 on 2006-02-22
I've added a couple of DLL-files my Wine installation complained about not having. It *should* work for a simple program like this Notepad clone. I recommend adding the most common Windows DLLs in your ***$home/.wine/drive_c/windows/system*** folder (mfc42.dll for example)

---

### Post by BitTorrentBuddha on 2006-02-22
I found a similar program that notepad++ is actually based off of, scintilla, it's even got a package in synaptic, however, after installing the package it doesn't show up in the applications menu nor does scintilla in terminal run it. I was wondering how I can run this program now? [the package is called libqscintilla5c2]

---

### Post by stalefries on 2006-02-22
It seems to me that you may have misunderstood something, as that package name tells me that it is a library, not a direct program. Libraries are sets of functions other programs can use. Try searching throught Synaptic again for scintilla, and make sure the package does not start with "lib".

---

### Post by BitTorrentBuddha on 2006-02-22
Nothing except python things = \

---

