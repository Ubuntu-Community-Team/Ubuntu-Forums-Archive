---
title: "Gettin uTorrent to run under WINE"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by auraithx on 2007-03-11
I'm trying to get uTorrent to run under WIne, using this tutorial.

[http://news.softpedia.com/news/uTorrent-under-Ubuntu-in-3-Easy-Steps-49037.shtml](http://news.softpedia.com/news/uTorrent-under-Ubuntu-in-3-Easy-Steps-49037.shtml)

I've done it all but I get the error

"There was an error launching the application
Details: Failed to execute child process
"wine" (no such file or directory)"

---

### Post by eljalill on 2007-03-11
Maybe wine didn't install correctly?
You could try it with synaptics, or getting it straight from [www.winehq.org](www.winehq.org) . But their server is down at the moment. 

For synaptics, wine has its own repositories:
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

best of luck!

---

### Post by nudnik on 2007-03-11
> **auraithx said:**
> I'm trying to get uTorrent to run under WIne, using this tutorial.

[http://news.softpedia.com/news/uTorrent-under-Ubuntu-in-3-Easy-Steps-49037.shtml](http://news.softpedia.com/news/uTorrent-under-Ubuntu-in-3-Easy-Steps-49037.shtml)

I've done it all but I get the error

"There was an error launching the application
Details: Failed to execute child process
"wine" (no such file or directory)"

In order to install wine:

sudo apt-get install wine

To reinstall:

sudo aptitude reinstall wine

However, I strongly suggest you use a native Linux client such as Bittornado for P2P downloads.

---

### Post by astrolabio on 2007-03-11
Look i'm using uTorrent under wine right now.

It was very easy to make it work. Actually i didn't do anything :)

I don't know if this is the bet way to do this, but i tell you what i did.

I installed wine using Automatix, so maybe that's the right path.

Then i went in my windows partition with Krusader (a file manager), right clicked on uTorrent, which was alredy installed in my windows xp, and selected Wine in the "open with..." menu.

That's it. It simply worked. 

I was impressed too. :guitar: 

I have already downloaded huge files with it. It resume them fine. Simply works. :)

The only glitch is that when you minimize it or change your desktop,  it stops redrawing the window. Fortunately there is an easy  workaround: doubleclick on the little uTorrent icon on your systray (next to the icons of volume etc). It will start redrawing again.

Using this way of doing stuff i managed to make work also:
WinHex
UltraEdit
UltraCompare
TvAnts
Net Transport 
Foxit Reader.

Actually i noticed that UltraEdit is faster on Linux. I though that they bloated it after i installed it in windows. It was slower than previus versions.
In linux it's fine. Don't ask me why.

Anyway I suggest that you use winecfg to change the background color that wine use to render the windows. 
The default dark gray really SUCKS.

---

### Post by auraithx on 2007-03-11
Found the problem;

Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

I cant find it in Synaptic either.

---

### Post by eljalill on 2007-03-11
Then try putting the wine repositories in your sources.list . That way at least synaptic should find it!

---

### Post by Ebacherville on 2007-03-11
Can I ask why you just don't use a Linux Torrent application instead of running utorrent under wine?

Just seems odd to run a app that is already available in Linux, are there certain features the Linux torrent variants don't have?

Just trying to understand why.. I also use utorrent in windows and love it but there are others out there that will do the same thing natively within Linux.

Ebacherville

---

### Post by auraithx on 2007-03-11
"sudo apt-get install wine"

I installed uTorrent because I prefer it to any Ubuntu client.

---

### Post by revertex on 2007-03-11
> **auraithx said:**
> "sudo apt-get install wine"

I installed uTorrent because I prefer it to any Ubuntu client.

Ditto.

Isn't linux about choice? what about a choice to run windows apps?

IMHO, utorrent and azureus are the best choice, but even running under wine utorrent still pretty low on resources compared to azureus.
Azureus eats lots of RAM.

---

### Post by drunken_sapo on 2007-11-16
Indeed, Linux is about choices, but IMHO, utorrent is as good as Azureus or KTorrent. From the resources point of view, maybe it beats azureus, but not sure if it beats KTorrent too. So if what you save in resources pays you the pains of installing and using through wine is fine for me.

---

### Post by Znort_Ubern00b on 2007-11-16
i had serious prob geting utorrent to work...have to say ktorrent so mch easier.

---

### Post by DooX on 2007-11-16
Im getting almost same error,used same tutorial...I get error Permission denied...

Well i tried some other version of utorrent,and icon launcher on desktop doesnt execute nothing now...

---

### Post by revertex on 2007-11-16
why make things hard when it's soo easy?

install wine, do not use aptitude, it use a different database than apt-get/synaptic.

Do not mix your scripts/executables with the system ones, please don't make your box a mess, use /usr/local/bin instead /usr/bin.

install utorrent, you do not need the standalone, the instalable work as expected.

write a script, make it executable, drop it in /usr/local/bin.
Made it plain simple, name it utorrent or whatever you want.

```
#!/bin/bash
cd "$HOME"/.wine/drive_c/Program\ Files/uTorrent/
wine utorrent.exe
```if you want a menu entry, create a utorrent.desktop file, made it executable and drop it in /usr/local/share/applications.

```
[Desktop Entry]
Encoding=UTF-8
Name=utorrent
Comment=windoze Bittorent client
Exec=utorrent
Terminal=false
Type=Application
Icon=utorrent.png
Categories=Application;Network;
MimeType=application/x-bittorrent

```to show  a proper icon put a utorrent.png image in /usr/local/share/pixmaps

---

