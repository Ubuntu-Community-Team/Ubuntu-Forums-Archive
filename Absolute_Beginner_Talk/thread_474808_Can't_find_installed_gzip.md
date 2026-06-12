---
title: "Can't find installed gzip?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-06-15
I am trying to use gzip but cannot find it! When I search I get the following :
benbow@benbow-desktop:~$ aptitude show gzip
Package: gzip
Essential: yes
State: installed
Automatically installed: no
Version: 1.3.9-2
Priority: required
Section: base
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 246k
Depends: debianutils (>= 1.6)
PreDepends: libc6 (>= 2.5-0ubuntu1)
Suggests: less
Description: The GNU compression utility
 This is the standard GNU file compression utility, which is also the default
 compression tool for Debian.  It typically operates on files with names ending
 in '.gz'. 
 
 This package can also decompress '.Z' files created with 'compress'.

But it doesn't appear anywhere?

---

### Post by Phixion on 2007-06-15
Try a:

sudo updatedb
sudo locate gzip

---

### Post by Benbow on 2007-06-15
Hi - What does this mean?
benbow@benbow-desktop:~$ sudo locate gzip
/var/cache/apt/archives/gzip_1.3.9-2_i386.deb
/var/lib/dpkg/info/gzip.list
/var/lib/dpkg/info/gzip.md5sums
/var/lib/dpkg/info/gzip.postinst
/var/lib/dpkg/info/gzip.preinst
/var/lib/dpkg/info/gzip.prerm
/bin/gzip
/usr/include/freetype2/freetype/ftgzip.h
/usr/include/libgsf-1/gsf/gsf-input-gzip.h
/usr/include/libgsf-1/gsf/gsf-output-gzip.h
/usr/lib/apt/methods/gzip
/usr/lib/cups/filter/gziptoany
/usr/lib/gnome-vfs-2.0/modules/libgzip.so
/usr/lib/kde3/kgzipfilter.la
/usr/lib/kde3/kgzipfilter.so
/usr/lib/klibc/bin/gzip
/usr/lib/python2.4/gzip.pyc
/usr/lib/python2.4/gzip.py
/usr/lib/python2.5/gzip.py
/usr/lib/python2.5/gzip.pyc
/usr/share/doc/diveintopython/html/http_web_services/gzip_compression.html
/usr/share/doc/gzip
/usr/share/doc/gzip/README-alpha
/usr/share/doc/gzip/README.gz
/usr/share/doc/gzip/TODO
/usr/share/doc/gzip/changelog.Debian.gz
/usr/share/doc/gzip/copyright
/usr/share/doc/kde/HTML/en/kioslave/gzip.docbook
/usr/share/doc/libfreetype6/reference/ft2-gzip.html
/usr/share/doc/zlib1g-dev/examples/minigzip.c.gz
/usr/share/icons/Amaranth/scalable/mimetypes/gnome-mime-application-x-gzip.svg
/usr/share/icons/BlankOn/scalable/mimetypes/gnome-mime-application-x-gzip.svg
/usr/share/icons/Gorilla/scalable/mimetypes/gnome-mime-application-x-gzip.svg
/usr/share/icons/Lush/scalable/mimetypes/gnome-mime-application-x-gzip.svg
/usr/share/icons/Nuovo/scalable/mimetypes/packages/gnome-mime-application-x-gzip.svg
/usr/share/icons/Nuvola/scalable/mimetypes/gnome-mime-application-x-gzip.svg
/usr/share/icons/Rodent/48x48/mimetypes/application-x-gzip.png
/usr/share/icons/Rodent/48x48/mimetypes/gnome-mime-application-x-gzip.png
/usr/share/icons/Rodent/48x48/mimetypes/mime-application:x-gzip.png
/usr/share/icons/Rodent/scalable/mimetypes/application-x-gzip.svg
/usr/share/icons/Rodent/scalable/mimetypes/gnome-mime-application-x-gzip.svg
/usr/share/icons/Rodent/scalable/mimetypes/mime-application:x-gzip.svg
/usr/share/icons/Suede/scalable/mimetypes/gnome-mime-application-x-gzip.svg
/usr/share/icons/Tango/16x16/mimetypes/gnome-mime-application-x-gzip.png
/usr/share/icons/Tango/22x22/mimetypes/gnome-mime-application-x-gzip.png
/usr/share/icons/Tango/24x24/mimetypes/gnome-mime-application-x-gzip.png
/usr/share/icons/Tango/32x32/mimetypes/gnome-mime-application-x-gzip.png
/usr/share/icons/Tango/scalable/mimetypes/gnome-mime-application-x-gzip.svg
/usr/share/icons/Wasp/scalable/mimetypes/gnome-mime-application-x-gzip.svg
/usr/share/icons/dlg-neu/scalable/mimetypes/gnome-mime-application-x-gzip.svg
/usr/share/icons/gartoon/scalable/mimetypes/gnome-mime-application-x-gzip.svg
/usr/share/icons/glass-icons/scalable/mimetypes/gnome-mime-application-x-gzip.svg
/usr/share/icons/gnome/16x16/mimetypes/gnome-mime-application-x-gzip.png
/usr/share/icons/gnome/22x22/mimetypes/gnome-mime-application-x-gzip.png
/usr/share/icons/gnome/24x24/mimetypes/gnome-mime-application-x-gzip.png
/usr/share/icons/gnome/32x32/mimetypes/gnome-mime-application-x-gzip.png
/usr/share/icons/gnome/scalable/mimetypes/gnome-mime-application-x-gzip.svg
/usr/share/icons/gperfection2/16x16/mimetypes/gnome-mime-application-x-gzip.png
/usr/share/icons/gperfection2/24x24/mimetypes/gnome-mime-application-x-gzip.png
/usr/share/icons/gperfection2/36x36/mimetypes/gnome-mime-application-x-gzip.png
/usr/share/icons/gperfection2/48x48/mimetypes/gnome-mime-application-x-gzip.png
/usr/share/icons/nuoveXT-1.6/128x128/mimetypes/gnome-mime-application-x-gzip.png
/usr/share/icons/nuoveXT-1.6/12x12/mimetypes/gnome-mime-application-x-gzip.png
/usr/share/icons/nuoveXT-1.6/16x16/mimetypes/gnome-mime-application-x-gzip.png
/usr/share/icons/nuoveXT-1.6/24x24/mimetypes/gnome-mime-application-x-gzip.png
/usr/share/icons/nuoveXT-1.6/36x36/mimetypes/gnome-mime-application-x-gzip.png
/usr/share/icons/nuoveXT-1.6/48x48/mimetypes/gnome-mime-application-x-gzip.png
/usr/share/icons/poloar2/128x128/extra/gnome-mime-application-x-gzip.png
/usr/share/icons/poloar2/128x128/mimetypes/gnome-mime-application-x-gzip.png
/usr/share/icons/UbuntuStudio/scalable/mimetypes/gnome-mime-application-x-gzip.svg
/usr/share/info/gzip.info.gz
/usr/share/lintian/overrides/gzip
/usr/share/man/man1/gzip.1.gz
/usr/share/mime/application/x-gzip.xml
/usr/share/mimelnk/application/x-gzip.desktop
/usr/share/services/gzip.protocol
/usr/share/services/kgzipfilter.desktop

