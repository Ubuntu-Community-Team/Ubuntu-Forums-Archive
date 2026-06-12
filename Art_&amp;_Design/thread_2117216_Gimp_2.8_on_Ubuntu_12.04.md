---
title: "Gimp 2.8 on Ubuntu 12.04?"
date: 2013-02-17
forum: Art &amp; Design
---

### Post by nenadcvetkovic on 2013-02-17
Does anyone know if GIMP 2.8 will come to Ubuntu 12.04 repo?

---

### Post by tgalati4 on 2013-02-17
tgalati4@Mint14-Extensa ~/Desktop $ apt-cache policy gimp
gimp:
  Installed: 2.8.2-1ubuntu1.1
  Candidate: 2.8.2-1ubuntu1.1
  Version table:
 *** 2.8.2-1ubuntu1.1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.8.2-1ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages


You could try getting the deb file from the 12.10 repositories and then installing.

If it breaks, you get to keep the pieces.

[http://packages.ubuntu.com/quantal/graphics/gimp](http://packages.ubuntu.com/quantal/graphics/gimp)

You will probably have to install several library files (along side your existing library files) to make it work:

tgalati4@Mint14-Extensa ~ $ apt-cache depends gimp
gimp
  Depends: libgimp2.0
  Depends: libgimp2.0
  Depends: gimp-data
  Depends: gimp-data
  Depends: python-gtk2
  Depends: libaa1
  Depends: libbabl-0.1-0
  Depends: libbz2-1.0
  Depends: libc6
  Depends: libcairo2
  Depends: libdbus-1-3
  Depends: libdbus-glib-1-2
  Depends: libexif12
  Depends: libfontconfig1
  Depends: libfreetype6
  Depends: libgdk-pixbuf2.0-0
  Depends: libgegl-0.2-0
  Depends: libglib2.0-0
  Depends: libgs9
  Depends: libgtk2.0-0
  Depends: libgudev-1.0-0
  Depends: libjasper1
  Depends: libjpeg8
  Depends: liblcms1
  Depends: libmng1
  Depends: libpango1.0-0
  Depends: libpng12-0
  Depends: libpoppler-glib8
  Depends: librsvg2-2
  Depends: libtiff5
  Depends: libwebkitgtk-1.0-0
  Depends: libwmf0.2-7
  Depends: libx11-6
  Depends: libxcursor1
  Depends: libxext6
  Depends: libxfixes3
  Depends: libxmu6
  Depends: libxpm4
  Depends: zlib1g
  Depends: python
  Depends: python2.7
 |Suggests: gimp-help-en
  Suggests: <gimp-help>
    gimp-help-de
    gimp-help-en
    gimp-help-es
    gimp-help-fr
    gimp-help-it
    gimp-help-ko
    gimp-help-nl
    gimp-help-nn
    gimp-help-pl
    gimp-help-ru
    gimp-help-sv
  Suggests: gimp-data-extras
  Suggests: gvfs-backends
    gvfs-backends:i386
  Suggests: libasound2
    liboss4-salsa-asound2
  Recommends: ghostscript
    ghostscript:i386
  Breaks: gimp-plugin-registry
  Breaks: gimp-plugin-registry:i386
  Replaces: gimp-plugin-registry
  Replaces: gimp-plugin-registry:i386
  Conflicts: gimp:i386

If that hasn't completely balled up your system, then here are some more suggestions using the apt-src command (you have to install apt-src first):

[http://ubuntuforums.org/showthread.php?t=1291814](http://ubuntuforums.org/showthread.php?t=1291814)

It's an old thread, but the information is applicable.

The agony units on this is probably on par with just installing 12.10 on the machine.

I'm not sure what the protocol is for proposing and promoting a package for backport, but that would be another avenue.

---

### Post by ibjsb4 on 2013-02-18
> **nenadcvetkovic said:**
> Does anyone know if GIMP 2.8 will come to Ubuntu 12.04 repo?

No, not likely.

You can install 2.8 by using the PPA.

```
sudo apt-add-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update
sudo apt-get install gimp
```

---

### Post by Dry Lips on 2013-02-18
> **ibjsb4 said:**
> No, not likely.

You can install 2.8 by using the PPA.

```
sudo apt-add-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update
sudo apt-get install gimp
```

**+1!** By far the easiest solution!

---

### Post by nenadcvetkovic on 2013-02-27
Thank you all for responses, I guess I'll have to add that ppa in the end :)

---

### Post by ibjsb4 on 2013-02-27
> **nenadcvetkovic said:**
> Thank you all for responses, I guess I'll have to add that ppa in the end :)

Be sure to remove 2.6 completely before installing 2.8 or you will end up with 2.6 again.

```
sudo apt-get remove --purge gimp
```

And then open up gksu nautilus and go to "filesystem" and do a search on the word "gimp".

```
gksudo nautilus
```

And remove any gimp leftovers.  Your now ready to install 2.8 :)

---

