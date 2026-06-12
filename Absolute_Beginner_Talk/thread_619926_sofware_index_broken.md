---
title: "sofware index broken"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by xord on 2007-11-22
i was trying to update but then and error message popped up and saying there's broken package.
i tried with sudo apt-get -f install but this come out

0 upgraded, 0 newly installed, 264 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 921MB disk space will be freed.

that practically remove all the things in this pc, its better to reinstall ubuntu, any other suggestion?

---

### Post by jfinkels on 2007-11-22
What is the exact error message you got before you tried "sudo apt-get -f install"? Do you have the package "ubuntu-desktop" selected and installed? If not, it could lead to this problem...but we need to see the exact error message first!

---

### Post by fastTalker on 2007-11-22
have you added a new repo?  if you are trying to add software from a repo that isn't intended for your distribution lots of conflicts can occur causing apt to want to uninstall a lot of packages.

---

### Post by xord on 2007-11-22
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

that's the error message


i tried to install mac menu from [https://wiki.ubuntu.com/global_menu](https://wiki.ubuntu.com/global_menu) and i used the zero method, downloaded all the debs from the link and run it

ok, just found out what is broken, its my libgtk2.0, but in order to fix it, i have to remove almost all my program, which is better if i just reinstall ubuntu, but the problem is, i really don't to do that, is there any other way?

---

### Post by jfinkels on 2007-11-22
You can try downloading the package from packages.ubuntu.com and reinstalling it using ```
sudo dpkg -i  *packagename.deb*
```I don't know if that will work...

---

### Post by xord on 2007-11-23
hey, thanks, it's working now. thanks a lot buddy!

---

