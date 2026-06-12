---
title: "Major graphics corruption on Wallstreet G3 Powerbook"
date: 2005-03-31
forum: Apple PPC Users
---

### Post by Cask on 2005-03-31
The first installation menus were fine on my Mac 233 G3 Powerbook but the problems began when I tried to bring up the console. Using BootX, with "No video driver" ticked I could see the menus fine, but the console would be just a black screen with a penguin in the top left but no way of getting out of it. So I tried it with "No video driver" unticked and that just yields a horribly corrupted screen where you can just about make out the menus, and the console prompt but it's impossible to do anything serious in it.

The monitor output works great but that kind of defeats the purpose of having a laptop and as I can't find anyone else with this problem I guess  I need to try another distro. I tried the various BootX kernel parameters in wiki and they had no effect at all.

---

### Post by Cask on 2005-04-01
Hurrah perseverance paid off. I added this vmode argument:

video=atyfb:vmode:12,cmode:0

and it works perfectly with the ATI driver.

---

