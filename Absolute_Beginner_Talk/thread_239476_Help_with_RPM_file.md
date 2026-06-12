---
title: "Help with RPM file"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by Psycosis on 2006-08-19
Hi. I'm completely new to any kind of unix OS, I just installed ubuntu a few hours ago. I needed a video player that could play WMV's so I downloaded Xine from it's website. The file is in RPM format and I was wondering how I go about using this RPM file to install the program.
Many thanks,
Peter.

---

### Post by ComplexNumber on 2006-08-19
> **Psycosis said:**
> Hi. I'm completely new to any kind of unix OS, I just installed ubuntu a few hours ago. I needed a video player that could play WMV's so I downloaded Xine from it's website. The file is in RPM format and I was wondering how I go about using this RPM file to install the program.
Many thanks,
Peter.
you can't install it directly on ubuntu. ubuntu is based on the deb package format, so you will have to convert it.  you can convert it by using a small applications called alien. i'm not too sure of the exact way to convert it at the moment because i haven't got it on my system. maybe someone else can. install it, then someone else can take it from there.


btw can't you find a deb equivelent in the repositories?

---

### Post by Klaidas on 2006-08-19
Ubuntu doesn't use RPM, it uses apt-get or .deb :) For more information, see [http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)

As for playing those formats, you need to install codecs. Please see my signature for "restricted formats"

Hope this helps :)

---

### Post by badactress on 2006-08-19
Hi Peter,

.RPM are Redhat linux packages and aren't directly installable on Debian/Ubuntu. However as somebody else mentioned there is an application called Alien which can convert .RPM packages into .DEB packages which you can then install.

If you haven't got it already, you need to install Alien on your system. Open the terminal and type:

sudo apt-get install alien

using the terminal, go to the directory where your .RPM file is stored and type:

alien <filename>.RPM

It should leap into action and create a .deb file out of the .RPM which you can install by typing:

sudo dpkg -i <filename>.deb

To play WMV's you'll also need to install the correct codecs. This page might help: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

