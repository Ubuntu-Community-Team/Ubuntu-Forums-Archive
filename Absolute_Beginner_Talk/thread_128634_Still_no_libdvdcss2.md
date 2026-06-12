---
title: "Still no libdvdcss2"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by petipit on 2006-02-11
:cry: :( Thanks for the help. using Terminal I have been able to install some program but still I cannot install "libdvdcss2". What Digitallysick propose did not work, when in terminal typing "sudo adept" did not do anything except going back to entering a command. No adept tree opening to search for the file.   I was able to install MPlayer using terminal using the command "Sudo apt-get" but that did not work for libdvdcss2. anymore sugestion.  I dont know what im doing wrong but using Smaptic I can not install it either

---

### Post by eriefisher on 2006-02-11
Did you try:sudo apt-get update
                sudo apt-get install libdvdcss2
If that doesn't work you might need to add or enable a repo.

eriefisher

---

### Post by jrib on 2006-02-11
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

add the plf repo, then you should be good to go

---

### Post by codejunkie on 2006-02-11
try running ```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
``` in a terminal this will install libdvdcss2.

---

### Post by aysiu on 2006-02-12
Yet another method:

Just download [the actual .deb straight from the Debian repositories](ftp://ftp.nerim.net/debian-marillat/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb) to your desktop and then ```
cd Desktop
sudo dpkg -i libdvd*.deb
```

---

