---
title: "Wma"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by physcsdrk on 2006-05-04
I have followed all of the instructions on the restricted formats wiki:

[https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=wma]("https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=wma")


Everything seemed to go okay.  I have mp3 files, wma, and restricted wma files.    I have only been able to play the mp3 files so far.
I followed all of the instructions explicity and everything seemed to go okay.
Is there something else I have to do to get the wma and restricted wma files to play?  Do I have to use a certain media player?

---

### Post by localzuk on 2006-05-04
The part of the document that is pertinent to wma's is the bit

>  wget -c [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb)
  sudo dpkg -i w32codecs_20050412-0.0_i386.deb

So, first thing to do is double check you have the w32codecs package installed (take a look in synaptic).

Next thing to find out is what program are you using to try and play them?

Finally, what version wma file is it you are trying to play?

Also, you will not be able to play any files with DRM in at all.

---

### Post by physcsdrk on 2006-05-05
Once I had restarted my computer the wma files will play now.  :)  Am not sure why I had to restart...but hey, it works!

---

