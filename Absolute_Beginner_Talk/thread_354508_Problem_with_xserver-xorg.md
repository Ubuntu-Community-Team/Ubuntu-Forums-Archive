---
title: "Problem with xserver-xorg"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by siddharth.dawara on 2007-02-06
I'm using Xubuntu and everytime I try to install something that involves a GUI or has something to do with graphics it tries to uninstall the xserver-xorg package.

I tried it once, but when I restarted my GUI was gone.

I need RMagick quite urgently and it tries to uninstall this package. I hope there's a way around this.

Thanks in advance.

---

### Post by aberry5555 on 2007-02-06
try updating the xserver and see if that helps, if not the go to a terminal and type in "sudo apt-get install kubuntu desktop" to get the kde environment. That way you can log in to the KDE and try and rectify anything that goes wrong with that.

---

### Post by siddharth.dawara on 2007-02-08
Updating didn't help, it broke my Xubuntu :(

But, when I did re-install instead of copying the sources.list from the Ubuntu Dapper Drake guide, I enabled them through Applications>System>Software Properties.

Now, nothing tries to remove xserver-xorg :D
Cheers!

---

