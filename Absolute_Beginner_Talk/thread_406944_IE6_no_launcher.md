---
title: "IE6 no launcher"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by mikewhatever on 2007-04-11
Today, I've tried installing IE6 according to a well known how-to at [http://psychocats.net/ubuntu/ies4linux](http://psychocats.net/ubuntu/ies4linux)
Everything has gone fine, but in the end, I got a ~/bin folder which is empty. A search for ie6 launcher turned up nothing, so, how do I fix or launch it.

---

### Post by LaurelLynn on 2007-04-11
Dear mikewhatever,

The first thing I noticed is that you are running Edgy (6.10) and are following a guide for Dapper(6.06).  It´s an excellent guide, but the two os versions are a bit different and use different repositories.  Look at this webpage for an explanation of what needs to be changed for Edgy:

[http://www.ubuntugeek.com/running-internet-explorer-in-ubuntu-linux.html](http://www.ubuntugeek.com/running-internet-explorer-in-ubuntu-linux.html)

---

### Post by aysiu on 2007-04-11
The first part is Dapper-specific (enabling the extra repositories through Software Properties instead of Software Sources), but the parts about installing *cabextract* and *wine* still apply to Edgy, as does the running of the IEs4Linux script.

---

### Post by mikewhatever on 2007-04-11
I've already had Universe and Multiverse enabled, so started from this step
> sudo aptitude update && sudo aptitude install cabextract wine
There was nothing unusual during the installation, pretty much according to the pictures, so I really don't know what's  wrong.

---

### Post by aysiu on 2007-04-11
Can you post the output of these commands (warning, the first command will ask for your password *and* it'll take a few minutes to execute)?: ```
sudo updatedb
locate ie6
```

---

### Post by mikewhatever on 2007-04-11
> **aysiu said:**
> Can you post the output of these commands (warning, the first command will ask for your password *and* it'll take a few minutes to execute)?: ```
sudo updatedb
locate ie6
```
Thanks for your reply.
> sudo updatedb
Password:
none@hello:~$ locate ie6
/home/none/.ies4linux/downloads/ie6
/home/none/.ies4linux/downloads/ie6/EN-US
/home/none/.ies4linux/downloads/ie6/EN-US/ADVAUTH.CAB
/home/none/.ies4linux/downloads/ie6/EN-US/CRLUPD.CAB
/home/none/.ies4linux/downloads/ie6/EN-US/HHUPD.CAB
/home/none/.ies4linux/downloads/ie6/EN-US/IEDOM.CAB
/home/none/.ies4linux/downloads/ie6/EN-US/IE_EXTRA.CAB
/home/none/.ies4linux/downloads/ie6/EN-US/IE_S1.CAB
/home/none/.ies4linux/downloads/ie6/EN-US/IE_S2.CAB
/home/none/.ies4linux/downloads/ie6/EN-US/IE_S5.CAB
/home/none/.ies4linux/downloads/ie6/EN-US/IE_S4.CAB
/home/none/.ies4linux/downloads/ie6/EN-US/IE_S3.CAB
/home/none/.ies4linux/downloads/ie6/EN-US/IE_S6.CAB
/home/none/.ies4linux/downloads/ie6/EN-US/SCR56EN.CAB
/home/none/.ies4linux/downloads/ie6/EN-US/SETUPW95.CAB
/home/none/.ies4linux/downloads/ie6/EN-US/FONTCORE.CAB
/home/none/.ies4linux/downloads/ie6/EN-US/FONTSUP.CAB
/home/none/.ies4linux/downloads/ie6/EN-US/VGX.CAB
/home/none/.ies4linux/ie6
/home/none/.ies4linux/ie6/dosdevices
/home/none/.ies4linux/ie6/dosdevices/c:
/home/none/.ies4linux/ie6/dosdevices/z:
/home/none/.ies4linux/ie6/dosdevices/d::
/home/none/.ies4linux/ie6/dosdevices/d:
/home/none/.ies4linux/ie6/drive_c
/home/none/.ies4linux/ie6/drive_c/windows
/home/none/.ies4linux/ie6/drive_c/windows/command
/home/none/.ies4linux/ie6/drive_c/windows/command/start.exe
/home/none/.ies4linux/ie6/drive_c/windows/fonts
/home/none/.ies4linux/ie6/drive_c/windows/inf
/home/none/.ies4linux/ie6/drive_c/windows/inf/wine.inf
/home/none/.ies4linux/ie6/drive_c/windows/system
/home/none/.ies4linux/ie6/drive_c/windows/system32
/home/none/.ies4linux/ie6/drive_c/windows/system32/drivers
/home/none/.ies4linux/ie6/drive_c/windows/system32/advapi32.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/advpack.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/cmd.exe
/home/none/.ies4linux/ie6/drive_c/windows/system32/comctl32.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/comdlg32.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/control.exe
/home/none/.ies4linux/ie6/drive_c/windows/system32/crypt32.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/d3d8.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/d3d9.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/dbghelp.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/ddhelp.exe
/home/none/.ies4linux/ie6/drive_c/windows/system32/ddraw.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/dsound.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/dsound.vxd
/home/none/.ies4linux/ie6/drive_c/windows/system32/explorer.exe
/home/none/.ies4linux/ie6/drive_c/windows/system32/gdi32.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/hhctrl.ocx
/home/none/.ies4linux/ie6/drive_c/windows/system32/imaadp32.acm
/home/none/.ies4linux/ie6/drive_c/windows/system32/imagehlp.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/kernel32.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/msadp32.acm
/home/none/.ies4linux/ie6/drive_c/windows/system32/msg711.acm
/home/none/.ies4linux/ie6/drive_c/windows/system32/msi.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/msiexec.exe
/home/none/.ies4linux/ie6/drive_c/windows/system32/msvcrt.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/notepad.exe
/home/none/.ies4linux/ie6/drive_c/windows/system32/ntdll.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/ole32.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/oleaut32.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/olepro32.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/opengl32.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/progman.exe
/home/none/.ies4linux/ie6/drive_c/windows/system32/regsvr32.exe
/home/none/.ies4linux/ie6/drive_c/windows/system32/riched20.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/riched32.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/rpcrt4.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/setupapi.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/shdocvw.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/shell32.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/shfolder.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/shlwapi.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/urlmon.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/user32.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/version.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/wininet.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/winmm.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/winspool.drv
/home/none/.ies4linux/ie6/drive_c/windows/system32/winver.exe
/home/none/.ies4linux/ie6/drive_c/windows/system32/ws2_32.dll
/home/none/.ies4linux/ie6/drive_c/windows/system32/wsock32.dll
/home/none/.ies4linux/ie6/drive_c/windows/temp
/home/none/.ies4linux/ie6/drive_c/windows/win.ini
/home/none/.ies4linux/ie6/drive_c/windows/system.ini
/home/none/.ies4linux/ie6/drive_c/windows/profiles
/home/none/.ies4linux/ie6/drive_c/windows/profiles/none
/home/none/.ies4linux/ie6/drive_c/windows/profiles/none/Desktop
/home/none/.ies4linux/ie6/drive_c/windows/profiles/none/Local Settings
/home/none/.ies4linux/ie6/drive_c/windows/profiles/none/Local Settings/Temporary Internet Files
/home/none/.ies4linux/ie6/drive_c/windows/profiles/none/Local Settings/History
/home/none/.ies4linux/ie6/drive_c/windows/profiles/none/Local Settings/Application Data
/home/none/.ies4linux/ie6/drive_c/windows/profiles/none/Cookies
/home/none/.ies4linux/ie6/drive_c/windows/profiles/none/My Documents
/home/none/.ies4linux/ie6/drive_c/windows/profiles/none/My Pictures
/home/none/.ies4linux/ie6/drive_c/windows/profiles/none/My Video
/home/none/.ies4linux/ie6/drive_c/windows/profiles/none/My Music
/home/none/.ies4linux/ie6/drive_c/windows/profiles/none/Start Menu
/home/none/.ies4linux/ie6/drive_c/windows/profiles/none/Start Menu/Programs
/home/none/.ies4linux/ie6/drive_c/windows/profiles/none/Start Menu/Programs/StartUp
/home/none/.ies4linux/ie6/drive_c/windows/profiles/none/Favorites
/home/none/.ies4linux/ie6/drive_c/windows/profiles/none/Application Data
/home/none/.ies4linux/ie6/drive_c/windows/profiles/none/Recent
/home/none/.ies4linux/ie6/drive_c/windows/profiles/none/SendTo
/home/none/.ies4linux/ie6/drive_c/windows/profiles/none/NetHood
/home/none/.ies4linux/ie6/drive_c/windows/profiles/none/Templates
/home/none/.ies4linux/ie6/drive_c/windows/profiles/none/PrintHood
/home/none/.ies4linux/ie6/drive_c/windows/profiles/All Users
/home/none/.ies4linux/ie6/drive_c/windows/profiles/All Users/Start Menu
/home/none/.ies4linux/ie6/drive_c/windows/profiles/All Users/Start Menu/Programs
/home/none/.ies4linux/ie6/drive_c/windows/profiles/All Users/Start Menu/Programs/StartUp
/home/none/.ies4linux/ie6/drive_c/windows/profiles/All Users/Desktop
/home/none/.ies4linux/ie6/drive_c/windows/profiles/All Users/Favorites
/home/none/.ies4linux/ie6/drive_c/windows/profiles/All Users/Application Data
/home/none/.ies4linux/ie6/drive_c/windows/profiles/All Users/Templates
/home/none/.ies4linux/ie6/drive_c/windows/profiles/All Users/Documents
/home/none/.ies4linux/ie6/drive_c/windows/notepad.exe
/home/none/.ies4linux/ie6/drive_c/windows/regedit.exe
/home/none/.ies4linux/ie6/drive_c/windows/rundll32.exe
/home/none/.ies4linux/ie6/drive_c/windows/winebrowser.exe
/home/none/.ies4linux/ie6/drive_c/windows/winhelp.exe
/home/none/.ies4linux/ie6/drive_c/Program Files
/home/none/.ies4linux/ie6/drive_c/Program Files/Common Files
/home/none/.ies4linux/ie6/system.reg
/home/none/.ies4linux/ie6/userdef.reg
/home/none/.ies4linux/ie6/user.reg
/home/none/ies4linux-2.0.5/winereg/ie6.reg


---

### Post by aysiu on 2007-04-11
Hm. It looks as if it may have dumped the launcher in something other than ~/bin

Can you try this? ```
cd /home/none/.ies4linux/
./ie6
```

---

### Post by mikewhatever on 2007-04-11
> **aysiu said:**
> Hm. It looks as if it may have dumped the launcher in something other than ~/bin

Can you try this? ```
cd /home/none/.ies4linux/
./ie6
```
the output:

> $ cd /home/none/.ies4linux/
[email]none@hello:~/.ies[/email]4linux$ ./ie6
bash: ./ie6: is a directory
[email]none@hello:~/.ies[/email]4linux$ 


---

### Post by aysiu on 2007-04-11
Then I'm stumped.

Looking back at your earlier output, that makes sense. It is a directory, but I don't see a launcher in there anywhere. Maybe something's wrong with the IEs4Linux script now...? I haven't used it in quite a while (my Psychocats screenshots are from Dapper, so it's been at least six months, if not longer).

Anyone else used the script recently? Have the same problem?

---

### Post by bobplano on 2007-04-11
ive been having the same problem. try going to the directory of the installer (in the terminal) and typing in 
```
./ies4linux
```
which will run the script from the terminal but more importantly show you any errors it is coming up with

i got errors like:
```
/home/keith/.ies4linux/downloads/ie6/EN-US//VGX.CAB: WARNING; possible 713248 extra bytes at end of file.
vgx.dll: checksum error
```

---

### Post by mikewhatever on 2007-04-11
yes, lots of errors there. That probably explains the issue. I really don't like those extra bytes.
> Installing IE 6
  Initializing
  Creating Wine Prefix
  Extracting CAB files
/home/none/.ies4linux/downloads/ie6/EN-US//ADVAUTH.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/none/.ies4linux/downloads/ie6/EN-US//CRLUPD.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/none/.ies4linux/downloads/ie6/EN-US//HHUPD.CAB: WARNING; possible 6720 extra bytes at end of file.
/home/none/.ies4linux/downloads/ie6/EN-US//IEDOM.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/none/.ies4linux/downloads/ie6/EN-US//IE_EXTRA.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/none/.ies4linux/downloads/ie6/EN-US//IE_S1.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/none/.ies4linux/downloads/ie6/EN-US//IE_S2.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/none/.ies4linux/downloads/ie6/EN-US//IE_S3.CAB: WARNING; possible 124183 extra bytes at end of file.
ie_3.cab: checksum error
/home/none/.ies4linux/downloads/ie6/EN-US//IE_S4.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/none/.ies4linux/downloads/ie6/EN-US//IE_S5.CAB: WARNING; possible 6752 extra bytes at end of file.
/home/none/.ies4linux/downloads/ie6/EN-US//IE_S6.CAB: WARNING; possible 264823 extra bytes at end of file.
ie_6.cab: checksum error
/home/none/.ies4linux/downloads/ie6/EN-US//SCR56EN.CAB: WARNING; possible 806829 extra bytes at end of file.
jscript.dll: checksum error
/home/none/.ies4linux/downloads/ie6/EN-US//SETUPW95.CAB: WARNING; possible 916531 extra bytes at end of file.
acmsetup.exe: checksum error
/home/none/.ies4linux/downloads/ie6/EN-US//VGX.CAB: WARNING; possible 577147 extra bytes at end of file.
vgx.dll: checksum error
An error occured when trying to cabextract some files.


---

### Post by mikewhatever on 2007-04-13
Since it wasn't working the way expected, I removed both wine and ie4linux. The issue is not of major importance. I dual boot, so have the original XP, but thought I'd try it out of curiosity. vmware does the same (in a small window), no harm's done.
Thanks to all who answered. :popcorn:

---

