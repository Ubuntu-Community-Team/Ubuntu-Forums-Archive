---
title: "again wine"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by bmarilena on 2005-10-20
Hi all

again problems with wine... actually with wt2.

After wt 2 a kind of installer started... adn after fake win was set... installing DCOM98 gave me errors:
[I][SIZE=3]Installing WineTools to /usr/local/winetools...
Installing translations...
install.sh: line 22: msgfmt: command not found
Installed translations for [EMAIL="de_DE@euro"]de_DE@euro[/EMAIL] to /usr/local/share/locale/de_DE@euro/LC_MESSAGES/wt2.mo
install.sh: line 22: msgfmt: command not found
Installed translations for es to /usr/local/share/locale/es/LC_MESSAGES/wt2.mo
Start WineTools as *normal* user with "wt2". Don't use as root!
[/SIZE][SIZE=3]grep: ~/.wine/installed.reg: No such file or directory
grep: ~/.wine/installed.reg: No such file or directory
rm: cannot remove `~/.wine/installed.reg': No such file or directory
software installation verified by /home/mari/.wine/winetools.log
dcom98.exe = installed at 20.10.2005 10:34:45
dcom98.exe = installed at 20.10.2005 10:47:38
dependency dcom98.exe fulfilled
using english setup...
mv: cannot stat `~/.wine/drive_c/windows/system/regsvr32.exe': No such file or directory
Microsoft Internet Explorer.*
regedit: Can't export. Registry key 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall' does not exist!
Success
[/SIZE][SIZE=3]grep: ~/.wine/installed.reg: No such file or directory
grep: ~/.wine/installed.reg: No such file or directory
rm: cannot remove `~/.wine/installed.reg': No such file or directory
software installation verified by ~/.wine/winetools.log
ls: ie6setup.exe: No such file or directory
[/SIZE][SIZE=3]downloading [http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/ie6setup.exe]("http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/ie6setup.exe") to ie6setup.exe with 491768 bytes...
WINEDLLOVERRIDES="" wine ./ie6setup.exe
waiting for wineservers to exit...
fixme:advapi:CheckTokenMembership ((nil) 0x7fdeb0d0 0x7fb2fd9c) stub!
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advpack:TranslateInfString ("C:\\windows\\temp\\IXP000.TMP\\IESetup.inf" "Options.NTx86" "Options.NTx86" "InstallDir" 0x10253f8 260 0x7fb1f83c (nil)): stub
fixme:advpack:NeedReboot (0x00000000): stub
fixme:advpack:IsNTAdmin (0x00000000, (nil)): stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "ActiveX", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub
fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "IE4Setup.Failure", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub
fixme:advpack:RunSetupCommand ((nil), "C:\\windows\\temp\\IXP000.TMP\\IESetup.inf", "ActiveX.Failure", "C:\\windows\\temp\\IXP000.TMP", (null), (nil), 0x0000000d, (nil)): stub
fixme:advpack:ExecuteCab ((nil) 0x7fb1f9f4 (nil)): stub
all wineservers endet after 15 seconds...
Failed: 0
check installation by path or registry value...
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Microsoft Internet Explorer.*
regedit: Can't export. Registry key 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall' does not exist!
Success
[/SIZE][SIZE=3]grep: ~/.wine/installed.reg: No such file or directory
grep: ~/.wine/installed.reg: No such file or directory
rm: cannot remove `~/.wine/installed.reg': No such file or directory
software installation verified by ~/.wine/winetools.log
Failed: 1
Failed: 1
mv: cannot stat `~/.wine/drive_c/windows/system/regsvr32.exe': No such file or directory
mv: cannot stat `~/.wine/drive_c/windows/system/regsvr32.exe.wine': No such file or directory
du: cannot access `~/winetools/sys/Windows Update Setup Files': No such file or directory
du: cannot access `~i/.wine/c/windows/Windows Update Setup Files': No such file or directory
Downloaded IE6-Files=0
Winetools  IE6-Files=0[/SIZE][/I][SIZE=3]

I'm really desperate.. please help me.
[/SIZE]

---

### Post by KingBahamut on 2005-10-21
What is the program wt2?

---

### Post by bmarilena on 2005-10-21
wt2 I think is winetools 2. I got this from [http://www.ubuntuforums.org/showthread.php?t=29996&highlight=wine+cvs](http://www.ubuntuforums.org/showthread.php?t=29996&highlight=wine+cvs).

---

