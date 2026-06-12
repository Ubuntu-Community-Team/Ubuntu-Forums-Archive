---
title: "problem with opening a tif file"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by diamantis13 on 2007-10-15
Hi, 

I am trying to open a .tif file, but no program can read it. I always get a message about not configured compression.
Is there any program that supports _all_ tiff files? Could I somehow check the file to find its compression method and search for the appropriate program?

Thank you very much!

---

### Post by Biochem on 2007-10-15
There is ImageJ. it's a java program mainly oriented toward scientific image analysis. With the plugins it's on of the most powerful image software out here 

[http://rsb.info.nih.gov/ij/](http://rsb.info.nih.gov/ij/)

---

### Post by diamantis13 on 2007-10-15
I just installed ImageJ, but I get the error:** "ImageJ cannot open TIFF files compressed in this fashion (6)**". I looked around their website and documentation but cannot find any detailed explanation for the error message.
I suppose that ImageJ does not support the specific compression :(. But it seems an interesting program!

---

### Post by Biochem on 2007-10-16
Maybe you need the Loci plugin to open your files. 
[http://www.loci.wisc.edu/ome/formats.html](http://www.loci.wisc.edu/ome/formats.html)
All you need is to put the *.jar file in you plugins folder and reopen ImageJ. Then plugins>LOCI>bio-format importer

I hope it works for you. If not, they say they are looking for tif with unusual compression. If you have the time, send them one of your file to help them improve their software

---

