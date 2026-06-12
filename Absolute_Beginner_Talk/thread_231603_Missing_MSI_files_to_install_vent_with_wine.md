---
title: "Missing MSI files to install vent with wine"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by kingvicious on 2006-08-07
well i realy do not understand how to install the MSI files to isntall vent. i have the exe file to install em into wine but i do not understand how to? i followed this guide for installing ventrilo [http://slinux.net/how-to-install-ventrilo-2-3-on-linux](http://slinux.net/how-to-install-ventrilo-2-3-on-linux) this guide tells me to download the msi files but i dont understand how to install them. i tryed skiping that step and did ever thing but when i do wine ventrilo2.3.0whatever.exe i get an error saying i need the msi files in my system folder. anywas can someone help me plz?

---

### Post by kingvicious on 2006-08-07
*bump

---

### Post by patrick295767 on 2006-08-07
[http://download.microsoft.com/download/WindowsInstaller/Install/2.0/W9XMe/EN-US/InstMsiA.exe](http://download.microsoft.com/download/WindowsInstaller/Install/2.0/W9XMe/EN-US/InstMsiA.exe)

Issue:
No 3D accleration with ATI in games
Solution:
$ export LD_PRELOAD=/usr/lib/libGL.so; cvscedega game.exe

--------------------------------------------------------------------------------
Issue:
err:font:WineEngInit FreeType support is not compiled in to wine, some font functionality will be disabled.
Solution:
Install Fontconfig, Freetype2 (libfreetype6) and Freetype2-devel


Here are some more hints about Cedega and Installshield/MSI installers from [http://www.frankscorner.org](http://www.frankscorner.org)



The CVS version of Cedega has no support for Installshield installers, but a lot of games use this installer. To make installation possible you must install the DCOM98 utility.



You can download DCOM98 here:
[http://www.microsoft.com/com/dcom/dcom98/download.asp](http://www.microsoft.com/com/dcom/dcom98/download.asp)
Type $ cvscedega dcom98.exe to install DCOM98.



To install .msi (Microsoft Installer) files get [http://download.microsoft.com/download/WindowsInstaller/Install/2.0/W9XMe/EN-US/InstMsiA.exe](http://download.microsoft.com/download/WindowsInstaller/Install/2.0/W9XMe/EN-US/InstMsiA.exe)    and install it with the command You can install Windows Installer by typing $ cvscedega instmsia.exe Now type $ cvscedega msiexec /i somefile.msi and the application will be installed.

---

### Post by kingvicious on 2006-08-07
well i acuatly use wine but i was told it was same basic steps but i also get the error missing msi files when trying to install ventrilo

---

### Post by patrick295767 on 2006-08-08
Did you try winetools also ?

---

