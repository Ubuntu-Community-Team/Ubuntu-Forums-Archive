---
title: "installing web browsers"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by rudolphna on 2008-02-24
I would like to install Firefox v3, and Opera9, and if possible IE7 as well.  I have the firefox and opera download .tar.gz files on my dekstop, but i have no idea where to go from there.  Synaptics manager doesnt recognize them.  help please.  :guitar:

---

### Post by wolfen69 on 2008-02-24
firefox 3 and opera are available in synaptic package manager.

---

### Post by rudolphna on 2008-02-24
really? I just downloaded the ones that said for linux.  where can i find them packages

---

### Post by kfir on 2008-02-24
just write in search firefox and opera and you will see it

---

### Post by rudolphna on 2008-02-24
yes, but only v 2.0.12 shows up.  im trying to use the Beta3 of v3.0.    my question is how to go from tar.gz file to installed program

---

### Post by LaRoza on 2008-02-24
> **rudolphna said:**
> yes, but only v 2.0.12 shows up.  im trying to use the Beta3 of v3.0.    my question is how to go from tar.gz file to installed program

Firefox 3.0 is availabe in Synaptic, System->Administration->Synaptic Package Manager 

For Opera: [http://www.opera.com/download/linux/?ver=9.50b](http://www.opera.com/download/linux/?ver=9.50b)

It is a .deb installer, just double click after downloading.

It is 9.50b, but it is good and doesn't have the issue with flash. (Actually, I don't know if that is an issue anymore)

For tarballs, you usually have to read the "README" in it for instructions, or check out the site.

---

### Post by lswest on 2008-02-24
make sure you have the ubuntu-backports repository enabled for firefox 3 (and maybe opera, not sure)

---

### Post by LaRoza on 2008-02-24
> **lswest said:**
> make sure you have the ubuntu-backports repository enabled for firefox 3 (and maybe opera, not sure)

Opera should be downloaded from that link, not from Synaptic.

---

### Post by lswest on 2008-02-24
Okay, wasn't sure,thanks for mentioning it^^  (i don't bother use opera anymore :P)

---

### Post by lovey on 2008-02-24
I;am new to ubuntu and you all have me totally confused

---

### Post by lovey on 2008-02-24
to let you all know I build all my computers,have 8 up and running,I built one just for ubuntu and just tring to figure it out thank you

---

### Post by lswest on 2008-02-25
okay, to enable the backports repositories you go to system-->administration-->software sources, then mark the box next to the line that ends with "(backports)"  then run sudo apt-get update, or open synaptic (it automatically refreshes your repository list, and if not, just click "refresh")  This is necessary because the FF is a beta release, and so isn't stable, which means it gets left in the backports repository (archive of software) so that it doesn't confuse anyone i guess :P

Apart from that, there are multiple ways to install software, one of which is downloading the tar files and then compiling them from those files using ./configure, make, sudo make install, etc.  Generally apt-getting and synaptic is easiest, because it installs deb files, and it installs it automatically, without you needing to really get involved.

Hope I cleared it up a bit

---

