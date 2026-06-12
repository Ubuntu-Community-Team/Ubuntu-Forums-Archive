---
title: "Foobar.exe works but where are the settings stored?"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by CK05 on 2005-11-28
I've managed to get foobar2000.exe to work properly through wine but where are the customization settings installed? On Windows they are in the Application Data folder. 

Thanks in advance for help.

---

### Post by gord on 2005-11-28
you should find a mockup of a windows c-drive in '/home/<yourusername>/.wine/c_drive/'

try checking in there

---

### Post by ltmon on 2005-11-28
Usually wine just has a "C" drive set at:

~/.wine/drive_c/

Anything under there should mirror a normal windows C:\.

Type:

> winecfg

To see all drives available to wine, and what wine uses them for.

L.

---

