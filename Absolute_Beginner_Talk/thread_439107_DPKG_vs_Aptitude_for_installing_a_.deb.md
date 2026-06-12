---
title: "DPKG vs Aptitude for installing a .deb"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Mattness on 2007-05-10
If you've downloaded a .deb file, say to the desktop.  Can you use (aptitude install) to install that file or do you have to use (dpkg -i)?  The reason I ask is that it seems like dpkg only informs you of the dependencies but does not install them for you unlike aptitude which should install any dependency it needs.  Thanks.

Matt

---

### Post by taurus on 2007-05-10
If you install .deb by hand (whether with dpkg -i or double-click it), then you need to take care of all the dependencies by hand too.  That's why try to install stuff with synaptic/apt-get/aptitude if you can.

---

### Post by Najand on 2007-05-10
For installing packages locally with apt-get check the following link:
[http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages)

---

### Post by Mattness on 2007-05-10
Thanks for the quick response.  Najand, that link you provided looks like it would work well but that's too much work to install one single .deb file like I needed to do.  But I'll definately keep it in mind it I have a bunch to install.  I usually just try to install from aptitude or synaptic but I could not find VirtualBox in the repositories.  Thanks again.

Matt

---

### Post by danomatika on 2007-12-23
There is an easy way to do this ... after reading this post I managed to find it and install a single .deb with lots of dependencies:[ https://forum.bytemark.co.uk/viewtopic.php?pid=2216]("https://forum.bytemark.co.uk/viewtopic.php?pid=2216")

Long story short its:
```
sudo dpkg -i your_package_to_install.deb
sudo aptitude install your_package_to_install_apt_repository_name
```

... and that's it!  dpkg will haemorrhage dependency errors and then aptitude will install them and everything will be peachy.

---

