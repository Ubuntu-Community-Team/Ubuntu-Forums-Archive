---
title: "utorrent"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by dunedust on 2007-04-03
i recently installed utorrent + wine using this tutorial

[http://ubuntuforums.org/showthread.php?t=295134&highlight=utorrent+using+wine]("http://ubuntuforums.org/showthread.php?t=295134&highlight=utorrent+using+wine")

it worked perfectly till yesterday until i deleted my default panels and replaced them with a single panel on top
now when i try launching it nothing happens
the u torrent sign does not show in the panel like it used to 
im not sure if its running in the background somewhere
please help

---

### Post by phr0z3n on 2007-04-03
Well, you could just use operas built in torrent downloader man :-D. There are plenty of Torrent apps for *NIX as well, just take a look around the packages!

---

### Post by TheMono on 2007-04-04
[Plug]
Have you tried Ktorrent?
[/plug]

---

### Post by Dual Cortex on 2007-04-04
Well, I don't mess with Wine much... but how about reinstalling utorrent?

---

### Post by DennShin on 2007-04-04
I would second KTorrent.  It seems nearly identical to utorrent but is native so it should install and run with far less problems and then you can drag and drop it to your panel if you wish. 

But if your heart is set on it, Alt+Tab should bring it up if its running minimized.  I am not sure about your panel though sorry =(

---

### Post by tonyr1988 on 2007-04-04
Open a Terminal (Applications >> Accessories >> Terminal) and copy / paste:

> wine ~/.utorrent/utorrent.exe

Copy and paste anything that it spits out. If there's some errors, we may be able to find out specifically what the problem is.

---

### Post by Doug11 on 2007-04-04
> **dunedust said:**
> i recently installed utorrent + wine using this tutorial

[http://ubuntuforums.org/showthread.php?t=295134&highlight=utorrent+using+wine]("http://ubuntuforums.org/showthread.php?t=295134&highlight=utorrent+using+wine")

it worked perfectly till yesterday until i deleted my default panels and replaced them with a single panel on top
now when i try launching it nothing happens
the u torrent sign does not show in the panel like it used to 
im not sure if its running in the background somewhere
please help

For some reason I like Utorrent as well. You should be able to go into your home folder, show hidden files, then into your .wine folder>c:>and you should find the Utorent.exe in there to start it back up.

---

### Post by david_kt on 2007-04-04
Try to right click on your new panel, and then click add to panel, and then drag notification area and drop it on your panel. After that try to run utorrent from terminal:

wine /home/<username>/.utorrent/utorrent.exe

I am not sure whether it work or not though. But if it works, you can edit your launcher:

sudo gedit /usr/share/applications/utorrent.desktop

replace: Exec=alltray --icon /home/<username>/.utorrent/utorrenteh8.png wine /home/<username>/.utorrent/utorrent.exe
with: Exec= wine /home/<username>/.utorrent/utorrent.exe

so that you can use your launcher again. I am not sure why he need to use alltray. I am using standalone utorrent and it work perfectly without alltray.

DK

---

### Post by dunedust on 2007-04-04
well adding the notification area to the panel seems to have done it 
thanks a lot
its working fine now
personally i prefer using u torrent as it utilizes almost the entire bandwidth
other than that ive tried azureus but it uses up too much memory 
so im gonna stick with u torrent for for the time being 
thanks a lot

---

### Post by Kuoi on 2007-04-06
I can tell you there's nothing better than Utorrent !
Just my opinion of course , but tried most of any other linux program , and had to install wine + Utorrent .
Speed is incredible better with Utorrent , but maybe you noticed that already?
Kuoi

---

### Post by zvacet on 2007-04-07
Why don´t you make launcher in menu layer.That way you wil be safe  and you will be able to add Utorrent to panel anytime.

---

### Post by david_kt on 2007-04-07
> **zvacet said:**
> Why don´t you make launcher in menu layer.That way you wil be safe  and you will be able to add Utorrent to panel anytime.

He did have launcher in the menu. His problem is not how to launch, but utorrent just run in the background due to it did not appear in control panel. that was due to accidentally he deleted the panel, which contain notification area. And when he add new panel, he did know what to do with the new panel. Anyway he has solved it by adding notification area.

DK

---

