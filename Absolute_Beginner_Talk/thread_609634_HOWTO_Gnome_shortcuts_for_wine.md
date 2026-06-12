---
title: "HOWTO: Gnome shortcuts for wine"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by apienk01 on 2007-11-11
I would like to share a solution, or rather a workaround, for creating wine launchers in Gnome. I found it after lot of experimenting.

**The problem:**
When you try to add a Gnome menu entry for a wine application, it often fails because some Windows executables need to be run from their folder in order to be able to find their files, and wine does not change dir to that path on execution. So while some examples like [COLOR="Lime"]wine C:\\windows\\notepad.exe[/COLOR] will work flawlessly, some will not.

**The cause:**
If the shortcut contains spaces in path, eg. Program Files, or the executable needs command-line arguments, gnome menu is unable to parse the command-line correctly. That is because gnome menu does not use bash to start applications. That's why you can successfully launch eg. Desert Combat mod for Battlefield 1942 in terminal with [COLOR="Lime"]cd /home/yourlogin/.wine/drive_c/Program\ Files/EA\ GAMES/Battlefield\ 1942 && wine BF1942.EXE +game DC_Final[/COLOR], but putting the same in gnome menu launcher fails, because gnome menu cannot do cd. For desktop launchers there is a workaround: simply edit the launcher file with the extension ".desktop" and add a line with path:

```
Path=/home/yourlogin/.wine/drive_c/Program\ Files/EA\ GAMES/Battlefield\ 1942
Exec=wine BF1942.EXE +game DC_Final
```

Unfortunately the Path key is not currently used by gnome-menu.

**The solution:**
Launch wine inside the bash terminal and correct path with this laucher command:

```
gnome-terminal --working-directory /home/yourlogin/.wine/drive_c/Program\ Files/EA\ GAMES/Battlefield\ 1942/ -x wine BF1942.EXE +game DC_Final
```

:) Happy launching

BTW: If you want to troubleshoot your launchers, make the terminal stay open after error by selecting the respective option in gnome terminal profile settings (right click in terminal window).

---

### Post by sup on 2007-11-11
Alternatively, you can make a script like this:
```
#!/bin/bash
cd /home/tom/.wine/drive_c/Program\ Files/CAESAR\ III/
wine C3.EXE

```
that you call from GNOME (or wherever else, if you put it in the path)
and you od not even have to have a terminal flying around that you can accidentaly close.

---

