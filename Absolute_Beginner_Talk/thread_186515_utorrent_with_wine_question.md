---
title: "utorrent with wine question"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by hikitsu4 on 2006-06-02
Hello does anyone know how i get utorrent in wine to support jap text, utorrent supports unicode so it should work, when i download the file it shows the catalog name in jap text with the filemanager nautilus, but in the utorrent window it doesnt show the torrent name or the files in correct jap text just weird symbols.

---

### Post by frodon on 2006-06-02
Wouldn't it be easier to use a linux utorrent equivalent like azureus for example, i know that utorrent is a reference for windows but linux softwares run always better on linux.

---

### Post by hikitsu4 on 2006-06-02
[QUOTE=frodon]Wouldn't it be easier to use a linux utorrent equivalent like azureus for example, i know that utorrent is a reference for windows but linux softwares run always better on linux.[/QUOTE]
Utorrent works great in linux with wine, it is fast/stable/cpu/memory friendly so why not use it. It is the best client i tried.

---

### Post by hikitsu4 on 2006-06-02
Does anyone know how to fix this problem?

---

### Post by dapperjohndoe on 2006-06-02
[QUOTE=frodon]Wouldn't it be easier to use a linux utorrent equivalent like azureus for example, i know that utorrent is a reference for windows but linux softwares run always better on linux.[/QUOTE]Azureus is also a BitTorrent client, however, it is not a Utorrent equivalent. Utorrent is fast and simple, Azureus is about the contrary... ;)

John

---

### Post by blackjack6.21.91 on 2006-06-02
You might want to install winetools, which will ease the installation of other fonts, as well as wine in general.  To do so, follow the instructions below

[http://ubuntuforums.org/showthread.php?t=149585&highlight=howto+wine](http://ubuntuforums.org/showthread.php?t=149585&highlight=howto+wine)

---

### Post by hikitsu4 on 2006-06-02
[QUOTE=blackjack6.21.91]You might want to install winetools, which will ease the installation of other fonts, as well as wine in general.  To do so, follow the instructions below

[http://ubuntuforums.org/showthread.php?t=149585&highlight=howto+wine](http://ubuntuforums.org/showthread.php?t=149585&highlight=howto+wine)[/QUOTE]
Thanks for the reply but i think that was much to read just to fix that small problem ;) ,i guess i hafto live with it. Linux it self works with jap support that is what is important.

---

### Post by lapsey on 2006-06-02
it is also advisable to add a japanese font to the wine installation

for those looking for a good native torrent program, i am told that [ktorrent](http://packages.ubuntu.com/dapper/net/ktorrent) works great.

---

### Post by Xilon on 2006-06-03
[Transmission]("http://transmission.m0k.org/") is quite similar to uTorrent (or at least when uTorrent was **very** young), I think it has a larger footprint but it works on Linux/GTK and MacOS, it's good enough for simple downloading :)

---

### Post by flapane on 2006-06-06
I have problems running utorrent1.5 with the last wine:
err:imagelist:ImageList_LoadImageW Error loading image!
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for for context 0x1
fixme:ole:CoCreateInstance no classfactory created for CLSID {304ce942-6e39-40d8-943a-b913c40c9cd4}, hres is 0x80040154
err:ole:CoGetClassObject class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:CoGetClassObject class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:create_server class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:CoGetClassObject no class object {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} could be created for for context 0x7
fixme:ole:CoCreateInstance no classfactory created for CLSID {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1}, hres is 0x80040154
err:imagelist:ImageList_LoadImageW Error loading image!
err:imagelist:ImageList_LoadImageW Error loading image!
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 15 lpiArray 0x55c1e114
fixme:keyboard:UnregisterHotKey (0x20024,1): stub

---

### Post by hikitsu4 on 2006-06-06
[QUOTE=flapane]I have problems running utorrent1.5 with the last wine:
err:imagelist:ImageList_LoadImageW Error loading image!
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for for context 0x1
fixme:ole:CoCreateInstance no classfactory created for CLSID {304ce942-6e39-40d8-943a-b913c40c9cd4}, hres is 0x80040154
err:ole:CoGetClassObject class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:CoGetClassObject class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:create_server class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:CoGetClassObject no class object {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} could be created for for context 0x7
fixme:ole:CoCreateInstance no classfactory created for CLSID {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1}, hres is 0x80040154
err:imagelist:ImageList_LoadImageW Error loading image!
err:imagelist:ImageList_LoadImageW Error loading image!
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 15 lpiArray 0x55c1e114
fixme:keyboard:UnregisterHotKey (0x20024,1): stub[/QUOTE]
I dont know exactly what this problem is but first you need to run 
sudo winecfg then press autodetect harddrives, then you need to run 
for example gksu wine /media/hda/program/utorrent.exe, (this asumes you run dual boot), i dont know your configuration i just made an example to look like my computer.
You need to use gksu (sudo) to use this program i did anyway.

---

### Post by flapane on 2006-06-07
wow it worked with sudo!!!!!!!
many thanks!

EDIT
ANyway the CPU is full load at 100% when I launch utorrent, what could it be?

---

### Post by hikitsu4 on 2006-06-07
[QUOTE=flapane]wow it worked with sudo!!!!!!!
many thanks!

EDIT
ANyway the CPU is full load at 100% when I launch utorrent, what could it be?[/QUOTE]
When i use utorrent with lots of downlods i only got about 10% cpu use if you count "wineserver and utorrent together" when you check with "top".
Then i use the k7 kernel with AMD XP 2100
I made some screenshot with my settings and packed them down in tar.gz, but before you use these settings goto "options/speed guide" and set your settings. 
And other people who use utorrent with wine should remeber you hafto use "gksu" or "sudo" when you start it or it doesnt work or it doesnt save your settings.
Hope this helps.

---

### Post by flapane on 2006-06-07
i switched to wine0.9.14 and everything went ok
[http://img108.imageshack.us/img108/1136/sk141lz.jpg](http://img108.imageshack.us/img108/1136/sk141lz.jpg)

---

### Post by hikitsu4 on 2006-06-07
[QUOTE=flapane]i switched to wine0.9.14 and everything went ok
[http://img108.imageshack.us/img108/1136/sk141lz.jpg](http://img108.imageshack.us/img108/1136/sk141lz.jpg)[/QUOTE]
Well i used the older wine before but now i use the one you use but i didnt have anyproblems but then.
I used the dapper version in both cases and both versions very new, but as long as it works it all good. :-D

---

