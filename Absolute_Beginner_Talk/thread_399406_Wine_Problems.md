---
title: "Wine Problems"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by sephy on 2007-04-02
I am trying to install wine on ubuntu edgy I386 but when I open the .Deb file it says Error: Dependency not satisfyable : libartsc0. does anyone know what that means? I cannot install off the internet as my wireless network card is not recognised. I need wine to install my windows driver. it is a Bt voyager 1040 PCI network card

---

### Post by Kobalt on 2007-04-02
I think the BT Voyager 1040 PCI card is based on a Broadcom 4306 chipset, so you do need windows drivers to get it working but you won't use them through Wine, that will be Ndiswrapper.
Here is a way to install your card : [http://www.ubuntuforums.org/showthread.php?t=201902](http://www.ubuntuforums.org/showthread.php?t=201902)
You will need to install packages though : if you don't have an internet connection at all with Ubuntu you can connect from another computer or from Windows to [http://packages.ubuntu.com](http://packages.ubuntu.com) and search for the packages you need to install, download and double-click on them to install them. 

PS: the problem you have with that wine packages is that it requires other packages to be installed to have wine installed and working properly : it's called dependencies.

---

