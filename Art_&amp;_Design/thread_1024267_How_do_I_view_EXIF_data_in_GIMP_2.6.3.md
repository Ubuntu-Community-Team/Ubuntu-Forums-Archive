---
title: "How do I view EXIF data in GIMP 2.6.3?"
date: 2008-12-28
forum: Art &amp; Design
---

### Post by bowens44 on 2008-12-28
I know that there was a plug-in for gimnp 2.4 that allowed you to view exif data. Is it possible to view exif in gimp 2.6 ?

---

### Post by Echow on 2009-01-04
found it! 
[http://registry.gimp.org/node/8839](http://registry.gimp.org/node/8839)
hope this helps you out, view exif should be under file menu

---

### Post by bowens44 on 2009-01-04
> **Echow said:**
> found it! 
[http://registry.gimp.org/node/8839](http://registry.gimp.org/node/8839)
hope this helps you out, view exif should be under file menu

Thanks for your response.

Yes, I also found this but I have been unable to compile it. It fails on configure. It appears to be for gimp 2.4 not 2.6.

I can usually resolve these issues but haven't had any luck with this one.

I get this when doing ./configure:

checking for gimp-2.0 gimpui-2.0 libexif >= 0.5.9... Package gimp-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gimp-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gimp-2.0' found Package gimpui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gimpui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gimpui-2.0' found
configure: error: Library requirements (gimp-2.0 gimpui-2.0 libexif >= 0.5.9) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

---

