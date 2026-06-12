---
title: "Wine startup error"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by WardLoockx on 2006-12-19
I try to install Dev-C++ with wine but always get the following error wile starting

> ward@ward-desktop:~/Desktop/devcpp_4$ wine SETUP.EXE
wine: creating configuration directory '/home/ward/.wine'...
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  12
  Current serial number in output stream:  13
wine: wineprefixcreate failed while creating '/home/ward/.wine'.
ward@ward-desktop:~/Desktop/devcpp_4$ wineserver: could not save registry branch to /home/ward/.wine-3CssGx/system.reg : No such file or directory
wineserver: could not save registry branch to /home/ward/.wine-3CssGx/user.reg : No such file or directory

---

### Post by Afoot on 2006-12-25
You haven't created the .wine directory yet, and it doesn't seem to be able to - you don't have permissions. To fix this, you could type these commands into a terminal.

First, you should make sure you are in fact the owner of your home folder.
```
sudo chown yourUserName /home/yourUserName
```

It should work now, so try for instance to run winecfg, the Wine configuration tool:
```
winecfg
```

You should now have a working 'fake windows' folder. What you need to do when first installing wine - and this is very important - is to have winecfg autodetect your drives. Go to the "Drives" folder in winecfg. Now all you need to do is to press "Autodetect...". To be certain everything's setup correctly though, you might want to "Show Advanced", and see if the drives' "Type" are correct.

Good luck!

---

