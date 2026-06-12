---
title: "What Linux program will unzip Winzip files?"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by kliljedahl on 2007-01-21
I'm assuming there probably is, I just haven't found it yet.

---

### Post by hod139 on 2007-01-21
The package is called unzip, and it should be installed by default.  From a terminal you can type ```
unzip foo.zip
```
or you should be able to right click the file and extract it using a menu entry.

---

### Post by meng on 2007-01-21
Or if you're in GNOME just double-click on the file, it will open the archive manager.

---

### Post by old_geekster on 2007-01-21
The only app that I am aware of is "RAR archiver (rar).  I am very new to Linux, Ubuntu in particular, so there may be a .zip app out there.

Here is a site to use for HowTo's:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

RAR is in the "Archiver/Packages/Compression area of the site.

I simply copy and paste the commands into the "Terminal".  This is a fast way to get programs installed.

---

### Post by meng on 2007-01-21
You only need (un)rar for rar files. You shouldn't need to install anything extra to extract from zip files.

---

### Post by kliljedahl on 2007-01-21
Thanks guys, I got Photoshop installed with wine. Now all I have to do is figure out how to run it. What else dio I need to do. 
This is what I typed in teminal and the result I got:  
wine "c:\Program Files\Adobe\Photoshop 7.0\Photoshop.exe"
libGL warning: 3D driver claims to not support visual 0x4b
fixme:actctx:QueryActCtxW 80000010 0x116283c (nil) 1 0x33fdc4 8 (nil)
libGL warning: 3D driver claims to not support visual 0x4b
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  145 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  35
  Current serial number in output stream:  35

---

