---
title: "Wine and WineTools"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by underworld288 on 2006-07-02
I have Wine and WineTools installed but I need to install Windows Installer and when I go to install it with WineTools I get this.....

[I]sytempath=/home/underworld288/.wine/dosdevices/c:/windows/system32
InstMsiA.exe to check
software installation verified by /home/underworld288/.wine/winetools.log
1709160 bytes previously downloaded
WINEDEBUG="fixme-all" WINEDLLOVERRIDES="" wine ./InstMsiA.exe
waiting for wineservers to exit...
all wineservers endet after 1 seconds...
Failed: 253
check installation by return value...
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Failed: 253
\*new\* fake Windows drive to check
software installation verified by /home/underworld288/.wine/winetools.log
*new* fake Windows drive = installed at 02.07.2006 17:29:11
dependency \*new\*
dcom98.exe to check
software installation verified by /home/underworld288/.wine/winetools.log
dcom98.exe = installed at 02.07.2006 17:30:39
dependency dcom98.exe fulfilled
Microsoft Internet Explorer.* to check
Microsoft Internet Explorer 6 SP1 and Internet Tools
software installation verified by registry value
dependency Microsoft[/I]

then it says that the installation failed, I don't know what to do. Can anyone help?

thanks

---

### Post by Apple 101 on 2006-07-03
What are you trying to install?

---

### Post by underworld288 on 2006-07-03
Windows Installler

---

### Post by Apple 101 on 2006-07-04
Can I ask why you would need the Windows installer?

---

### Post by wylfing on 2006-07-04
*boggle*

Can you be a lot more specific about what "Windows Installer" is and what you are trying to accomplish? Are you talking about that thing that lets you install from MSI files? Or, heaven forbid, are you talking about installing Windows itself?

---

### Post by underworld288 on 2006-07-04
I need to install Windows Installer to install BF1942 on my system.

---

### Post by Apple 101 on 2006-07-05
Couldn't you just play the Linux version of Battlefield 1942?  I found a version for Linux on Google.

---

### Post by wylfing on 2006-07-05
IIRC, the Linux version of it is a dedicated server, not a game client. You need wine or Cedega to run the Windows client if you want to play the game.

I would be surprised if there is any kind of "windows installer" you need. Just get a copy of Cedega and do the install like you would on Windows. It's an officially supported game for Transgaming, so there shouldn't be any issues.

---

