---
title: "[SOLVED] GTK? 1 or 2? (Peazip)"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2008-02-22
I want to download the file archiver Peazip from here: [http://sourceforge.net/project/showfiles.php?group_id=178996](http://sourceforge.net/project/showfiles.php?group_id=178996)

But instead of having just 1 download for linux it has 2:
[list=1][*]PeaZip for Linux, GTK1[*]PeaZip for Linux, GTK2[/list]
So which one do I need GTK1 or GTK2 for Ubuntu 7.10 64-bit?
And what does the GTK version mean anyways?

---

### Post by glennric on 2008-02-22
You most likely want the gtk2 one.

---

### Post by PeterJS on 2008-02-22
GTK, is the GIMP (gnu image manipulation program)  tool kit, it's the library that draws all the elements of gnome apps. The gnome 2.x.x series use GTK2 (note the two in the leading element of the version numbers on both). GTK1 is old (over a decade old), but still supported because some apps haven't been ported to GTK2. Most people don't even have any GTK1 themes installed anymore.

---

### Post by BassKozz on 2008-02-22
Thanks Guys =D>

---

### Post by BassKozz on 2008-02-22
Ran into another problem:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/Screenshot-PackageInstaller-peazip.png[/IMG]

I assume this is because I am running 64-bit version of Ubuntu... does this mean I can't use PeaZip ?

---

### Post by PeterJS on 2008-02-22
Possibly, looking at the screenshot you posted it looks like you downloaded the RPM and converted it with alien. You might have better luck with the deb version:
[http://downloads.sourceforge.net/peazip/peazip_1.11.bin.LINUX.GTK2.i586-1.deb?modtime=1201507364](http://downloads.sourceforge.net/peazip/peazip_1.11.bin.LINUX.GTK2.i586-1.deb?modtime=1201507364)

If that doesn't work, you might try rolling your own from source:
[http://downloads.sourceforge.net/peazip/peazip-1.11.src.zip?modtime=1201506528](http://downloads.sourceforge.net/peazip/peazip-1.11.src.zip?modtime=1201506528)

EDIT2:
Nevermind trying to build your own, they use a really overly complex build environment that I've never heard of.That's not very friendly or open :(

---

### Post by BassKozz on 2008-02-22
> **PeterJS said:**
> Possibly, looking at the screenshot you posted it looks like you downloaded the RPM and converted it with alien. You might have better luck with the deb version:
[http://downloads.sourceforge.net/peazip/peazip_1.11.bin.LINUX.GTK2.i586-1.deb?modtime=1201507364](http://downloads.sourceforge.net/peazip/peazip_1.11.bin.LINUX.GTK2.i586-1.deb?modtime=1201507364)
Nope...Same error message as before :(
> **PeterJS said:**
> 
If that doesn't work, you might try rolling your own from source:
[http://downloads.sourceforge.net/peazip/peazip-1.11.src.zip?modtime=1201506528](http://downloads.sourceforge.net/peazip/peazip-1.11.src.zip?modtime=1201506528)
I think that might be a bit out of my league, I wouldn't know where to begin :confused:
I guess I'll just have to get by w/ "File-Roller Archive Manager" :(

---

### Post by BassKozz on 2008-02-22
Well I figured out a work-around...
I downloaded the *.tgz version and uncompressed and ran the executable directly w/out installing :)
I am probably missing out on context menu's and the like (right clicking on a file and sending to PeaZip), but for now this will do...
Time to go bother the PeaZip creators to plea for a 64-bit version ;)
Thanks for the help PeterJS :guitar:

---

### Post by Giorgio tani on 2008-02-23
Hi, the right packages for most destop users are the ones compiled for GTK2.
Presently installable packages are only for x86, but you can omit architecture check when lauching installation from your software installer, and install them anyway.
However PeaZip is natively standalone, so you don't strictly need an installation package, you can just extract and run the application (peazip_portable tar.gz packages are meant for that, but of course you can unpack any other package).
64 bit packages are planned in future, I need to build 64 bit Linux testing and development machines (and test the IDE and my code on them) but I hope it will be feasible soon.

---

### Post by BassKozz on 2008-02-24
> **Giorgio tani said:**
> Hi, the right packages for most destop users are the ones compiled for GTK2.
Presently installable packages are only for x86, but you can omit architecture check when lauching installation from your software installer, and install them anyway.
However PeaZip is natively standalone, so you don't strictly need an installation package, you can just extract and run the application (peazip_portable tar.gz packages are meant for that, but of course you can unpack any other package).
64 bit packages are planned in future, I need to build 64 bit Linux testing and development machines (and test the IDE and my code on them) but I hope it will be feasible soon.
Thanks for the update **Giorgio** I will keep my eyez open for the 64-bit version :D

---

### Post by BassKozz on 2008-02-28
I just noticed the font's in the options menu are all screwy...
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/PeazipOptions.png[/IMG]
Using PeaZip Portable v1.11 GTK2

Any idea's on how to fix this, or should I use GTK1?

---

### Post by Giorgio tani on 2008-02-28
Hi, [http://sourceforge.net/forum/message.php?msg_id=4805587](http://sourceforge.net/forum/message.php?msg_id=4805587)
The problem is that my IDE doesn't let me resize dropdown menus / comboboxes height in GTK/GTK2 so I cannot change this parameter.
Some distributions like OpenSuse have small fonts, and the object height is enough to display the font; some other, like Ubuntu, have larger fonts and the box height is not enough to display it (but the text is correctly displayed if you click on the dropdownl menu), expecially in GTK2 where some more pixels are used for object style decoration.
As soon as the IDE-level issue is resolved I'll make combobox height prarametric in order users can set and save it in program options in order to make the boxed text readable in all Linux distributions.

---

### Post by BassKozz on 2008-02-28
> **Giorgio tani said:**
> Hi, [http://sourceforge.net/forum/message.php?msg_id=4805587](http://sourceforge.net/forum/message.php?msg_id=4805587)
The problem is that my IDE doesn't let me resize dropdown menus / comboboxes height in GTK/GTK2 so I cannot change this parameter.
Some distributions like OpenSuse have small fonts, and the object height is enough to display the font; some other, like Ubuntu, have larger fonts and the box height is not enough to display it (but the text is correctly displayed if you click on the dropdownl menu), expecially in GTK2 where some more pixels are used for object style decoration.
As soon as the IDE-level issue is resolved I'll make combobox height prarametric in order users can set and save it in program options in order to make the boxed text readable in all Linux distributions.

Thanks again for the help **Giorgio**,
Sorry for the cross-posting,
Keep up the great work,:guitar:
-BassKozz

---

