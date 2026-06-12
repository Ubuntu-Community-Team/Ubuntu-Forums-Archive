---
title: "[SOLVED] Want to keep Avast4workstation"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by iClouseau88 on 2007-10-30
Hi,

I just successfully downloaded and installed Avast4workstation.  Synaptic Package Manager shows that this program is indeed installed.  I now use the GUI (Fille > Accessories) on the desktop to run it, i.e. scanning.
However, when I type sudo aptitude update, the terminal shows that avast4workstation is an unused package and therefor will be removed.  How do I prevent the removal of this software package?

Thanks in advance for your help.

:confused:

---

### Post by JBAlaska on 2007-10-31
How did you install avast? did you use the deb package from the avast for linux web site?

I have avast 4 installed (I don't know why..for fun I guess lol) and aptitude does not try to uninstall it.

---

### Post by iClouseau88 on 2007-10-31
Hi,

Thank you for replying.  I followed the HOWTO in [www.ubuntugeek.com](www.ubuntugeek.com).  I did use the deb package from the avast web site.  Once I download the package, the computer asks me if I want to install so I said yes.  I did not use wget [http://files.avast.com](http://files.avast.com) etc. to download it.
I then used the following to set up the application menu:
 Code:
cd /usr/lib/avast4workstation/share/avast/desktop
sudo ./install-desktop-entries.sh install

---

### Post by iClouseau88 on 2007-10-31
Hello all,

I solved the problem by removing the package, sudo aptitude autoclean, redownloading and reinstalling it, and rebooting the machine.

---

