---
title: "Gnome Art Next Gen in Karmic?"
date: 2009-11-19
forum: Art &amp; Design
---

### Post by booksnmore4you on 2009-11-19
[Gnome Art Next Gen]("http://developer.berlios.de/projects/gnomeartng/") looks sweet.  Unfortunately, there are no packages for Karmic and the earlier ones do not work in it.  

Has anyone had success compiling G A N G from source?  If so, what did you do?  Here are the errors I get:

```

books@books-desktop:~/gnomeartng-0.7.0$ ./compile
Package glade-sharp-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glade-sharp-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glade-sharp-2.0' found
Package gnome-sharp-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gnome-sharp-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gnome-sharp-2.0' found
Package gconf-sharp-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gconf-sharp-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gconf-sharp-2.0' found
error CS0006: cannot find metadata file `System.Windows.Forms.dll'
Compilation failed: 1 error(s), 0 warnings
books@books-desktop:~/gnomeartng-0.7.0$ 


```

---

