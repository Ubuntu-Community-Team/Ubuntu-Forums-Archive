---
title: "can't uninstall KDE"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by maneesh77 on 2006-12-26
I installed kubuntu core on top of my gnome desktop environment, But I can't seem to uninstall it 


It says no package found, but I can change desktop environment between gnome and kde.

Also there is no shutdown button??? Where did it go??

 
maneesh@maneesh-desktop:~$ sudo aptitude remove kubuntu-core
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "kubuntu-core"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
maneesh@maneesh-desktop:~$
[COLOR="Red"]
I also tried removing kubuntu as it is[/COLOR] and kubuntu-desktop, but still nothing

maneesh@maneesh-desktop:~$ sudo aptitude remove kubuntu
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find package "kubuntu".  However, the following
packages contain "kubuntu" in their name:
  kubuntu-default-settings kubuntu-live kubuntu-grub-splashimages
  kubuntu-artwork-usplash kubuntu-desktop kubuntu-konqueror-shortcuts
  kubuntu-docs kubuntu-artwork-kbfx
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by bulldog on 2006-12-26
```
sudo aptitude remove kubuntu-desktop
```

[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

---

