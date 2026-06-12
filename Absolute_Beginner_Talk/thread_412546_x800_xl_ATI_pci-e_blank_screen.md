---
title: "x800 xl ATI pci-e blank screen"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Maglio on 2007-04-18
ok, this is my first post, so please be nice :D  i am brand new to linux and ubuntu...like i've been trying to use it for a week.  i really like ubuntu because it's very easy to use, and most things work out of the box.  i am trying to run world of warcraft, however, and am having some issues.

i install wine, and that goes well.  i install and patch WoW, and that goes well.  i manually create the tweaks to the wtf.config of WoW, and the regedit in wine, and that works well.  however, when i get in the game, it's like a slide show.  so i figure it's the open source drivers for my ati card.

well, i've been through about 6 or 7 different guides on how to install the ati restricted drivers.  i've tried using the "restricted drivers' feature in feisty (i can't seem to even load up edgy), i've tried installing the ati drivers from their site, but it says something about it can't find the correct version of xorg.

pretty much every time i can actually seem to load up the ati drivers, my screen goes blank after i restart my computer.  once i was able to just restart the x server, and it reset the resolution to 1280x1024, which is fine, because that's what i was going for.  when i restarted after that though, the ubuntu loading screen with the bar loaded, and then my screen just went blank, and i couldn't even do ctrl-alt-f1.  there was no response.

i read somewhere that the drivers may have defaulted the screen to something not supported by my monitor, so i went into recovery mode, and opened the xorg.conf with the sudo vim command, and looked at the file.  everything seemed ok in the file, and nothing looked out of place.  is there anything else i can do?

as stated above, i really like ubuntu, and would like to make it my everyday system, but if i can't get the game to play, i may have to stick with windows until ubuntu can get this worked out.  sorry i can't post my xorg.conf because i'm at work.

sorry for the long post.

Maglio

---

### Post by Maglio on 2007-04-18
bumping once and once only to see if anyone has any ideas for me.

---

