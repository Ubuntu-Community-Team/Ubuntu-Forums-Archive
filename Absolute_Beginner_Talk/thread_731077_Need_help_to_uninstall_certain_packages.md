---
title: "Need help to uninstall certain packages"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by hikujk123 on 2008-03-21
I am new to ubuntu and linux.  I just switched from ubuntu to xubuntu.  I wanted to delete a shortcut from my applications menu, so I installed alacarte (I didn't realize it was a gnome application).  I typed sudo apt-get install alacarte.  Well, I got all these extra gnome packages with it.   Then, I realized that it must be a gnome application, so I type sudo apt-get remove alacarte.  Of course, I did not have the insight to realize that all the other packages are still there.  I will post the output and would appreciate it if someone told me how to uninstall all of the packages without having to uninstall each one individually.
desktop:~$ sudo apt-get remove alacarte
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libaiksaurus-1.2-data lib32ncurses5 link-grammar-dictionaries-en
  gnome-panel-data libots0 ia32-libs libedataserver1.2-9
  libgnome-window-settings1 libecal1.2-7 gnome-menus liblpint-bonobo0
  libc6-i386 lib32gcc1 python-gmenu lib32asound2 liblink-grammar4 gnome-about
  libt1-5 libedataserverui1.2-8 binfmt-support libgdome2-0 libwpd-stream8c2a
  libaiksaurusgtk-1.2-0c2a libgsf-gnome-1-114 libgtkmathview0c2a
  gnome-desktop-data libcamel1.2-10 gnome-control-center lib32z1
  libaiksaurus-1.2-0c2a libqt3-mt lib32stdc++6 gnome-panel capplets-data
  libaudio2 libebook1.2-9 libgdome2-cpp-smart0c2a
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  alacarte
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 1180kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 89480 files and directories currently installed.)
Removing alacarte ...

---

### Post by Paqman on 2008-03-21
Actually, the answer is hiding in the error script you quoted: "Use 'apt-get autoremove' to remove them."

---

### Post by forestpixie on 2008-03-21
> Use 'apt-get autoremove' to remove them. - it tells you how :)

```
sudo apt-get autoremove
```

---

### Post by hikujk123 on 2008-03-21
Thanks.  I read that but forgot to put sudo in front of it.  Oh well, I'm learning as I go.

---

### Post by hikujk123 on 2008-03-21
How do you delete icons from the application menu in xubuntu?

---

### Post by bumanie on 2008-03-21
Have you rebooted since removing the packages you didn't want? Sometimes menus won't disappear until you have rebooted or at least logged out and back in. Try that.

---

### Post by hikujk123 on 2008-03-21
Those aren't the shortcuts I want to get rid of.  The reason I "installed" alacarte is because I wanted to get rid of a trillian icon that didn't go away once I uninstalled it under wine and then uninstalled wine itself.

---

