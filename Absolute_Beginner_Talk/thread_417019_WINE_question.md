---
title: "WINE question"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by paker on 2007-04-21
The following is what I did to install Sibelius sheet music viewer plugin.

I downloaded a Windows program, InstallScorch.exe, to Desktop.
cd ~/Desktop
wine InstallScorch.exe

All went well until I was prompted to locate the folder for web browser (FireFox). Where is it located? I could not find it in C:\Programs.  Thanks.

---

### Post by bobplano on 2007-04-21
that is because ubuntu doesn't use a programs folder like windows does or at least a folder named programs. i don't know what folder to look for but if i find it i will put it here
EDIT: it seems everything you install goes in the /etc directory but that just looks like config files

---

### Post by Boreras on 2007-04-21
it isn't in C:\ but somewhere else on the filesystem*, but the program won't be able to do much with it. I suggest installing [IEs4linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page") or firefox in WINE (don't know if that actually works).
IEs4linux is a install script for installing, Windows Internet Explorer. Great for checking compatibiltiy of webpages, and it will probably work with your program (which I don't know, but I guess it will work).
Hope it helps.

Boreras

*edit: the general root ( "/") and home filesystem are named differently, like H:\ and Z:\ in my case. You can view this yourself by running "winecfg" in a terminal, under the tab "Drivers"

---

### Post by bobplano on 2007-04-21
well last time i tried to install ies4linux it didn't work but i'll try it again. btw it is not recommended to use that internet explorer for everyday browsing because it is a slimmed down version.
EDIT: i got the same errors as before, that there are some extra bytes at the end of the files

---

### Post by Boreras on 2007-04-21
according to the [firefox AppDB]("http://appdb.winehq.org/appview.php?iVersionId=5819"), windows firefox will install perfectly fine (3 x gold, 1 silver, 1 platinum) and simple. So you can try that.

Boreras

---

### Post by paker on 2007-04-23
Boreras,
Please explain to me what I should do. I suppose I will have to download Firefox first. If I install FireFox in wine, will it not affect the regular FireFox? The forum (link) was not specific about installation method. Thanks.

---

