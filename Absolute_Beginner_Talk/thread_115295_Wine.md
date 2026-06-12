---
title: "Wine"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by limguohong91 on 2006-01-10
I think this is the best place I can seek help about WINE, I apologise if I am wrong.

I have install WINE through Synaptic and It did. Afterwhich i tried to start Wine through Terminal which gets me this

[php]limguohong91@cm46:~$ wine
Warning: Language 'en_SG' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_SG' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_SG' was not recognized, defaulting to 'en_US'.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system" is not accessible.
Warning: could not find DOS drive for current working directory '/home/limguohong91', starting in the Windows directory.
Wine 20050725
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
[/php]

So when I type wine notepad.exe or whatever for a start It gave me 

[php]Warning: Language 'en_SG' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_SG' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_SG' was not recognized, defaulting to 'en_US'.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system" is not accessible.
Warning: could not find DOS drive for current working directory '/home/limguohong91', starting in the Windows directory.[/php]


I am not sure what should I do to solved it. I think these information might help you
1. I have a fake Window install on Ubuntu
2. This is what the config have under /home/.wine/config

[php][wine]
"Windows" = "/home/limguohong91/.wine/fake_windows/Windows"
"System" = "/home/limguohong91/.wine/fake_windows/Windows/System"
"Temp" = "X:\\"
"Path" = "/home/limguohong91/.wine/fake_windows/Windows;/home/limguohong91/.wine/fake_windows/Windows/System;X:\\;X:\\test;Y:\\"
"GraphicsDriver" = "x11drv"
; Wine doesn't pass directory symlinks to Windows programs by default.
; Enabling this may crash some programs that do recursive lookups of a whole
; subdir tree in case of a symlink pointing back to itself.
;"ShowDirSymlinks" = "1"
;"ShowDotFiles" = "1"
"ShellLinker" = "wineshelllink"

# [wineconf]

[Version]
; Windows version to imitate (win95,win98,winme,nt351,nt40,win2k,winxp,win2k3,win20,win30,win31)
"Windows" = "win98"
; DOS version to imitate
;"DOS" = "6.22"[/php]

Thanks a lot if you can help me. I am a starter at all these

---

### Post by kosmic on 2006-01-10
In a terminal do a :
 
sudo dpkg-reconfigure locales and select your local, with should be EN-GB or US

---

