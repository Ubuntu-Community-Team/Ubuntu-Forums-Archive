---
title: "Photoshop CS3 on ubuntu"
date: 2008-05-18
forum: Art &amp; Design
---

### Post by Dusal on 2008-05-18
I tried to install Adobe Photoshop CS3 on my Ubuntu.
I used this guide from Wine AppDB site:

[COLOR="DimGray"]How To succesfully Install Photoshop CS3 (XP dlls required)

1. Copy mshtml, shdocvw, urlmon, shlwapi, mlang and jscript.dll from an XP partition to ~/.wine/drive_c/windows/system32

2. Do 'regsvr32 jscript.dll'

3. Do 'wget kegel.com/wine/winetricks && sh winetricks msxml3'

4. Set mshtml, shdocvw, urlmon, shlwapi, mlang to native in winecfg

All this is only needed to make the installer happy and finish fine. The actual Photoshop.exe doesn't need any native dlls set here, you only need gdiplus:

5. Do winetricks gdiplus (in console of choice)

Note: If Photoshop CS3.exe crashes, update to the very latest git, got it running there
 
Thanks to Louis Lenders for this step-by-step guide. [/COLOR]

There is an error:

[INDENT]
dusal@desktop:$ /media/sda2/Installs/Adobe/Adobe\ CS3/Setup.exe
fixme:console:AttachConsole stub ffffffff
Begin Adobe Setup
UI mode: Full GUI
End Adobe Setup.  Exit code: 4[/INDENT]

How can I fix this?

---

### Post by jedimasterk on 2008-05-18
> **Dusal said:**
> I tried to install Adobe Photoshop CS3 on my Ubuntu.
I used this guide:

[COLOR="DimGray"]How To succesfully Install Photoshop CS3 (XP dlls required)

1. Copy mshtml, shdocvw, urlmon, shlwapi, mlang and jscript.dll from an XP partition to ~/.wine/drive_c/windows/system32

2. Do 'regsvr32 jscript.dll'

3. Do 'wget kegel.com/wine/winetricks && sh winetricks msxml3'

4. Set mshtml, shdocvw, urlmon, shlwapi, mlang to native in winecfg

All this is only needed to make the installer happy and finish fine. The actual Photoshop.exe doesn't need any native dlls set here, you only need gdiplus:

5. Do winetricks gdiplus (in console of choice)

Note: If Photoshop CS3.exe crashes, update to the very latest git, got it running there
 
Thanks to Louis Lenders for this step-by-step guide. [/COLOR]

There is an error:

[INDENT]
dusal@desktop:$ /media/sda2/Installs/Adobe/Adobe\ CS3/Setup.exe
fixme:console:AttachConsole stub ffffffff
Begin Adobe Setup
UI mode: Full GUI
End Adobe Setup.  Exit code: 4[/INDENT]

How can I fix this?

Call Adobe support and blame it on them for the error!. Not natively porting their apps to Linux!.

---

### Post by MadsRH on 2008-05-18
Great work and very nice guide :)
Have you posted it at the Wine AppDB site?

---

### Post by Dusal on 2008-05-18
No I'm take it from that site and trying to install. But I have error :( Did you complete  installed it?

---

### Post by Sordelka on 2008-05-19
Checked winDb. Everyone claims that set up generally fails for CS3 on any version. So, blame Adobe :mad:

---

### Post by Sydius on 2008-05-19
I've tried a few different ways to get it to work, but haven't succeeded yet. :-(

---

### Post by Dusal on 2008-05-23
I followed this tutorial:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7694](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7694)

and Photoshop CS3 working too. But it has many bugs :(

Now I'm installed Photoshop CS. It's working great :D

---

