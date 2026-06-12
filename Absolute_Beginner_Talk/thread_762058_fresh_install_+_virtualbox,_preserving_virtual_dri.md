---
title: "fresh install + virtualbox, preserving virtual drives"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by akiratheoni on 2008-04-21
With the release of Hardy this week I'm really excited. I'm going to be doing a fresh install on my computer :)

But I think there's a problem.

I use VirtualBox so I can use Windows for Photoshop and stuff. If I remember last time I did this, I installed VirtualBox for the second time awhile ago and the previous virtual drives from the first installation no longer worked... how do I preserve my virtual hard drives so I don't lose it when I install Hardy? I'd hate to reinstall Windows... it takes sooooo long.

Thanks.

---

### Post by boomdiddly on 2008-04-21
I managed to do this when i moved for Virtualbox OSE to the closed source one and if you give me a little while i'll write how i did it. bear in mind VB will moan but it will be fine!!

---

### Post by boomdiddly on 2008-04-22
Hopefully you will find this in the new forum structure so here goes and thank god i saved this off to a text file as by the time I had finished typing the original the forum was under maintance lol.

_**Backing up your VirtualBox virtual drive**_

[LIST=1]
[*]Browse to your home folder
[*]Press Ctrl+H
[*]Find .VirtualBox folder and double click it
[*]Double click the VDI Folder
[*]In there you will find you virtual hard drives
[*]Mines called Windows XP.vdi
[*]Copy that file somewhere safe as thats the one you need.
[/LIST]

Do what you need to with your system and reinstall virutalbox then

[LIST=1]
[*]Copy you .vdi back to the same location
[*]Start virtual box
[*]Click new
[*]Next
[*]Name it and select OS type
[*]Next
[*]Set memory
[*]Next
[*]Click existing
[*]If it doesn't list it in the window that pops up the click add and select it
[*]Select
[*]Next
[*]Finish
[/LIST]

And thats it!!

This has worked for me every time I've needed to do this but i have to put use this walk through AT YOUR OWN RISK

Good luck

Paul

---