Is it available? thanks guys.

---

### Post by Bachstelze on 2007-06-15
Gzip is installed, it just does not have a graphical frontend. You can use it to decompress gzipped files with

```
gunzip /path/to/file.gz
```

---

### Post by Benbow on 2007-06-15
Thanks for the answers. I have had Ubuntu for three weeks now and am happy but still struggling.
Is there a "zip" program with a graphical front end like say Win Zip?

---

### Post by Bachstelze on 2007-06-15
There is a graphical Archive Manager but I don't know if it's able to create archives as WinZip is. I always just use the command-line :

```
tar czvf archive.tgz directory/
```

will create a gzipped tarball of that directory. There's really no need for a graphical thingie...

---

### Post by Benbow on 2007-06-15
Hymn to life, I thank you>

---

### Post by shelzmike on 2007-06-15
> **Benbow said:**
> Thanks for the answers. I have had Ubuntu for three weeks now and am happy but still struggling.
Is there a "zip" program with a graphical front end like say Win Zip?

There are free version of both WinZip and WinRAR for Linux as far as I know; however, they are both command only. It would be nice, but no go as of yet. In this case, it makes just as much sense to use the Archiver that comes with Ubuntu. It has a pretty decent GUI that acts as a WinRAR and WinZip program does. And I do think that it does allow you create archives in .tar.gz, .tar.bz2, .tar, .zip, .ar, .ear, .jar, and .war. The only thing that it is lacking is the ability to see the files inside any archives before extracting them (plus individual extraction). Hope this helps!

---

