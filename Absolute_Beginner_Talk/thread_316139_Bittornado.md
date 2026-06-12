---
title: "Bittornado"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by 0m3n on 2006-12-10
im not sure why this is happening since i didnt install anything or update anything... but heres what im getting when i open up Bittornado 

> BitTorrent T-0.3.15 (BitTornado)
OS: linux2
Python version: 2.4.4c1 (#2, Oct 11 2006, 21:51:02) 
[GCC 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)]
wxWindows version: 2.6.3.2

Traceback (most recent call last):
  File "/usr/bin/btdownloadgui", line 2327, in _next
    savedas = dow.saveAs(choosefile, d.newpath)
  File "/var/lib/python-support/python2.4/BitTornado/download_bt1.py", line 429, in saveAs
    n = path.join(n, i)
  File "posixpath.py", line 65, in join
    path += '/' + b
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe2 in position 14: ordinal not in range(128)

anyone know what that means and how can i fix it? thanks in advance

---

### Post by dolphinsonar on 2007-01-01
Sometimes just ignoring the problems is easier... Try Ktorrent instead and uninstall bittornado.

---

### Post by shutterbc on 2007-01-01
It really looks like you have a corrupt download_bt1.py file.  Either that or you have bad characters in your preferences, and the gui isn't able to correctly handle the exception.

You might have luck if you remove and reinstall the package.

---

