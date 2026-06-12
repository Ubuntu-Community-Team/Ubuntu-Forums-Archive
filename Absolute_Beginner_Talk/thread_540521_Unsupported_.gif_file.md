---
title: "Unsupported .gif file"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Xummoner on 2007-09-01
I have a bunch of .gif files that Ubuntu won't open and I really don't know why. 
Let me explain the whole thing: 
There's a type of file with .ezx extension which is just a compressed file that contains a bunch of icons used on my cellphone (based on Linux btw), there's both a Perl script and a windows program that uncompress that file and as a result I get a folder with all the images in .gif format, but with names such as these: "carrier_ani.g.g.gif" and "chkbx_bg_hs.k.gif". The thing is that Ubuntu recognizes the ones ending in .g.gif but not the ones ending in .k.gif and I have no idea why this could be, since window$ can open both types of files fine. 
I even emulated the windows program with WINE and it worked, but again .k.gif files could not be opened with any program. 

I'll try to attach a couple of those 2 kinds of files in case someone wants to take a look at then and find the problem

I could also attach the Perl script and/or .ezx file and see if someone can tell me if there's something wrong with the script or with Ubuntu not reading those files properly.

Thanks in advance.

Note: the attached file contains the Perl script, 3 examples of images and a compressed .ezx file which is uncompressed by running the Perl script in the same folder where the .ezx file is contained.

---

### Post by deadgobby on 2007-09-01
The G stands for Gnome and the K stands for KDE. Ubutu is Gnome based and KUbuntu KDE based. 
 You may want to try to see if Gimp will open up the K ones. Or see if you lie and rename the K ones to G. It rarely works that way. 
Gobby

---

### Post by Xummoner on 2007-09-01
I don't think those file names are related to KDE or Gnome, since they can be opened in windows perfectly so that K and G thing is just a coincidence. GIMP only opens the G ones, and if I change the K for a G in the filename it still won't open them. Even Nautilus can't recognize the files since it doesn't show the thumbnail.

When I try to open any of them on GIMP it gives me this error:

This is not a GIF file
Opening 'chkbx_bg_hs.k.gif' failed: Plug-In could not open image

---

