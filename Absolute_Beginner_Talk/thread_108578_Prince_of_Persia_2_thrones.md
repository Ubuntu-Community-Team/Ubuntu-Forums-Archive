---
title: "Prince of Persia 2 thrones"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by projectgonewrong on 2005-12-26
On box it says for windows 2000 and Xp only and I put it in my computer with ubuntu on it and I can't get it to work (cause everyone knows game boxes lie).  I tried to click on the autorun but that doesnt work. any ideas how to get it to install.  I have heard about a windows emulator would one of those work?

---

### Post by pmjdebruijn on 2005-12-26
It's not wise to buy games and expect them to work on Ubuntu...

But with blood-sweat-and-tears it's _probably_ possible!

The emulator was called winex, and has been renamed to cedega, but it's a paid product (sort of)...

Regards,
Pascal de Bruijn

---

### Post by Estariel on 2005-12-26
Yes, it will probably work with Cedega.

On a sidenote, if the box does not say: "Linux" there won't be any linux version in there (with the remarkably exception of UT2004. There is a Linux version on the original DVD :D)

Go to [www.transgaming.com](www.transgaming.com)
Buy cedega (It's not that expensive..)
install it (it is easy, you can download a .deb file from their website. Install it using ```
sudo dpkg -i cedega-blablabla.deb
```
If you get a dependency error, issue ```
 apt-get install -f
```
It will be installed then.
You can start  it from the Applications menu. A wizard will guide through the setup (it is trivial).
After that, put the game CD in your Computer and click "install" in the cedega environment. give the installation an arbitrary titel and select the installer ("setup.exe" or something). It should work then.

Before you do any of this you might want to check in the transgaming database that cedega indeed supports the games you want to play.

---

