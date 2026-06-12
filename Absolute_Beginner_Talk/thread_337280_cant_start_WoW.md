---
title: "cant start WoW"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by noenter1 on 2007-01-12
Ok i installed win and WoW followed all the instructions for the 6.10amd64 installed all .dlls installed all drivers and this is what is happening when i try to run WoW: ```
no1enter@rurouni2:~$ wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/no1enter', starting in the Windows directory.
wine: cannot find '/home/no1enter/.wine/drive_c/Program Files/World of Warcraft/WoW.exe'
```
Does anyone know why this is happening and how to fix it?

---

### Post by pay on 2007-01-12
Run ```
winecfg
```

---

### Post by noenter1 on 2007-01-13
```
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/no1enter', starting in the Windows directory.
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") failed (error c000007a).
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007a).
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007a).
err:module:import_dll Library comctl32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007a).
err:module:import_dll Library shell32.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") failed (error c000007a).
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007a).
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007a).
err:module:import_dll Library comctl32.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\winspool.drv") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\winspool.drv") failed (error c000007a).
err:module:import_dll Library winspool.drv (which is needed by L"c:\\windows\\system32\\comdlg32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") failed (error c000007a).
err:module:import_dll Library comdlg32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007a).
err:module:import_dll Library comctl32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") failed (error c000007a).
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007a).
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\comctl32.dll") failed (error c000007a).
err:module:import_dll Library comctl32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007a).
err:module:import_dll Library shell32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") failed (error c000007a).
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\winmm.dll") not found
err:module:import_dll Library winmm.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") failed (error c000007a).
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") failed (error c000007a).
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\uxtheme.dll") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\uxtheme.dll") failed (error c000007a).
err:module:import_dll Library uxtheme.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") failed (error c000007a).
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\winecfg.exe" failed, status c0000135
```
Apperently im missing allot of dlls.

---

### Post by noenter1 on 2007-01-13
I am currently copying all my windows dlls to my linux hard drive.

---

### Post by noenter1 on 2007-01-13
Ok nvm didnt work still get the same thing...

---

### Post by OldTimeTech on 2007-01-13
Sorry, my husband's machine is acting up (of course it's windoze) and it won't let me put the right url up for you to check out.

---

### Post by OldTimeTech on 2007-01-13
[http://www.ubuntuforums.org/showthread.php?t=185557&highlight=Elf+Class+64](http://www.ubuntuforums.org/showthread.php?t=185557&highlight=Elf+Class+64)

---

### Post by OldTimeTech on 2007-01-13
Okay, I think above will help on your problem....sorry it took so long.

---

### Post by noenter1 on 2007-01-13
Thanks working so far currently patching.

---

### Post by noenter1 on 2007-01-13
Ok... can start wow and login, but after the loading screen finishes it exits out of the game.

---

### Post by noenter1 on 2007-01-13
nvm got it working now.

---

