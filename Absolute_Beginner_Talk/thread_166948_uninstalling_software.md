---
title: "uninstalling software"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by rameez on 2006-04-27
just wondering when I install software mannually by compiling them or use an rpm how do I uninstall them later. I have two questions:
1. Where does ubuntu install softwares like windows by default installs in Program Files. 
2. How can I check what softwares have been installed on my system (i.e installed manually without using synaptic).

Thanks.

---

### Post by gingermark on 2006-04-27
If you install from a .deb (whether native or converted from an rpm) you can remove it with synaptic.

If you regularly compile from source consider installing checkinstall (sudo apt-get install checkinstall). Then, instead of typing "sudo make install" when compiling a program you type "sudo checkinstall -D" and a .deb file will be created that can easily be removed.

Most software goes into /usr/bin I think. As far as checking for software that you've compiled (without using checkinstall), I thnk you'd have to manually look for it.

Anything else though will be marked as installed in Synaptic.

---

### Post by Jagot on 2006-04-27
Here's a bit more about checkinstall that gingermark was talking about:

[https://wiki.ubuntu.com/CheckInstall](https://wiki.ubuntu.com/CheckInstall)

---

