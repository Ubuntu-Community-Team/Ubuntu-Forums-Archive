---
title: "A few VirtualBox queries"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by tprzepiorka on 2007-10-18
Hello,
So I finally got VirtualBox installed and up and running :D
I'm running XP with it. I want to be able to play some games and run photoshop.
I am wondering if it is possible at all to do any of the following things:

Transfer files between XP(running in VirtualBox) and Ubuntu. 
Should I download and install graphic card drivers in XP?
If I want to play games on XP (HL:2, CSS, and other FPS) can I have some recommendations on how much RAM I should allocate and video memory?
(^I know it depends on the game, but I want to give enough so I can switch back and keep Ubuntu usable. FYI I have 2GB of RAM and NVIDIA 7600GS. Right now it has 192MB RAM and 8MB Video memory allocated to my XP install)

Thanks a lot, I'm kinda new to the whole virtual OS thing. Seems very cool though:)

Oh, one more thing, may sound stupid. If I allocate, let's say, 1GB of RAM to the VBox when I am not running virtual box will that GB still be available to my Ubuntu install?

Thanks once more!

---

### Post by sintoris on 2007-10-18
To transfer files between winxp and ubuntu you can use windows file sharing. Check out [ubuntuguide.org]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_folders_the_easy_way") for detailed instructions.

C.

---

### Post by Beggar on 2007-10-18
All valve games play fine in WINE, I do it all the time, just search the forums for a guide, or install wine, then steam, then download the tahoma.ttf font, and copy it to drive_c/windows/fonts. there are guides all over the web to do it. Its generally a bad idea to run them in a vm because you lose things like graphics acceleration, etc.

---

### Post by steve.horsley on 2007-10-18
Do not try installing graphics drivers in XP inside VirtualBox. VirtualBox emulates a graphics card that XP already knows how to drive so the drivers for your actual card will be useless. But VirtualBox do provide drivers for the emulated video card to give extra features, and it is well worth installing those. There is an option somewhere on the pull-down menus at the top of the VM which makes XP think an installer CD rom has been inserted.

---

### Post by kellemes on 2007-10-18
> **steve.horsley said:**
> There is an option somewhere on the pull-down menus at the top of the VM which makes XP think an installer CD rom has been inserted.

guest additions

---

### Post by livingtarget on 2007-10-18
It is worth noting that i've never been able to run a lot of 3d games in VirtualBox, I think the display driver from them will not allow it to run direct3d programs. If you have a look in dxdiag (start->run->type "dxdiag) it will probably show you that it cant do 3d. 

HL2/CS:S will likely run with Wine (install wine in ubuntu through synaptic or the add/remove programs), you may need to read up on the Wine Application database if there are any tweaks that need to apply.

Counter Strike Source on the Wine Application Database: 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731)

I run photoshop, flash, vb and a few other things in Virtualbox which works great. I use Wine more for games.

---

### Post by Frak on 2007-10-18
For games I would use Wine or Cedega, there aren't any drivers yet for virtual sessions that allow games to be run.

Also, when not using Vbox, Ubuntu will cache the RAM for predictible popularity, (faster opening of programs) so even though you may have NOTHING running, Ubuntu may use 99% of your RAM.

It uses that RAM because unused RAM is wasted RAM. It doesn't impact performance in any negative way.

---

### Post by compiledkernel on 2007-10-18
Should have all the essential Virtualbox stuff, it it doesnt let us know.[VirtualBox howto and info]("http://doc.gwos.org/doku.php/doc:office:virtualbox")

---

