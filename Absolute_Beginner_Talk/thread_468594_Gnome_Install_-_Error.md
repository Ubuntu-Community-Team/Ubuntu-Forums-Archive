---
title: "Gnome Install - Error?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-06-09
```

Errors were encountered while processing:
 gnome-app-install
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up gnome-app-install (0.2.21) ...
Caching application data...
Got non-package menu entry kiso.desktop
Got non-package menu entry xchm.desktop
Got non-package menu entry k3dsurf.desktop
Got non-package menu entry grdesktop.desktop
Got non-package menu entry tsclient.desktop
Traceback (most recent call last):
  File "/usr/sbin/update-app-install", line 69, in ?
    generate_cache()
  File "/usr/sbin/update-app-install", line 49, in generate_cache
    menu.createMenuCache(options.cache_dir)
  File "/usr/lib/python2.4/site-packages/AppInstall/CoreMenu.py", line 29, in createMenuCache
    self._populateFromEntry(menu)
  File "/usr/lib/python2.4/site-packages/AppInstall/CoreMenu.py", line 43, in _populateFromEntry
    self._populateFromEntry(entry, item,  progress=progress)
  File "/usr/lib/python2.4/site-packages/AppInstall/CoreMenu.py", line 94, in _populateFromEntry
    item.mime = entry.DesktopEntry.getMimeType()
  File "/var/lib/python-support/python2.4/xdg/DesktopEntry.py", line 74, in getMimeType
    return self.get('MimeType', list=True, type="regex")
  File "/var/lib/python-support/python2.4/xdg/IniFile.py", line 129, in get
    value = re.compile(value)
  File "/usr/lib/python2.4/sre.py", line 180, in compile
    return _compile(pattern, flags)
  File "/usr/lib/python2.4/sre.py", line 227, in _compile
    raise error, v # invalid expression
sre_constants.error: multiple repeat
dpkg: error processing gnome-app-install (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gnome-app-install

```

Im installing GNOME on a Kubuntu 6.10.

I was wondering, should I be worried about this error?

---

### Post by LollYouSuckZor on 2007-06-09
```

nic@nic-desktop:~$ sudo apt-get install xserver-xgl
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libemeraldengine0 beryl-plugins-data libberyldecoration0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libglitz-glx1 libglitz1
The following NEW packages will be installed:
  libglitz-glx1 libglitz1 xserver-xgl
0 upgraded, 3 newly installed, 0 to remove and 724 not upgraded.
1 not fully installed or removed.
Need to get 1843kB of archives.
After unpacking 4825kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com edgy/main libglitz1 0.5.6-1 [76.6kB]
Get:2 http://us.archive.ubuntu.com edgy/main libglitz-glx1 0.5.6-1 [29.6kB]
Get:3 http://us.archive.ubuntu.com feisty/universe xserver-xgl 7.2.0.git.20070224-0ubuntu3 [1737kB]
Fetched 1843kB in 8s (228kB/s)                                                 
Selecting previously deselected package libglitz1.
(Reading database ... 113924 files and directories currently installed.)
Unpacking libglitz1 (from .../libglitz1_0.5.6-1_i386.deb) ...
Selecting previously deselected package libglitz-glx1.
Unpacking libglitz-glx1 (from .../libglitz-glx1_0.5.6-1_i386.deb) ...
Selecting previously deselected package xserver-xgl.
Unpacking xserver-xgl (from .../xserver-xgl_7.2.0.git.20070224-0ubuntu3_i386.deb) ...
Setting up gnome-app-install (0.2.21) ...
Caching application data...
Got non-package menu entry kiso.desktop
Got non-package menu entry xchm.desktop
Got non-package menu entry k3dsurf.desktop
Got non-package menu entry grdesktop.desktop
Got non-package menu entry tsclient.desktop
Traceback (most recent call last):
  File "/usr/sbin/update-app-install", line 69, in ?
    generate_cache()
  File "/usr/sbin/update-app-install", line 49, in generate_cache
    menu.createMenuCache(options.cache_dir)
  File "/usr/lib/python2.4/site-packages/AppInstall/CoreMenu.py", line 29, in createMenuCache
    self._populateFromEntry(menu)
  File "/usr/lib/python2.4/site-packages/AppInstall/CoreMenu.py", line 43, in _populateFromEntry
    self._populateFromEntry(entry, item,  progress=progress)
  File "/usr/lib/python2.4/site-packages/AppInstall/CoreMenu.py", line 94, in _populateFromEntry
    item.mime = entry.DesktopEntry.getMimeType()
  File "/var/lib/python-support/python2.4/xdg/DesktopEntry.py", line 74, in getMimeType
    return self.get('MimeType', list=True, type="regex")
  File "/var/lib/python-support/python2.4/xdg/IniFile.py", line 129, in get
    value = re.compile(value)
  File "/usr/lib/python2.4/sre.py", line 180, in compile
    return _compile(pattern, flags)
  File "/usr/lib/python2.4/sre.py", line 227, in _compile
    raise error, v # invalid expression
sre_constants.error: multiple repeat
dpkg: error processing gnome-app-install (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libglitz1 (0.5.6-1) ...

Setting up libglitz-glx1 (0.5.6-1) ...

Setting up xserver-xgl (7.2.0.git.20070224-0ubuntu3) ...
Errors were encountered while processing:
 gnome-app-install
E: Sub-process /usr/bin/dpkg returned an error code (1)
nic@nic-desktop:~$ 

```
while trying to install beryl.

---

